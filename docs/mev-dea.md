# MEV and DEA

MEV and DEA are two common mods that add enemies to the game. They are used in a few commonly played difficulties and although they are not directly related to CD2, it is handy to have a list of the new enemy descriptors they add. Some of the enemies here can be replicated with CD2 without needing an external mod with the use of custom materials and [projectiles](projectiles.md). 

Neither of the two mods are in mod.io and they can be found as .pak files in the Practical DRG Discord. The mods themselves don't do anything: in order to spawn them, they have to be included in a CD2 file.

## MEV

Descriptions provided by mod author @yinny. Updated for MEV 5.4.

### Grunt variants

These grunts are recolors of the normal grunt and its veterans (Guards and Slashers) to be used for special purposes (eg. to give grunts spawning from nexus a different color from normal grunts).

| ED name | Comments |
| -------- | -------- |
| ED_Spider_Grunt_cyan | Blue grunt. | 
| ED_Spider_Grunt_red | Red grunt. |  
| ED_Spider_Grunt_white | White grunt. | 
| ED_Spider_Grunt_yellow | Yellow grunt. |
| ED_Spider_Grunt_Guard_cyan | Blue guard. |
| ED_Spider_Grunt_Guard_red | Red guard. |
| ED_Spider_Grunt_Guard_white | White guard. |
| ED_Spider_Grunt_Guard_yellow | Yellow guard. |
| ED_Spider_Grunt_Attacker_cyan | Blue slasher. |
| ED_Spider_Grunt_Attacker_red | Red slasher. |
| ED_Spider_Grunt_Attacker_white | White slasher. | 
| ED_Spider_Grunt_Attacker_yellow | Yellow slasher. |

### Breeders 

These breeders are recolors of the normal breeder. Their main use is to be able to have multiple breeders spawning different enemies in the same mission, which before CD2 was only partially possible by using the rockpox breeder as a second variant. As an alternative way, CD2 now allows to have multiple breeder descriptors with different settings (see the `Grabber` module in [Enemies](enemies.md).)

| ED name | Comments |
| --------- | ------- |
| ED_JellyBreeder_green | Green breeder, spawns ED_Jelly_Spawn_dummy_green. |
| ED_JellyBreeder_red | Red breeder, spawns ED_Jelly_Spawn_dummy_red. |
| ED_JellyBreeder_purple | Purple breeder, spawns ED_Jelly_Spawn_dummy_purple. |
| ED_JellyBreeder_yellow | Yellow breeder, spawns ED_Jelly_Spawn_dummy_yellow. |

To use these, override the specified dummy jelly descriptor with the ED you want to spawn:

```json
"ED_JellyBreeder_purple": {
    "Base": "ED_Spider_Exploder"
}
```

will make the purple breeder spawn exploders.

### Bulks


| ED name | Comments |
| --------- | ------- |
| ED_Spider_ExploderTank_black | A bulk recolor in black. |
| ED_Spider_ExploderTank_white | A bulk recolor in white. |
| ED_Spider_ExploderTank_small | A small bulk, commonly called mini-bulk, with a smaller radius explosion. |
| ED_Spider_ExploderTank_big | A bigger bulk which also has a huge explosion with magma lining. |
| ED_Spider_ExploderTank_frozen | An ice bulk, does no damage but freezes everything around it. |
| ED_Spider_Plantonator | A special bulk. When exploding, each bomblet will spawn ED_sprout_spawn in turn, which is a korlok sprout by default but can be changed by specifying a different base. |

### Exploders

| ED name | Comments |
| --------- | ------- |
| ED_Spider_Exploder_frost | An ice exploder, leaves snow when it explodes. |
| ED_Spider_Exploder_fungus | A fungus bogs themed exploder, leaves goo behind when it dies. |
| ED_Spider_Exploder_white | A recolor in white. |

### Mactera

