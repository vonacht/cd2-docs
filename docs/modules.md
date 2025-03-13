#Modules
Modules are the top level hierarchy names for a valid CD2 JSON. The following is an alphabetized list of the current modules.

## Caps
Control for the maximum number of enemies in the map, with the following fields:

| Field | Type |
| ----- | ----- |
| MaxActiveCritters | Int |
| MaxActiveEnemies | Int |
| MaxActiveSwarmers | Int |

Example:

```json
"Caps": {
    "MaxActiveCritters": 40,
    "MaxActiveSwarmers": [90, 120, 180, 180],
    "MaxActiveEnemies": [90, 120, 180, 180]
}
```

When the number of enemies in the map reach their cap, new enemies will be prevented from spawning and some existing enemies will despawn. The exact mechanics behind this behaviour are not completely understood. 

## Darkness
The Darkness module offers controls related to lighting and illumination both in the Space Rig and during a mission. It has the following fields (descriptions provided by @noskill):

| Field                 | Type  | Default | Comment |
| --------------------- | ----- | ------- | -------- |
| FlashlightStrength    | Float | 1? | Headlight light strength, affects both range and strength of the light. |
| PlayerIllumination    | Float | 1? | Light strength in a radius around the player. Only affects strength and not radius. |
| FlareMax              | Int   | 4  | Maximum number of flares that the player can keep.  |
| FlareStrength         | Float | 1? | Strength of the flares, affects both radius and strength. Seems no have no effect above 3. |
| FlareDuration         | Float | 30 | Duration of the player flares. |
| FlareProductionTime   | Float | 12 | Recharge time of the player's flares. It has been noted that changing this setting while in-game could cause flares to get stuck and not recharge. |
| EnvironmentalLight    | Float | 1? | Environmental (cave) light. Affects both radius and strength. |
| DisableFog            | Bool  | False | Removes "fog", making the caves look darker. It seems that after disabling it in-mission it can't be enabled again. |
| FlareGunStrength      | Float | 1? | Strength of Scout's flare gun flares. |
| FlareGunDuration      | Float | Depends on flare gun stats | Duration of Scout's flare gun flares. |

## Description
A short explanation of the difficulty.

Example:

