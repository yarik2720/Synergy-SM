# Synergy-SM Project Description

## Overview
Synergy Mod Map Fixes — a project for adapting Half-Life 2 and Episodes maps for the cooperative mod Synergy.

## Project Structure

```
Synergy-SM/
├── README.md          # Documentation (installation, changes)
├── .gitignore         # Excludes fgd/ and maps_sources/ from repository
├── fgd/               # FGD files for map editor (references)
│   ├── base.fgd       # Source Engine base classes
│   ├── halflife2.fgd  # Standard HL2 entities
│   ├── hl2mp.fgd      # Multiplayer entities
│   └── synergy.fgd    # Synergy-specific entities
├── maps/              # EDT map fix files (published)
├── maps_sources/      # Original VMF map files for analysis (NOT in git)
├── scripts/           # Game scripts
└── sound/             # Sound files
```

## Workflow

1. **Original map analysis**: VMF files in `maps_sources/` are studied in Hammer Editor
2. **Comparison with EDT**: Matching changes with corresponding EDT files in `maps/`. When working with parameters and entities in EDT, refer to FGD files in the `fgd/` folder to understand available options and arguments.
3. **Editing**: Changes are made to EDT via Synergy plugin or manually
4. **Publication**: Only EDT files from `maps/` are included in the repository

> **Important**: Folders `fgd/` and `maps_sources/` are excluded from git via `.gitignore`
> **Mapping rule**: Any file `maps/<map_name>.edt` corresponds to source `maps_sources/<map_name>_d.vmf`. The `_d` suffix is added to all decompiled sources.

## Agent Workflow

1. Prefer editing published EDT files in `maps/`. Treat `fgd/` and `maps_sources/` as references unless explicitly asked otherwise.
2. Before adding a new entity pattern, search existing `maps/*.edt` files for similar fixes and reuse the established approach when it fits.
3. For map-specific changes, inspect the matching `maps_sources/<map_name>_d.vmf` when it is available.
4. When adding or changing entity keys, check the relevant FGD file to confirm class names, key names, inputs, outputs, and spawnflags.
5. Keep EDT edits scoped. Do not reformat unrelated parts of a file.
6. Bring only newly added or touched EDT blocks toward the project style used nearby in that file.
7. Write EDT comments in English.
8. Use semantic `targetname` values for created entities, preferably with the `syn_` prefix when the entity is part of the cooperative fix logic.

## EDT File Format

EDT (Entity Definition Template) — a text format for modifying map entities without recompilation.

### Basic syntax
```
<map_name>
{
    entity
    {
        // Entity operations
        create {classname "class_name" origin "x y z"
            values {key "value" ...}}
        
        edit {targetname "entity_name" 
            values {key "new_value" ...}}
        
        delete {classname "class_name" or targetname "entity_name"}
    }
    
    console
    {
        // Console commands
        command value
    }
}
```

### Operation types
- **create** — create a new entity
- **edit** — modify parameters of an existing entity
- **delete** — delete an entity

### Style rules
- Preserve the local style of the EDT file being edited.
- Normalize only new or modified blocks as part of the change.
- Use English comments in EDT files.
- Avoid creating backup files in the repository; rely on git history unless a manual backup is explicitly requested.

### Operation examples
```edt
// Creating a coop spawn point
create {classname "info_player_coop" origin "1000 2000 300"
    values {angles "0 90 0" targetname "spawn_1"}}

// Modifying starting equipment weapons
edit {classname "info_player_equip" 
    values {weapon_smg1 "1" weapon_shotgun "1"}}

// Removing extra NPCs
delete {targetname "npc_citizen_extra"}
```

## Key FGD Classes

### base.fgd
- `Angles`, `Origin`, `Studiomodel` — positioning and model
- `Targetname`, `Parentname` — naming and hierarchy
- `RenderFields`, `RenderFxChoices` — rendering
- `EnableDisable`, `Global`, `DamageFilter` — triggers and filters

### synergy.fgd
- `TalkNPC`, `PlayerCompanion`, `RappelNPC` — NPCs with advanced behavior
- `npc_turret_ground`, `npc_turret_ceiling`, `npc_turret_floor` — Combine turrets
- `func_combine_ball_spawner`, `point_combine_ball_launcher` — energy ball generators
- `trigger_physics_trap`, `trigger_weapon_dissolve`, `trigger_weapon_strip` — weapon triggers

### hl2mp.fgd
- `info_player_deathmatch`, `info_player_combine`, `info_player_rebel` — spawn points
- `filter_activator_team` — team filter
- `prop_physics_respawnable` — physics object with respawn

## Map Changes Categories

