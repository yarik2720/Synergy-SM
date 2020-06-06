# Map fixes of Half Life 2 and Episodes for Synergy Mod
## Installation 
### Synergy 56.16:
- Simply place folders with files in `synergy` directory, for example: `Steam\steamapps\common\Synergy\synergy\`

### Synergy 20.xx (development and twitch branch):
- Place folders with files in custom directory, for example:
`Synergy\synergy\custom\thisedit\`

	> The folder `thisedit` can be named anything, it is just a container folder.

- After placing edt files you need to restart your server if it was already running and set `content_mount_synergy_mod_path_priority 0` for the EDTs to apply.

## Changes
> All files were imported from Synergy version 56.16 and here is changes:

- Changes over all maps (or almost all):
	+ Notifications of mission failure (will be removed when next version releases)
	+ Half Life 2 Update support
	+ Added Elite Jeep spawn on some hl2 and ep2 maps (also fix for Jeep Elite included in `scripts` folder)
	+ Increased vehicle spawns for more players
	+ Damage players on vehicle spawn places who blocks spawning
	+ Vitage mode fixes
	+ Fixed stucking on synergy transition wall and changed synergy coop counter positions
	+ Antlion Guard health moved out from edt files, set up needed health in file `synergy\cfg\skill_mod.cfg`, example:
        ```
    	// Default health without setting it up is 500
    	sk_antlionguard_health "2560"
    	sk_antlionguard_dmg_charge "60"
    	sk_antlionguard_dmg_shove "25"
        ```

- Map specific changes:
+ ##### Half Life 2
	+ d1_trainstation_01
		+ fixed players teleportation into the train after Gman scene
		+ Changed Barney room teleport trigger to disable after TeleportPlayersNotTouching so it isn't a jarring teleport
		+ fixed citizens queue stops due to rushing
	+ d1_trainstation_03
		+ enabled never used track "Miscount Detected"
		+ changed player percentage on trigger_coop
	+ d1_trainstation_06
		+ preventing skipping Barney scene
	+ d1_canals_02
		+ fixed origin for antiskip triggers
		+ added new one trigger_push for skip preventing
	+ d1_canals_06
		+ closed skip through wall
	+ d1_canals_07
		+ added checkpoint before gates opening
	+ d1_canals_08
		+ extended trigger_coop size while waiting other players
	+ d1_canals_09
		+ extended trigger_coop size while waiting other players
	+ d1_canals_10
		+ extended trigger_coop size while waiting other players
	+ d1_canals_11
		+ preventing blocking ramp
		+ fixes for trigger_coop
		+ preventing blocking gates opening
		+ extended trigger_coop size while waiting other players
	+ d1_canals_12
		+ extended trigger_coop size while waiting other players
	+ d1_canals_13
		+ fixed helicopter health in vintage mode
	+ d1_eli_01
		+ fixed npc's damage filter
	+ d1_town_01
		+ closed puzzle skip
	+ d1_town_02
		+ fixed playing around with tram lever
		+ checkpoint after tram lever
		+ antiskip triggers fixed and more added
		+ disabled trigger hurt after coming back from d1_town_03
		+ fixed preventing backtracking to d1_town_03
		+ added trigger to disable zombie spawns at lift section when standing near them (grind block).
	+ d1_town_02a
		+ antiskip trigger added
		+ proper trigger coop position
		+ added more zombies
	+ d1_town_05
		+ removed some turrets to prevent changemap crashes
		+ prevented escaping out of the map
		+ reenabled antirush in warehouse, but with decreased antirush time, to prevent stucking in warehouse
	+ d2_coast_04
		+ prevented wallclimbing
		+ alerting players that they need vehicle to proceed after crane
		+ fixed missing sound (included in `scripts` folder)
	+ d2_coast_07
		+ extended trigger hurt against field overjump
	+ d2_coast_09
		+ moved syn_autosave from multiple trigger to trigger once (more players = more cars stopping)
	+ d2_coast_10
		+ antirush push triggers
		+ antirush trigger_hurt now disables after secret door opens
		+ fixed server crash by replacing already used TemplateName for Combine Soldiers
	+ d2_coast_11
		+ fixed health for Antlion Guard on vintage mode
		+ added antiskip clips
		+ added button to open gates if bugbait is broken (happens if server didn't restarted after Episodes)
	+ d2_coast_12
		+ fixed assault on vintage mode
	+ d2_prison_03 
		+ fixed vent skip
	+ d2_prison_05
		+ added checkpoint before Antlion Guard
		+ add checkpoint after combine crusherwall ends moving (helpful if level restart disabled when all players are dead)
	+ d2_prison_06
		+ reenabled commented out working solution to fix Alyx stuck
		+ added checkpoints and teleports on Eli scene and after it
		+ made more vanilla doors behavior
		+ teleport players on elevator, prevent them to be teleported on checkpoint too early
	+ d2_prison_07
		+ revert to vanilla backtracking d2_prison_07
	+ d2_prison_08
		+ close NPC spawn-kill zone
		+ fixed broken checkpoints
	+ d3_c17_01
		+ prevent working teleport overjump (or it can be stucked during opening)
	+ d3_c17_02
		+ fixed broken checkpoint
		+ start Dog automatically (trigger can be hitted before Dog can begin sequence)
	+ d3_c17_06a
		+ fixed checkpoint location
	+ d3_c17_06b
		+ prevented skipping
	+ d3_c17_07
		+ prevented rushing before Alyx enters bloody room (hitting triggers while sequence is not ended breaks her)
		+ prevent skipping on the roof
	+ d3_c17_08
		+ remove all wooden boards near manhacks to prevent clients crashes by exploding them (this also still crashes original hl2)
		+ fix mp_antirush_disable breaking elevator on vanilla mode
		+ fix catwalk grenade throw sequence
	+ d3_c17_09
		+ prevent skip without waiting for Barney
	+ d3_c17_10a
		+ fix Barney stucking on beginning
		+ remove syn_transition_wall on the beginning to allow rebels come through (trigger_push still prevents backtracking)
	+ d3_c17_10b
		+ antirush push in trap with Barney
	+ d3_c17_13
		+ remove meeting citizen storytelling, it stucks in duck position
		+ antirush push positions added
		+ added checkpoint
		+ added fix by Katie Roberts (@PsychoNightmare) - Killing strider prevents progression - https://gitlab.com/SynergyMod/Synergy/issues/6
		+ trigger hurt for players, that are trying to go at the end before killing all Striders
	+ d3_breen_01
		+ fixed blinking
		+ proper teleport destinations
		+ fix spectators GUI breaking when spectating on falling player in the teleport chamber
+ ##### Half Life 2 Episode One
	+ ep1_citadel_00
		+ fixed Alyx stucking and falling down through ground
		+ fixed vanride can be ended before Alyx exits van
		+ antirush blocks
	+ ep1_citadel_01
		+ don't stop Alyx scenarios on players fall, close door on rollermine area
		+ added teleports and checkpoints
		+ fixes for Alyx if there is afk player on server
	+ ep1_citadel_02
		+ add Alyx and players teleport before dropship scene
	+ ep1_citadel_02a
		+ deleted entry_transition_door, some players can stay before it and can't proceed
		+ teleport Alyx on elevator platform
		+ remade autosaves with delay to prevent infinite players death after fail
	+ ep1_citadel_03
		+ play sound_radiation_warning only once
		+ fix teleport positions and added new one in danger zones
		+ reduce glow size
		+ added fallback in trigger_socket_5 for when sometimes counter fails
		+ block disabling timer_ball_tube1 which prevents completing section where you have to fill 3 parts if someone leaves
		+ applied no damage filter to Alyx after mossman scene starts
	+ ep1_c17_00
		+ antirush block
		+ teleport players to prevent stucking in Alyx
		+ add checkpoint and tp Alyx to zombine joke scene
		+ open gate automatically
	+ ep1_c17_00a
		+ prevent early elevator power reenabling
		+ open gate automatically
		+ teleport players when Alyx enters elevator (clip wall appears that doesn't allow players to enter elevator)
		+ make Alyx invincible (level restart breaks elevator appearing)
		+ tp players and Alyx in waterroom, no need to wait a lot when Alyx come
	+ ep1_c17_01
		+ fix crank locking
		+ add player teleports in some places, Alyx waits for afk's
		+ make fire deal more damage (antirush)
	+ ep1_c17_02
		+ teleport Alyx in combines room (she can be blocked by players and props)
		+ fixed long waiting after guard death
	+ ep1_c17_02b
		+ prevent whole map skip
		+ added teleport
		+ prevent players being stucked in npc (fixed)
	+ ep1_c17_02a
		+ reduce door delay
		+ lazy people must take a part in puzzle solving (water therapy), so teleport them all
		+ give rpg for all players once one take it
	+ ep1_c17_05
		+ added checkpoint
		+ made citizens proceed automatically (supports vintage mode) - BUG on Synergy 56.16: citizens stops following any player when someone connects
		+ faster combine spawns
	+ ep1_c17_06
		+ made killing Strider a bit harder
		+ added checkpoint
		+ prevent escaping
+ ##### Half Life 2 Episode Two
	+ ep2_outland_01
		+ antiskip triggers
		+ suiciding after activating button to open gates can stuck game, move all players there
		+ revert back to antirush coop, waiting for vort is too long
	+ ep2_outland_02
		+ fix health of wood_boords after scene complete
		+ more fun - more antlion guards
	+ ep2_outland_03
		+ Vort enables generator quicker
		+ edited entry gates mass
	+ ep2_outland_04
		+ prevent elevator blocking with props
		+ fix vort position on elevator
		+ made fanblade always rotating
		+ added checkpoints on the map
	+ ep2_outland_06
		+ antiskip triggers
		+ Alyx sniper invulnerable
		+ reenabled players teleport after forklift
	+ on maps ep2_outland_06a - ep2_outland_10a made Alyx and jalopy teleporting at the end so they will be on next map after changelevel
	+ ep2_outland_06a
		+ antiskip triggers
	+ ep2_outland_07
		+ prevent escaping advisor room
		+ antiskip triggers
	+ ep2_outland_08
		+ removed door that can make transition to another map (looks bad, maybe I'll remade it later)
	+ ep2_outland_10
		+ teleport jalopy, players and Alyx on trap, also locks jalopy before trap is not opened
		+ failsafe Alyx moving after turret disabled to start next sequence
		+ more antirush events to prevent breaking game
	+ ep2_outland_10a
		+ moved car spawning points, remove additional
		+ added trigger_coop at the end to teleport Alyx
	+ ep2_outland_12
		+ added trigger_coop at the end to teleport Alyx
	+ ep2_outland_12a
		+ fixed players teleportations to elevators
		+ added GMan as Half Life Alyx reference