```json
{
    "Description": "Hazard 6 with double enemies."
}
```
## DifficultySetting
Main controls for enemy resistance, swarm and wave intervals and enemy counts. The descriptions here are very summarized, please check [A Quick and Dirty Guide to Custom Difficulty for Deep Rock Galactic](https://docs.google.com/document/d/131FqOl0FnwiAslvvDSYkV35oBQXYx2kH0oZYwEpjoBI/edit?tab=t.0), a CD1 guide explaining most of the fields inside this module foe details. To see the values of these fields for the vanilla Hazards and some others, please check the [DRG Hazard Scaling](https://docs.google.com/spreadsheets/u/0/d/15L6sCaM5WdfuI65X54qDhD5sRDCGpb1Q4fkVkRhbBU4/htmlview) file.
 

| Field | Description |
| ------- | ----------| 
| BaseHazard | Declares a base vanilla hazard, with values from 1 to 5. When a CD2 JSON doesn't specify a certain field, the value is taken from the `BaseHazard` specified here.|
| ExtraLargeEnemyDamageResistance | Affects the damage resistance of the three dreadnought variants. |
| ExtraLargeEnemyDamageResistanceB | Affects the damage resistance of the Korlok Tyrant Weed. |
| ExtraLargeEnemyDamageResistanceC | Affects the damage resistance of the OMEN Tower. |
| ExtraLargeEnemyDamageResistanceD | Affects the damage resistance of Elite enemies. |
| EnemyDamageResistance | Damage resistance of most larger enemies in the game: praetorians, oppressors, menaces, goo bombers, bulk detonators, etc. |
| SmallEnemyDamageResistance | Damage resistance of everything not covered by the other resistance fields: grunts, mactera, swarmers, etc. |
| EncounterDifficulty | Difficulty of the encounters, waves that appear when the players come within a certain distance of an unexplored cave. |
| StationaryDifficulty | How many stationary enemies will spawn. |
| EnemyCountModifier | A global multiplier on the number of enemies that will spawn in waves, swarms, constant pressure, extraction, among others. |
| EnemyWaveInterval | Interval in seconds between swarms (announced). |
| EnemyNormalWaveInterval | Interval in seconds between normal (non-announced) waves. |
| EnemyNormalWaveDifficulty | How many enemies will spawn in a normal wave. |
| EnemyDiversity | Determines how many enemies will spawn in a given spawn event, given an `EnemyPool`. |
| StationaryEnemyDiversity | Enemy diversity roll for stationary enemies (everything in the `StationaryPool`). |
| VeteranNormal | Percentage of Grunt and Mactera veterans promoting from the non-veteran variants. |
| VeteranLarge | Percentage of Oppressors promoting to veterans from Praetorians.|
| EnviromentalDamageModifier ||
| PointExtractionScalar | Interval between swarms in Point Extraction, taking effect after the first swarm. The value is capped at 1 and the formula seems to be Interval = 165/ PointExtractionScalar. |
| FriendlyFireModifier | How much friendly fire players deal to each other. | 
| WaveStartDelayScale | Adds (or subtracts) a delay for the first swarm in a mission. The delay in seconds will be 150 · WaveStartDelayScale. The default is zero; if negative (eg. -1), a swarm will spawn directly at mission start. |
| SpeedModifier | Global modifier affecting the speed of ground enemies. Mactera are unaffected. |
| AttackCooldownModifier | Global modifier affecting the speed of enemy attack animations. |
| ProjectileSpeedModifier | Global modifier affecting the speed of all projectiles. |
| HealthRegenerationMax | Maximum health that the dwarves regenerate naturally to. |
| ReviveHealthRatio | Health points after revive. |

## Dwarves
Offers some controls related to the players.

| Field | Description |
| ------ | ---------|
| RegenHealthPerSecond | |
| RegenDelayAfterDamage | |
| Scale | Player size. |

## Enemies / EnemiesNoSync
See the [Enemies/EnemiesNoSync](enemies.md) section.

## EscortMule
Controls for the Drilldozer in Escort missions.

| Field | Type | Default | Comments |
| --- | ---| ----| ----- | 
| HealPerTickNormal | Float | 13| Currently unsupported.|
| HealPerTickUnderAttack | Float | 4.5 | Currently unsupported. |
| MaxAttackersOmoranFight | Float | 6 | Currently unsupported. |
| MaxHealth | Float | 520| Currently unsupported. |
| FriendlyFireModifier | Float | 0.1 | |
| NeutralDamageModifier | Float | 0.1 | |
| BigHitDamageModifier |  Float | 0.5 | |
| BigHitDamageReductionThreshold | Float | 6 | |
| PST_PoisonResistance | Float | 0.25 | Currently unsupported. |
| PST_RadiationResistance | Float |  0.5 | Currently unsupported. |
| PST_ExplosionResistance | Float |  0.5 | Currently unsupported. |

## MaxPlayers
A field accepting an int specifying the maximum number of players allowed in the lobby. 

```json
{
    "MaxPlayers": 16
}
```

## Name
The name of the difficulty. This field is necessary to be able to save the file in the in-game CD2 dropdown.
Example:

```json
{
    "Name": "Hazard 6x2 40 nitra"
}
```

## NextDifficulty
`NextDifficulty` allows CD2 to automatically pick another difficulty at two specific moments:

1. When launching a mission from the space rig. 
2. When a mission is finished.

There are many different uses for this field but a typical application is, using the `RandomChoice` mutator, choosing a difficulty at random when launching a mission:

```json
{ 
 "Name": "Difficulty Roulette", 
 "NextDifficulty": {
  "Mutate": "RandomChoice",
  "Choices": ["6x2", "6x2-ultra", "7x2", "DIIa8", "ND"]
 }
}
```

Where it is understood that all the names in the `Choices` field are other difficulties existing in your CD2 list. The same snippet can be used to change the difficulty at random in deep dive stages. 

If you don't want the difficulty to change when launching a mission from the Space Rig, the `IfOnSpaceRig` mutator can be used as follows: 

```json
{
  "NextDifficulty": {
    "Mutate": "IfOnSpaceRig",
    "Then": "",
    "Else": "My Next Difficulty"
  }
}
```

### Different difficulties in every stage of a Deep Dive 
This is a common application of `NextDifficulty` allowing to mimic the increasing difficulty of the vanilla Deep Dive with whatever set of three difficulties you choose. The way to set it up is as follows: let's say that we want to play Hazard 5x2 on Stage 1, Hazard 6x2 on Stage 2 and ND on Stage 3. We will need the three files saved in Custom Difficulty, and then we would add the following to each:

```json 
{
    "Name": "Hazard 5x2",
    ...
    "NextDifficulty": "Hazard 6x2",
    ...
}
```


```json 
{
    "Name": "Hazard 6x2",
    ...
    "NextDifficulty": "ND",
    ...
}
```

The ND file, being the one played in stage 3, doesn't need any modifications. In addition to editing the files for stage 1 and 2, you will need a "starter" file:

```json
{
    "Name": "Dive Starter",
    "NextDifficulty": "Hazard 5"
}
```

This Dive Starter will be the file you will select while on the Space Rig before starting the dive, and it should point to the difficulty you want to play on the first stage.


## NitraMultiplier
A special module that accepts a float and controls the amount of nitra generated in the map. It has a default of 1. The following snippet would generate twice the amount of nitra in a certain mission:

```json
{
    "NitraMultiplier": 2
}
```

## Pools
`Pools` is where enemies can be added or removed from the different pools in the game. For more information, [this document](https://docs.google.com/document/d/1g13t4J77OL-R5R72WK9vxErqGPINazwweAvTdi9aOVQ/edit?usp=sharing) is a detailed explanation about the pools system and how are they used when deciding which enemies are present in a mission. The accepted fields in `Pools` are:

| Field | Type |
|------| ------- |
| MinPoolSize |  Int |
| DisruptiveEnemyPoolCount | Int (min, max) |
| StationaryEnemycount | Int (min, max) |
| CommonEnemies | * |
| SpecialEnemies | * |
| DisruptiveEnemies | * |
| StationaryPool | * |
| EnemyPool | * |

The fields marked with `*` accept the `Add` (list), `Remove` (list) and `Clear` (bool) fields for adding and removing enemies at will. The `EnemyPool` can be freely manipulated with [mutators](mutators.md) during the mission, opening the possibility of adding and removing enemies based on gameplay conditions. **It is not recommended to mutate the other pools.** 

Example:

```json
{
    "Pools": {
    "MinPoolSize": 30,
    "DisruptiveEnemyPoolCount": {
      "min": 8,
      "max": 8
    },
    "StationaryEnemyCount": {
      "Min": 6,
      "Max": 6
    },
    "CommonEnemies": {
      "Add": [
        "ED_JellyBreeder_Swarm",
        "ED_PatrolBot",
        "ED_Sentinel",
        "ED_Bomber_Explosive"
      ]
    },
    "StationaryPool": {
      "Add": ["ED_ShootingPlant_NukeSingle"],
      "Remove": []
    }
  }
}
```

## Salvage
A special module offering customization options for Salvage missions. It contains three submodules: `MiniMules`, `Uplink` and `Refuel` with the following fields:

| Submodule | Field                  | Type   | Default | Description                                                                      |
| --------- | ---------------------- | ------ | ------- | -------------------------------------------------------------------------------- |
| MiniMules | ScanUsable             | Usable |         | Settings for e holding to scan for legs                                          |
| MiniMules | RepairUsable           | Usable |         | Settings for e holding to repair the minimule                                    |
| MiniMules | LegsRequired           | Int    | 3       | Number of legs that must be attached before allowing repair                      |
| MiniMules | LegsPerMule            | Int    | 4       | Number of legs to spawn per minimule                                             |
| MiniMules | LegDistance            | Float  | 1500    | Untested, should be distance legs spawn from the minimules                       |
| MiniMules | Count                  | Int    | 2       | Number of minimules to spawn (or 1.5x on long Salvage)                           |
| MiniMules | NitraToGive            | Int    | 50      | Nitra given by the mules after repairing them                                    |
| --------- | ---------------------- | ------ | ------- | -------------------------------------------------------------------------------- |
| Uplink    | RepairUsable           | Usable |         | Settings for holding e to activate the uplink                                    |
| Uplink    | Scale                  | Float  | 1       | Size of the triangulation zone                                                   |
| Uplink    | Duration               | Float  | 80      | Defense duration in seconds                                                      |
| Uplink    | ExtraDefenderBonus     | Float  | 0.25    |                                                                                  |
| Uplink    | DisableLeaveShout      | Bool   | false   | Disables mission control messages when there are no players in the defense area. |
| Uplink    | LeavePenaltyMultiplier | Float  | 1       | 1 means vanilla penalty (2x the speed progress normally increases)               |
| --------- | ---------------------- | ------ | ------- | -------------------------------------------------------------------------------- |
| Refuel    | RepairUsable           | Usable |         |                                                                                  |
| Refuel    | Scale                  | Float  | 1       | Size of the triangulation zone                                                   |
| Refuel    | Duration               | Float  | 100     | Defense duration in seconds                                                      |
| Refuel    | ExtraDefenderBonus     | Float  | 0.25    |                                                                                  |
| Refuel    | DisableLeaveShout      | Bool   | false   |                                                                                  |
| Refuel    | LeavePenaltyMultiplier | Float  | 1       | 0 means no lost progress if leaving the defense area                             |

Example: a salvage where each mule spawns 20 legs and requires 15 to be repaired, and the area of the uplink bubble is 1.5x the normal.

```json
{
    "Salvage": {
       "MiniMules": {
            "LegsPerMule": 20,
            "LegsRequired": 15
        },
        "Uplink": {
            "Scale": 1.5
        }
    }
}
```

Please see the `BySalvagePhase` [mutator](mutators.md) for values that need to change during different phases of the mission. 

## SpecialEncounters
This module controls the chance of some random events such as the Korlok, Bet-C, etc. Please note that this module is not 100 % functional as some of the encounters depend on the seasons system which CD2 cannot control for now. 
Each `SpecialEncounter` accepts the following fields:

| Field | Type | 
| ------ | ---- |
| BaseChance | Float |
| Enemy | Descriptor |
| CanSpawnInDeepDive | Bool |

The vanilla `SpecialEncounters` would look like:

```json
{
    "SpecialEncounters": [
    {
      "Enemy": "ED_InfectedMule",
      "BaseChance": 0.05,
      "CanSpawnInDeepDive": true
    },
    {
      "Enemy": "ED_Spider_ExploderTank_King",
      "BaseChance": 0.03,
      "CanSpawnInDeepDive": false
    },
    {
      "Enemy": "ED_HydraWeed",
      "BaseChance": 0.05,
      "CanSpawnInDeepDive": false
    },
    {
      "Enemy": "ED_Terminator",
      "BaseChance": 0.03,
      "CanSpawnInDeepDive": true
    }
  ]
}
```

Example: set all special encounters to zero.

```json
{
    "SpecialEncounters": []
}
```

`SpecialEncounters` can accept any enemy descriptor in its `Enemy` field and it can be used to make sure there's exactly 1 such enemy for the whole mission. As an example, some difficulties have exactly 1 Vartok Scalebramble per mission:

```json
{
    "SpecialEncounters": [
        {
          "BaseChance": 1.0,
          "CanSpawnInDeepDive": true,
          "Enemy": "ED_TentaclePlant"
        }
      ]
}
```

## Resupply
This module contains information about the resupply cost. It accepts a single `float` field `Cost` that can be [mutated](mutators.md).

Example: a fixed resupply cost of 40 nitra.

```json
{
    "Resupply": {
        "Cost": 40
    }
}
```

The `StartingNitra` field from CD1 does not exist in CD2: the same functionality is done with mutators. Example: the first resupply is free, 40 nitra for all others:

```json 
{
    "Resupply": {
        "Cost": {
            "Mutate": "ByResuppliesCalled",
            "Values": [0, 40]
        }
    }
}
```


```json
{
    "Resupply": {
      "Cost": {
        "Mutate": "IfFloat",
        "Value": {
          "Mutate": "ResuppliesCalled"
        },
        "==": 0,
        "Then": 0,
        "Else": 40
      }
    }
}
```

While both snippets do the same thing, `ByResuppliesCalled` is usually more compact when specifying a different cost for the first few supplies.

Example: the cost is 45, but after the 6th resupply it drops to 40. 

```json
{ 
  "Resupply": {
    "Cost": {
      "Mutate": "IfFloat",
      "Value": {
        "Mutate": "ResuppliesCalled"
      },
      ">": 6,
      "Then": 40,
      "Else": 45
    }
  }
}
```

## Warnings
The `Warnings` module can be used to ban mission anomalies. It accepts a single `Banned` field which is one or more from the following table:

| CD2 name | In-game name |
| -------- | ------------ |
| "MMUT_BloodSugar" | Blood Sugar |
|       "MMUT_ExplosiveEnemies" | Volatile Guts |
|       "MMUT_ExterminationContract" | Golden Bugs |
|       "MMUT_GoldRush" | Gold Rush |
|       "MMUT_LowGravity" | Low Gravity |
|       "MMUT_OxygenRich" | Rich Atmosphere |
|       "MMUT_RichInMinerals" | Mineral Mania |
|       "MMUT_SecretSecondary" | Secret Secondary |
|       "MMUT_Weakspot" | Critical Weakness |
|       "MMUT_XXXP" | Double XP |
|       "WRN_BulletHell" | Duck and Cover |
|       "WRN_CaveLeechDen" | Cave Leech Cluster |
|       "WRN_ExploderInfestation" | Exploder Infestation |
|       "WRN_Ghost" | Haunted Cave |
|       "WRN_HeroEnemies" | Elite Enemies |
|       "WRN_InfestedEnemies" | Parasites |
|       "WRN_LethalEnemies" | Lethal Enemies |
|       "WRN_MacteraCave" | Mactera Plague |
|       "WRN_NoOxygen" | Low O2 |
|       "WRN_NoShields" | Shield Disruption |
|       "WRN_Plague" | Lithophage Outbreak | 
|       "WRN_RegenerativeEnemies" | Regenerative Enemies |
|       "WRN_RivalIncursion" | Rival Presence |
|       "WRN_RockInfestation" | Ebonite Outbreak |
|       "WRN_Swarmagedon | Swarmageddon |

Example: ban Swarmageddon and Low O2 from a difficulty.

```json
{
    "Warnings": {
        "Banned": [
            "WRN_Swarmagedon",
            "WRN_NoOxygen"
        ]
    }
}
```

## WaveSpawners
See the [WaveSpawners](wavespawners.md) section. 