| ED name | Comments |
| --------- | ------- |
| ED_Mactera_Shooter_HeavyVeteran_cyan | Elemental electric brundle. |
| ED_Mactera_Shooter_HeavyVeteran_green | Elemental poison brundle. |
| ED_Mactera_Shooter_HeavyVeteran_red | Elemental fire brundle. |
| ED_Mactera_Shooter_HeavyVeteran_white | Elemental ice brundle. |
| ED_Mactera_Shooter_cyan | Elemental electric mactera spawn. |
| ED_Mactera_Shooter_green | Elemental green mactera spawn. |
| ED_Mactera_Shooter_red | Elemental fire mactera spawn. |
| ED_Mactera_Shooter_white | Elemental ice mactera spawn. |
| ED_Mactera_TripleShooter_cyan | Elemental electric trijaw. |
| ED_Mactera_TripleShooter_green | Elemental poison trijaw. |
| ED_Mactera_TripleShooter_red | Elemental fire trijaw. |
| ED_Mactera_TripleShooter_white | Elemental ice trijaw. |
| ED_Bomber_buffer | A goo bomber warden, gives the protection effect to nearby enemies. |

### Menaces

| ED name | Comments |
| --------- | ------- |
| ED_Spider_RapidShooter_cyan | Elemental electric menace. |
| ED_Spider_RapidShooter_green | Elemental poison menace. |
| ED_Spider_RapidShooter_red | Elemental fire menace. |
| ED_Spider_RapidShooter_white | Elemental ice menace. |
| ED_Spider_RapidShooter_Turbo | A rapid-fire shooting menace. |

### Nexus

These are recolors of the normal nexus, following the same logic for breeders: they allow to have more than one type of nexus in the same mission. CD2 currently doesn't have a `Nexus` module to specify the EDs of different nexii (although the effect can be simulated by using `Spawner`, see in [enemies](enemies.md)), so this method is still the simplest. 

| ED name | Comments |
| ----- | --------- |
| ED_SpiderSpawner_green | Green nexus spawning ED_Spider_Spawn_dummy_green. |
| ED_SpiderSpawner_red | Red nexus spawning ED_Spider_Spawn_dummy_red. |
| ED_SpiderSpawner_yellow | Yellow nexus spawning ED_Spider_Spawn_dummy_yellow. |
| ED_SpiderSpawner_white | White nexus spawning ED_Spider_Spawn_dummy_white. |

### Nukeballers

Spitballers shooting nukes. Since they provide a different number of shot projectiles, they are an interesting match for custom [projectiles](projectiles.md).

| ED name | Comments |
| ----- | --------- |
| ED_ShootingPlant_NukeSingle | Shoots a single projectile. |
| ED_ShootingPlant_Nuke | Shoots three projectiles in a row. |
| ED_ShootingPlant_NukeEX | Shoots five projectiles in a row. |
| ED_ShootingPlant_NukeU | Shoots ten projectiles in a row. |

### Oppressors

Recolors (not elemental) of the oppressor.

| ED name | Comments |
| ----- | --------- |
| ED_Spider_ShieldTank_cyan | Blue oppressor. |
| ED_Spider_ShieldTank_red |  Red oppressor. |
| ED_Spider_ShieldTank_yellow |  Yellow oppressor. |
| ED_Spider_ShieldTank_white |  White oppressor. |

### Praetorians 

| ED name | Comments |
| ----- | --------- |
| ED_Spider_Tank_buffer | Praetorian warden, gives the protection buff and a healing buff to nearby enemies. |
| ED_Spider_Tank_cyan | Elemental electric praetorian variant. |
| ED_Spider_Tank_red | Elemental fire praetorian variant. |

### Shellbacks 

| ED name | Comments |
| ----- | --------- |
| ED_Woodlouse_cyan | Elemental electric shellback. |
| ED_Woodlouse_red | Elemental fire shellback. |
| ED_Woodlouse_purple | Purple shellback recolor. |
| ED_Woodlouse_white | Elemental ice shellback. |

### Sprouts
Can be used as new stationary enemies. 

| ED name | Comments |
| ----- | --------- |
| ED_Sprout_Normal | Vanilla korlok sprout. |
| ED_Sprout_purple | A korlok sprout that shoots the web spitter projectile. |
| ED_Sprout_upside | Vanilla korlok sprout that spawns on ceilings. |

### Swarmers

| ED name | Comments |
| ----- | --------- |
| ED_Spider_Tank_HeavySpawn_swarmer | Swarmer-scale sentinel. |
| ED_Spider_Stalker_swarmer | Swarmer-scale stalker. |

