# Map fixes of Half Life 2 and Episodes for Synergy Mod
## Installation 
### Synergy actual version:
- Place folders with files in custom directory, for example:
`Synergy\synergy\custom\Synergy-SM\`

	> The folder `Synergy-SM` can be named anything, it is just a container folder.

- After placing edt files you need to restart your server if it was already running and set `content_mount_synergy_mod_path_priority 0` on your server config for the EDTs to apply.

### Synergy old version 56.16:
- Download version https://github.com/yarik2720/Synergy-SM/releases/tag/1.56.16
- Simply place folders with files in `synergy` directory, for example: `Steam\steamapps\common\Synergy\synergy\`

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
		+ added checkpoints for game with disabled reloads
	+ d1_trainstation_03
		+ enabled never used track "Miscount Detected"
		+ changed player percentage on trigger_coop
		+ fixed players teleport point on raid start
		+ added checkpoint as failsafe if someone suicides after door close
	+ d1_trainstation_06
		+ preventing skipping Barney scene
	+ d1_canals_01
		+ added another way to remove stuff that blocks train
	+ d1_canals_01a
		+ removed ragdolls to save network usage
	+ d1_canals_02
		+ fixed origin for antiskip triggers
		+ added new one trigger_push for skip preventing
	+ d1_canals_03
		+ fixed fall damage timer
	+ d1_canals_06
		+ closed skip through wall
	+ d1_canals_07
		+ added checkpoint before gates opening
		+ added checkpoint before second APC
	+ d1_canals_08
		+ extended trigger_coop size while waiting other players
	+ d1_canals_09
		+ extended trigger_coop size while waiting other players
	+ d1_canals_10
		+ extended trigger_coop size while waiting other players
	+ d1_canals_11
		+ deleted acid hurt trigger at map start
		+ preventing blocking ramp
		+ fixes for trigger_coop
		+ preventing blocking gates opening
		+ extended trigger_coop size while waiting other players
	+ d1_canals_12
		+ extended trigger_coop size while waiting other players
	+ d1_canals_13
		+ fixed helicopter health in vintage mode
		+ Prevent other NPCs from being able to be removed by crow removal trigger
	+ d1_eli_01
		+ fixed npc's damage filter
	+ d1_eli_02
		+ removed prop_ragdoll to prevent high network usage
		+ added block to hole by displacement
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
		+ made Monk avoid players on his way at the end
	+ d1_town_04
		+ fixed missing sound (included in `scripts` folder)
	+ d1_town_05
		+ made combines spawn while visible, fixed odd spawnflags for them
		+ made spawn additional waves of combines only when it needs to be (preventing game stuck)
		+ fixed music overlapping when players proceeds too fast
		+ prevented escaping out of the map
		+ reenabled antirush in warehouse, but with decreased antirush time
	+ d2_coast_04
		+ prevented wallclimbing
		+ alerting players that they need vehicle to proceed after crane
		+ replaced ragdolls cars with physics models
	+ d2_coast_07
		+ extended trigger hurt against field overjump
  		+ re-enabled manhack spawner in first room
	+ d2_coast_08
		+ fixed skip of trigger coop
	+ d2_coast_09
		+ moved syn_autosave from multiple trigger to trigger once (more players = more cars stopping)
	+ d2_coast_10
		+ antirush trigger_hurt now disables after secret door opens
		+ fixed soft-lock by preventing trigger on the other side of the lighthouse door to be enabled until after the secret door opens
		+ fixed server crash by replacing already used TemplateName for Combine Soldiers
	+ d2_coast_11
		+ fixed health for Antlion Guard on vintage mode
  		+ removed harpoon due soft-lock by killing npc_antlionguard
		+ added antiskip clips
		+ added failsafe to game reload if someone kills vort
		+ added button to open gates if bugbait is broken (happens if server didn't restarted after Episodes)
	+ d2_coast_12
		+ fixed assault on vintage mode
	+ d2_prison_02
		+ made sound overwatch_freeman_spotted play once
	+ d2_prison_03
		+ fixed vent skip
	+ d2_prison_05
		+ added checkpoint before Antlion Guard
		+ add checkpoint after combine crusherwall ends moving (helpful if level restart disabled when all players are dead)
  		+ fixed spawning outside the crusherwall if mp_reset is disabled
    		+ add static crate for ledge for a lot of players
	+ d2_prison_06
		+ reenabled commented out working solution to fix Alyx stuck
 		+ fix spawning outside the elevator
		+ added checkpoints and teleports on Eli scene and after it
		+ made more vanilla doors behavior
		+ prevent gate block
		+ teleport players on elevator, prevent them to be teleported on checkpoint too early
	+ d2_prison_07
		+ revert to vanilla backtracking d2_prison_07
		+ fixed spawned combine being stucked without any target
		+ added trigger_push to prevent players escape and spawnkill
	+ d2_prison_08
		+ fixed Alyx spawn on new game
		+ close NPC spawn-kill zone
		+ fixed broken checkpoints
		+ play sound HL2_song25_teleporter - Miscount Detected while elevating
	+ d3_c17_01
		+ prevent working teleport overjump (or it can be stucked during opening)
	+ d3_c17_02
		+ fixed broken checkpoint
		+ start Dog automatically (trigger can be hitted before Dog can begin sequence)
	+ d3_c17_06a
		+ fixed checkpoint location
	+ d3_c17_06b
		+ prevented skipping
		+ remade trigger_look to trigger_coop for proper coop gameplay
		+ block bridge closing to prevent players fall through it
	+ d3_c17_07
		+ prevented rushing before Alyx enters bloody room (hitting triggers while sequence is not ended breaks her)
		+ prevented skipping on the roof
		+ prevented spawnkills
	+ d3_c17_08
		+ remove all wooden boards near manhacks to prevent clients crashes by exploding them (this also still crashes original hl2)
		+ fix mp_antirush_disable breaking elevator on vanilla mode
		+ fix catwalk grenade throw sequence
	+ d3_c17_09
		+ prevent skip without waiting for Barney
	+ d3_c17_10a
		+ fix Barney stucking on beginning
		+ remove syn_transition_wall on the beginning to allow rebels come through (trigger_push still prevents backtracking)
	+ d3_c17_10a
		+ removed antirush blocking plug, was useless due to next trigger_coop placed
		+ replaced ragdoll car with physics one
	+ d3_c17_10b
		+ antirush push in trap with Barney
	+ d3_c17_11
		+ fixed combine skip door
		+ fixed skybridge skip block origin
	+ d3_c17_13
		+ remove meeting citizen storytelling, it stucks in duck position
		+ antirush push positions added
		+ added checkpoint
		+ added fix by Katie Roberts (@PsychoNightmare) - Killing strider prevents progression - https://gitlab.com/SynergyMod/Synergy/issues/6
		+ trigger hurt for players, that are trying to go at the end before killing all Striders
		+ replaced ragdoll cars with physics one
	+ d3_citadel_01
		+ prevented players enter upperpod
	+ d3_citadel_02
		+ fixed not entering pod on map start
		+ fixed ejecting out of the pod at the end
	+ d3_citadel_04
		+ added trigger hurt for skipping map
	+ d3_breen_01
		+ fixed blinking
		+ fixed exploit of blocking "digger" on the teleport part
		+ proper teleport destinations
		+ fix spectators GUI breaking when spectating on falling player in the teleport chamber
 		+ For people that may want to see the credits all the way through, there is a comment in each of these: "// Comment out these to see the credits all the way through"
+ ##### Half Life 2 Episode One
	+ ep1_citadel_00
		+ render bug fixes
		+ fixed Alyx stucking and falling down through ground
		+ fixed vanride can be ended before Alyx exits van
		+ antirush blocks
		+ don't kill falling Van (bug Synergy 56.16: players can be teleported into van if player joins server) looks weird, but better, than player inside vehicle being killed
	+ ep1_citadel_01
		+ don't stop Alyx scenarios on players fall
		+ close door on rollermine area
		+ fixes for Alyx if there is afk player on server
		+ teleport players into stalkers room and start rollertraining if alyx was blocked by players
		+ enabled more rollermine charges if another charged mine was thrown out
		+ recreated particle system to fix vortex rendering
  		+ fixed trigger position to prevent rollermine creating out of edicts limit
	+ ep1_citadel_02
		+ add Alyx and players teleport before dropship scene
  		+ fixed energy balls spawning out of edict limits
	+ ep1_citadel_02a
		+ deleted entry_transition_door, some players can stay before it and can't proceed
		+ teleport Alyx on elevator platform
		+ remade autosaves with delay to prevent infinite players death after fail
	+ ep1_citadel_02b
		+fixed checkpoints
	+ ep1_citadel_03
		+ play sound_radiation_warning only once
		+ fix teleport positions and added new one in danger zones
		+ reduce glow size
		+ added fallback in trigger_socket_5 for when sometimes counter fails
		+ block disabling timer_ball_tube1 which prevents completing section where you have to fill 3 parts if someone leaves
		+ applied no damage filter to Alyx after mossman scene starts
		+ fixed sprite wasn't removed
	+ ep1_citadel_04
		+ added teleport Alyx to airlock on many players
		+ added failsafe for Alyx not running out of train
	+ ep1_c17_00
		+ antirush block
		+ disable stalker sequence from previous map (origin Valve EP1 bug)
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
		+ fixed crank locking
		+ added player teleports in some places, Alyx waits for afk's
		+ made fire deal more damage and block skipping fire puzzle (antirush)
		+ don't allow ceiling breaking by shooting on it
		+ add failsafe to stop antlions spawn and start final scene "thats over"
		+ fixed car lost on combines gate
	+ ep1_c17_02
		+ teleport Alyx in guards room as failsafe while she can be blocked by another players
		+ recreate antlion_guard, stop spawning antlions and proceed next scene
		+ fixed long waiting after guard death
	+ ep1_c17_02b
		+ prevent whole map skip
		+ added teleport
		+ prevent players being stucked in npc (fixed)
	+ ep1_c17_02a
		+ disable backtracking trigger, some players could touch it on spawn
  		+ teleport players to the gunship battle
		+ gave rpg for all players once one take it
		+ disabled movement of gunship ragdoll after falldown
		+ reduce door delay
		+ remade part "Alyx found a shotgun" to prevent game stuck whene there is no shotguns in area
		+ lazy people must take a part in puzzle solving (water therapy), so teleport them all
	+ ep1_c17_05
		+ added checkpoint
		+ made citizens proceed automatically - BUG on Synergy 56.16: citizens stops following any player when someone connects
		+ faster combine spawns
	+ ep1_c17_06
		+ made killing Strider a bit harder
		+ added checkpoint
		+ prevent escaping
		+ fixed strider wan't respawning on early death
 		+ For people that may want to see the credits all the way through, there is a comment in each of these: "// Comment out these to see the credits all the way through"
+ ##### Half Life 2 Episode Two
	+ ep2_outland_01
		+ prevent early use of choreo vehicle and soft-locking players (original ep2 bug) and lock after players eject
		+ getting alyx faster into communication center by trigger_coop
		+ prevented fast wire plugin
		+ antiskip triggers
		+ suiciding after activating button to open gates can stuck game, move all players there
		+ revert back to antirush coop, waiting for vort is too long
	+ ep2_outland_02
		+ fix health of wood_boords after scene complete
		+ more antlion guards controlled with logic_difficulty by players amount
		+ removed hoppers to prevent server crashes (on high players amount)
	+ ep2_outland_03
		+ Vort enables generator quicker
		+ edited entry gates mass
  		+ fixed platform rising with high amount of players
	+ ep2_outland_04
		+ prevent elevator blocking with props
		+ fix vort position on elevator
		+ made fanblade always rotating
		+ added checkpoints on the map
	+ ep2_outland_04
		+ spawn guards when player hits battle area
	+ ep2_outland_06
		+ antiskip triggers
		+ prop_ragdoll disable movement to save network usage
		+ fixed warehouse teleport
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
		+ made final rebel invencible
		+ break props from exploding tower to prevent killing with them friendly npc's
	+ ep2_outland_10
		+ teleport jalopy, players and Alyx on trap, also locks jalopy before trap is not opened
		+ added shield disabling failsafe
		+ more antirush events to prevent breaking game
	+ ep2_outland_10a
		+ moved car spawning points, remove additional
		+ added trigger_coop at the end to teleport Alyx
	+ ep2_outland_11b
		+ added failsafe timer if something went wrong (no new magnussons, strider stuck while moving or smth)
	+ ep2_outland_12
		+ added trigger_coop at the end to teleport Alyx
	+ ep2_outland_12a
		+ fixed players teleportations to elevators
		+ added GMan as Half-Life: Alyx reference
 		+ For people that may want to see the credits all the way through, there is a comment in each of these: "// Comment out these to see the credits all the way through"