- **Transport**: Elite Jeep, increased vehicle count
- **Gameplay**: checkpoints, anti-skip protection
- **Fixes**: player teleportation, NPC queues, progression blocking
- **Vintage Mode**: special compatibility mode fixes

## Typical Map Adaptation Tasks

### 1. Adding cooperative spawn points
- Replacing `info_player_start` with `info_player_coop`
- Creating multiple points for different players
- Setting up respawn system via `info_spawn_manager`

### 2. Adapting single-player scripts for multiplayer
- Replacing `scripted_sequence` with cooperative alternatives
- Adding activation triggers for all players
- Progress synchronization via `logic_relay` and `math_counter`

### 3. Fixing NPC issues
- Configuring NPC behavior for multiple players
- Fixing NPC "stuck" in dialogues
- Adding protection for important NPCs

### 4. Difficulty balancing
- Adjusting enemy count based on player count
- Modifying boss health
- Adding extra equipment

### 5. Fixing original map bugs
- Removing places where players can get stuck
- Fixing incorrect textures and models
- Performance optimization for multiplayer

## Work Tools

### Main tools
1. **Hammer Editor** — Source Engine map editor
   - Load FGD files from `fgd/` folder
   - Use for analyzing VMF sources

2. **Synergy Plugin for Hammer** — plugin for automatic EDT change generation
   - Generates basic EDT files
   - Simplifies adding cooperative elements

3. **Text editors** (VS Code, Notepad++) — for manual EDT file editing
   - Syntax highlighting recommended
   - Search and replace across multiple files

4. **BSPSource** — utility for decompiling BSP to VMF
   - Obtain map sources for analysis
   - Note: decompiled maps may contain artifacts

### Auxiliary utilities
- **VTFEdit** — texture viewing and conversion
- **Crowbar** — working with Source models
- **GCFScape** — extracting files from GCF archives

## Debugging Process

### 1. Test environment setup
```
1. Install Synergy mod
2. Configure console commands for quick map loading
3. Create local server for testing
```

### 2. Quick testing of changes
```bash
# Console commands for testing
sv_cheats 1
noclip                    # Free flight around the map
notarget                  # NPCs don't attack
ent_fire !picker <input>  # Activate entity under cursor
```

### 3. Problem diagnostics
- **Game logs**: `synergy/logs/`
- **Console messages**: Use `developer 1`
- **Entity debugging**: `ent_text` for info about entity under cursor
- **Generated entity cache**: after launching the map, inspect the generated `.ent` file in `Synergy/synergy/maps/ent_cache` to confirm the final entity output.

### 4. EDT validation
- Without launching the game, only EDT syntax can be validated.
- Syntax validation should check balanced braces, quoted key/value pairs, and operation structure (`create`, `edit`, `delete`, `values`).
- Runtime behavior still requires loading the map in Synergy.

## Useful Commands

- `content_mount_synergy_mod_path_priority 0` — EDT file priority
- Antlion Guard settings in `synergy/cfg/skill_mod.cfg`:
  - `sk_antlionguard_health`
  - `sk_antlionguard_dmg_charge`
  - `sk_antlionguard_dmg_shove`

## Maps Sources

The `maps_sources/` folder contains original VMF map files for analysis:
- **Format**: Valve Map Format (`.vmf`) — editable map sources
- **Logs**: Accompanying `.log` files for compilation diagnostics
- **Mapping structure**: For each file in `maps/` there is a corresponding file in `maps_sources/` following the scheme: `<filename>.edt` -> `<filename>_d.vmf`.

### Maps by episodes:
- **Half-Life 2**: d1_* (trainstation, canals, eli, town), d2_* (coast, prison), d3_* (c17, citadel, breen)
- **Episode 1**: ep1_c17, ep1_citadel
- **Episode 2**: ep2_outland

## Recommendations for New Contributors

### Getting started
1. Choose a simple map to study (e.g., `d1_trainstation_01`)
2. Compare original VMF and existing EDT file
3. Run the map in Synergy to understand current changes

### Best practices
1. **Use git/history** before editing EDT files; create manual backups only when explicitly requested
2. **Test with different player counts** (1, 2, 4+)
3. **Refer to FGD** when adding new entities
4. **Use semantic names** for created entities (prefix `syn_`)
5. **Check generated `.ent` output** in `Synergy/synergy/maps/ent_cache` after launching the map

### Common mistakes
- Changing coordinates without considering Hammer coordinate system
- Incorrect use of spawnflags (check FGD)
- Creating conflicting targetnames
- Not accounting for multiplayer specifics (race conditions)

## Links and Resources
- [Official Synergy website](http://www.synergymod.net/)
- [Source SDK Documentation](https://developer.valvesoftware.com/wiki/Source_SDK_Documentation)
- [Source modding community](https://www.moddb.com/engines/source)