### Younglings

| ED name | Comments |
| ----- | --------- |
| ED_Woodlouse_Youngling_cyan | Blue youngling recolor. |
| ED_Woodlouse_Youngling_red | Red youngling recolor. |

### Miscellaneous enemies

| ED name | Comments |
| ----- | --------- |
| ED_Lootbug_bulk | Mimic lootbug. Can't be pet and when killed it explodes like a bulk detonator. |
| ED_CaveLeech_cloak | A leech with the stalker material. |
| ED_CaveLeech_silent | A silent leech. |
| ED_PatrolBot_missile | A special patrol bot with a different attack pattern. |
| ED_PatrolBot_rocketbeam | A special patrol bot with a different attack pattern. |

## DEA 

Descriptions provided by the mod author @donnie_danko. Updated for version 5.5.

### Grunts and spitter variants

| ED name | Comments |
| ------- | -------- |
| ED_Spider_Glasher  | A hybrid of the Guard and Slasher, best of both worlds. Includes ice and radiation biome variants. |
| ED_Spider_Gritter_Ceiling | Ceiling pathfinding preference. |
| ED_Spider_Gritter_Wall | Lower health than grooter, with web spitter attack instead of acid. |
| ED_Spider_Grooter  | A grunt/acid lobber hybrid which will lob ground acid spitter PRJs in a tri jaw like pattern. Mostly a proof of concept hybrid ranged/melee enemy. | 
| ED_Spider_Grooter_Ceiling | Grooter with ceiling pathfinding preference, and normal acid spitter attack. |
| ED_Spider_Grooter_Wall | Hybrid melee/range grunt with wall pathfinding preference, same triple acid lob attacka as grooter. |
| ED_Spider_Grunt_Guardian | Glasher with a burrow attack tacked on, does 20% more damage than its slash. |
| ED_Spider_Shooter_Bouncer  | A ground acid spitter which lobs RJ250 at you. Should do half the damage of a typical spitter prj, within 2m max damage radius. | 
| ED_Spider_Shooter_Fire  | An acid spitter variant which fires OG dread fireball, slightly less aggressive behavior. | 
| ED_Spider_Shooter_Ice  | An acid spitter variant which applies cold damage on hit, rather than the acid STE. | 
| ED_Spider_Shooter_Spawner  | A ground acid spitter which lobs dreadnaught swarmer eggs which spawn 2*enemy count modifier of ED_Spider_Swarmer_SpawnShot. | 
| ED_Spider_Slobber  | A septic spreader variant which lobs deadnaught swarmer eggs which spawn 2*enemy count modifier of ED_Spider_Swarmer_SpawnShot. | 
| ED_Spider_Spitter_Cyan  | A web spitter variant which applies the stalker shield disruption effect. |
| ED_Spider_Spitter_Pink  | A web spitter variant which applies a marked-for-death status effect. |
| ED_Spider_Spitter_Stagger  | A web spitter variant which applies the slasher stun effect. |
| ED_Spider_Spitter_White  | A web spitter variant which does not apply any status effect. | 

### Mactera variants

| ED name | Comments |
| - | - |
| ED_Acid_Bomber | Bomber variant which drops goo with properties of both sentinel goo and septic spreader goo. Its projectile attack will also leave goo behind when dodged, does a 50/50 split of poison/explosive damage rather than explosive, and applies the acid spitter STE if it hits you. |
| ED_Arbabomber | Firebomber with projectile attack replaced with arbalest mines, no visual difference from firebomber. |
| ED_Bomber_Exploder | Firebomber whose projectile attack spawns exploders, no visual difference from firebomber. spawned exploders use ED_Spider_Exploder_SpawnShot . |
| ED_Bomber_NoShot | Goo bomber with no projectile attack. |
| ED_Enola_Gay | Goo bomber that shoots nukes. |
| ED_Mactera_IPJaw | Instant penta jaw. |
| ED_Mactera_InstaJaw | Tri jaw that shoots all its projectiles at once. Currently not visually distinct from tri-jaw so I would recommend using CD2 to change materials. |
| ED_Mactera_Pentajaw | Mactera trijaw that shoots 5 projectiles instead of 3. |
| ED_Mactera_RadialJaw | Mactera that shoots in a circular pattern. | 
| ED_Mactera_Shooter_Breach and ED_Mactera_Brendle | They shoot a faster version of OMEN linecutter. | 
| ED_Mactera_Trundle  | A hybrid of the tri-jaw and brundle. I suggest using CD2 to change its materials if you use it. |  
| ED_Parabomber | Drops spawn eggs and fires an egg which applies phero STE. Greatly reduced drop rate compared to typical goober and each spawn egg spawns 1*enemy count modifier of ED_Spider_Swarmer_SpawnShot. |

### Menace variants

| ED name | Comments |
| ------- | -------- |
| ED_Spider_Fanatic  | A menace variant which uses the arbalest fireball fan attack, rather than normal menace attack. Long delay between attacks, and fires 5 times before reburrowing.  | 
| ED_Spider_ShotgunMenace  | Similar to the Fanatic, but fires 9 fireballs in a grid pattern, rather than 5 in a fan. | 
| ED_Spider_FanaticEX | Original pre nerf version of Fanatic, with normal menace AI |
| ED_Spider_ShotgunMenaceEX | Same for the ShotgunMenace. |

### Spawner enemies

| ED name | Comments |
| - | - |
| ED_Spider_SlobberEX | Spawns 6*enemy count modifier. |
| ED_Spider_Shooter_SpawnerEX | Spawns 6*enemy count modifier. |
| ED_ShootingPlant_Spawner | Fires spawn egg which spawns 6*enemy count modifier of ED_Spider_Swarmer_SpawnShot. |
| ED_ShootingPlant_SpawnerEX | Also applies phero STE. |
| ED_ShootingPlant_Spawner_Boomer | Fires spawn egg which spawns 6*enemy count modifier of ED_Spider_Exploder_SpawnShot. |

### Dreadnought variants

Do not recommend allowing these to exist at the same time as vanilla twins. will lead to weird behavior of vanilla twin. These will not heal with vanilla twins or each other, but vanilla twins will try to heal with them and will grieve them.

| ED name | Comments |
| - | - |
| ED_Altnought and _Tank variant | Fauxnought with slightly altered appearance and different moveset. Uses the oppressor slam instead of dread, a 3 fireball attack, and a burrow attack instead of dread fireball and swarmer egg attacks. |
| ED_Banshee | Arbalest variant that only uses grieve attack. |
| ED_Fauxbalester | Arbalester that will use both attacks. |
| ED_Fauxbalester_Locked | Arbalester that will only use mines. Technically behaves as a post heal Arbalest, but just uses mines in place of fan attack. |
| ED_Fauxnought | Non health gated dreadnought, slightly smaller than normal dread. Has slightly above Oppressor health and Large enemy health scaling. Eggshot spawns ED_Spider_Swarmer_SpawnShot. |
| ED_Fauxnought_Tank | fauxnought with stun immunity, may make some additional changes to bring more in line with dread
| ED_Lassie_Aggro | A work around for my inability to make an unlocked lacerator without messing up the stomp attack. Trades out the fire attack for burrow. |
| ED_Lassie_Locked | A Lacerator that will not use burrow attack. Seems to really like its flamethrower attack, probably needs some tweaking.  |
| ED_Lassie_Unlocked | A Lacerator that will use burrow attack.  |
| ED_Lassie_Zen | A work around for my inability to make a nonhealing/grieving lacerator without messing up the stomp attack. Will not burrow after grieve sequence is triggered by killing fauxbalester/arbalester. |

### Miscellaneous enemies

| ED name | Comments |
| - | - |
| ED_Drone_Breeder | A breeder which drops homing drones (from OMEN) instead of eggs. |
| ED_Sniper_Turret_Slow | Sniper turret with 2/3rds health and 50% projectile speed, from 10x spitter projectile speed down to 5x. |
| ED_StabberVine | Stabber vines to be used as stationary enemies, might have weird behaviours. |
| ED_SuckingPlant | An unused sucking plant. Seems to be pretty buggy with the potential to give you a permanent low grav state, might try to fix it at some point. |
