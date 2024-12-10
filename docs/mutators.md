# Mutators

Here follows an alphabetized list of mutators for CD2.

## Accumulate
`Accumulate` can track changes in other mutators by adding to a starting `Initial` number. In addition, it also supports clamping the accumulated value with `Min` and `Max`. If used with a constant value, it can be used to make a simple counter.

Example: the value of the following snippet starts at 0 and would cap at 10 after roughly 10 seconds.

```json
{
    "Mutate": "Accumulate",
    "Initial": 0,
    "Value": 1,
    "Min": 0,
    "Max": 10
}
```


## Add, Subtract, Multiply, Divide, Pow, Modulo, Round, Ceil, Floor
Arithmetic mutators that can be used for basic mathematical operations.

Example: enemy speed as a linear function of resupplies called during the mission.

```json
"SpeedModifier": {
      "Mutate": "Add",
      "A": 1.35,
      "B": {
        "Mutate": "Multiply",
        "A": {
          "Mutate": "ResuppliesCalled"
        },
        "B": 0.1
      }
    }
```

## And, Or, Not 
Basic boolean operators.

## ByBiome
Change the value based on the mission biome. If a value isn't set for a biome it will use the 'Default' value. A 'Default' must be set unless a value is specified for biomes. If a biome is not recognized and no default is specified, the value for CrystallineCaverns will be used.

| Official name | Alias 1 | Alias 2 |
| ------------- |-------|------------|
| BIOME_AzureWeald | AzureWeald |
| BIOME_CrystalCaves | CrystalCave | CrystallineCaverns |
| BIOME_FungusBogs | FungusBogs |
| BIOME_HollowBough | HollowBough |
| BIOME_IceCaves | IceCaves | GlacialStrata |
| BIOME_MagmaCaves | MagmaCaves | MagmaCore |
| BIOME_SandblastedCorridors | SandblastedCorridors | Sandblasted |
| BIOME_RadioactiveZone | RadioactiveExclusionZone | REZ |
| BIOME_SaltCaves | SaltCaves | SaltPits |

## ByDDStage
Change the value based on the Deep Dive stage. If a value isn't set for a stage, it will use the 'Default' value. A 'Default' must be set.

Example: 

```json
{
    "Mutate": "ByDDStage",
    "Default": 1.2,
    "Stage1": 1.0,
    "Stage2": 1.2,
    "Stage3": 1.45
 }
```
## ByDNA
Allows setting a value based on a combination of Mission Type, Length, and Complexity:
``` json
{
  "Mutate": "ByDNA",
  "Default": 1,
  "Mining": 2,
  "Refinery": 3,
  "Refinery,x,2": 5,
  "Refinery,2": 4,
  "x,x,2": 8
}
```
The condition with the most matches will be prioritized. Mission type is prioritized over length and length over complexity. An “x” matches anything. In the above a (2,2) refinery would have the value 4.

## ByEscortPhase

Used to detect the different stages of an Escort mission:

```json
{
  "Mutate": "ByEscortPhase",
  "Default": 0,
  "InGarage": 0.1,
  "Stationary": 2,
  "Moving": 30,
  "WaitingForFuel": 400,
  "FinalEventA": 5,
  "FinalEventB": 0.6,
  "FinalEventC": 70,
  "FinalEventD": 8,
  "Finished": 900
}
```

## ByMissionType
Change the value based on mission type. If a value isn't set for a mission type it will use the 'Default' value. A 'Default' must be set unless a value is specified for all mission types.
Supported mission types:

* DeepScan
* Egg
* Elimination
* Escort
* Mining
* PE 
* Refinery
* Sabotage
* Salvage

Example: 

```json
{
    "Mutate": "ByMissionType",
    "Default": 60,
    "Egg": 70,
    "PE": 80
 }
```
## ByTime 

## ByPlayerCount
Change the value based on the number of players in-game. A solo game gets the first position in the list; two players get the second spot and so on. The last value in the list is used if there are more players than there are values in the list.

Example:

```json
{
    "Mutate": "ByPlayerCount",
    "Values": [
        80,
        120,
        180,
        180
    ]
}
```


## ByRefineryPhase

Used to detect the different stages of a Refinery mission.

```json
 {
  "Mutate": "ByRefineryPhase",
  "Default": 0,
  "Landing": 1,
  "ConnectingPipes": 2,
  "PipesConnected": 3,
  "Refining": 4,
  "RefiningStalled": 5,
  "RefiningComplete": 6,
  "RocketLaunched": 7
}
```

## Clamp
Constrain a float (number) to fall within a range. This range is inclusive. If only a min or only a max is specified, the value will only be clamped in that direction.
 
Example:

```json
{
    "Mutate": "Clamp",
    "Value": 90,
    "Min": 0,
    "Max": 100
}
```
## Delta
`Delta` can be used to detect a change in some other variable or mutator, and it is often used with `Accumulate`.

Example:
The following snippet will become momentarily true when a player receives health or shield damage.

```json
{
    "Mutate": "IfFloat",
    "Value": {
      "Mutate": "Delta",
      "Value": {
        "Mutate": "Add",
        "A": {
          "Mutate": "DwarvesHealth"
        },
        "B": {
          "Mutate": "DwarvesShield"
        }
      }
    },
    "<": 0,
    "Then": true,
    "Else": false
}
```

## DepositedResource
Count of a resource that has been deposited into the team depository. Any resource can be referenced by the name as it appears in the in-game UI.
 
Example:

```json
{
    "Mutate": "DepositedResource",
    "Resource": "Nitra"
}
```
## DescriptorExists
This is a boolean value which reflects whether an enemy descriptor is available. This is intended to allow a difficulty to fall back to a different descriptor if the desired descriptor isn't available, e.g. if MEV is not available.
Example:

```json
{
  "Mutate": "If",
  "Condition": {
    "Mutate": "DescriptorExists",
    "ED": "ED_MEV_Enemy"
  },
  "Then": ["ED_MEV_Enemy"],
  "Else": ["ED_Backup"]
}
```
## DrillerCount
Number of drillers in the lobby.
## DuringDefend
Becomes true when a black box, uplink or cell refuel is active.
## DuringDread
Becomes true whenever there is one of the following descriptors active on the map: `ED_Spider_Boss_Heavy` (Hiveguard), `ED_Spider_Boss_TwinA` (Arbalest), `ED_Spider_Boss_TwinB` (Lacerator) and `ED_Spider_Tank_Boss` (classic Dreadnought). 
## DuringDrillevator
Becomes true during the elevator phase in a Deep Scan mission. 
## DuringEggAmbush
Returns True during a non-announced wave after pulling an egg in Egg Hunts. 
## DuringEncounters
Becomes true when Encounters are being placed in the map, that is, during mission generation. One of its uses it to change descriptor properties depending on whether they are part of an encounter or not:

```json 
{
    "Enemies": {
        "ED_Spider_Exploder": {
             "Base": "ED_Spider_Exploder",
             "CanBeUsedForConstantPressure": true,
             "CanBeUsedInEncounters": true,
             "DifficultyRating": 10,
             "Rarity": {
               "Mutate": "If",
               "Condition": {
                 "Mutate": "DuringEncounters"
               },
               "Then": 0.1,
               "Else": 5.5
             }
        }
    }
}
```

The snippet will force exploders in almost all encounters by giving them a very low rarity during those.
Clearing the `EnemyPool` when `DuringEncounters` is true will remove encounters from the mission.

## DuringExtraction
Becomes true during the extraction phase of the mission, ie, when going back to the drop pod.
## DuringGenericSwarm
Becomes true during a swarm announced by Mission Control. 
## DuringMission
This is true during a mission, or true during a specific window of time during a mission if times are specified. If specified, StartingAt determines the elapsed mission time in seconds when this becomes true. If specified, StoppingAfter determines the elapsed mission time in seconds after which this is false.
 
Example:
Only add stalkers and elite guards to the pool after 240 seconds have elapsed in the mission.

```json
"EnemyPool"{
    "add" {
        "Mutate": "If", 
        "Condition": {"Mutate": "DuringMission", "StartingAfter": 240},
        "Then": ["ED_Spider_Stalker", "ED_Spider_Grunt_Guard_Elite"],
        "Else": []
    }
}
```

## DuringPECountdown
Returns True during the extraction phase of a PE mission. 

## DwarvesAmmo
Average percent ammo left for the team, 1 when all teammates have 100% of their ammo and 0 when all teammates are at 0% ammo. This works the same way as the 4 bars under the dwarves names in the UI.

## DwarvesDown
Float count of the dwarves that are currently down, 0 if no dwarves are currently downed, 4 if all 4 dwarves are down.

## DwarvesDownTime
Time in seconds that has elapsed while a dwarf has been down. If multiple dwarves are down, it's the longest time down among the downed dwarves.

## DwarvesDowns
Total number of downs for the team during the mission. This might not match the end screen because it will still count downs from disconnected players, and will not over-count downs.

## DwarvesHealth
Average health, 1 when all teammates are at 100% health and 0 when all teammates are down.

## DwarvesRevives
Total number of revives for the team during the mission. This includes IW self-revives.

## DwarvesShield
Average shields, 1 when all teammates are at full shield 0 when all teammates are at 0 shield. Untested on shield disruption.
## ElapsedExtraction
Returns the elapsed time in the extraction phase of a mission.

## EnemiesKilled
Count number of Enemies that have died this mission. Optionally, this can get the deaths of a specific enemy descriptor.
Despawned enemies because of caps are likely counted. If your difficulty despawns significant amounts of enemies, this number might not match expectations.

Examples:

Count of all enemy kills:

```json
{
    "Mutate": "EnemiesKilled"
}
```

Count of enemies that have died with a specific descriptor:

```json
{
    "Mutate": "EnemiesKilled",
    "ED": "ED_Spider_Grunt"
}
```
## EnemyCooldown


## EnemyCount
Count the number of enemies currently alive on the map. Optionally, this can get the count of a specific enemy descriptor.
It's possible for this monitor to drift slightly from the actual count if base game events don't fire, but it should always be correct.

Examples:
Count all enemies on the map:

```json
{
    "Mutate": "EnemyCount"
}
```

Count of enemies with a specific descriptor:

```json
{
    "Mutate": "EnemyCount",
    "ED": "ED_Spider_Grunt"
}
```
## EngineerCount
Number of engineers in the lobby. 
## GunnerCount
Number of gunners in the lobby.
## HeldResource
For a resource, the sum of that resource in players' inventories, not deposited.
 
Example:
```json
{
    "Mutate": "HeldResource",
    "Resource": "Apoca Bloom"
}
```
## IWsLeft
Float count of the number of IWs the team still has in reserve, 0 when no IWs remain. This will be 0 until dwarves are spawned which happens after the level is setup including encounters and terrain.

## If
Check a boolean condition, "Condition", and select either "Then" or "Else". The condition is usually another mutator that returns a boolean value.
 
Example:
Remove a fast bulk from the pool during a defense objective.

```json
{
  "Mutate": "If",
  "Condition": {"Mutate": "DuringDefend"},
  "Then": [],
  "Else": ["ED_Fast_Bulk"]
}
```
## IfFloat
Choose one value or another based on a comparison of two float values.
The two floats are specified by 'Value' and the operator to be used e.g. '>=' if the comparison was to be greater than or equal. If the condition is true the 'Then' value is used, else the 'Else' condition is used.
Valid operators are: ==, >=, >, <=, <

Example: as long as the team has called less than 2 resupplies the value is 40. After the team has called their second resupply, the value is 80.

```json
{
    "Mutate": "IfFloat",
    "Value": {"Mutate": "ResuppliesCalled"},
    "<": 2,
    "Then": 40,
    "Else": 80
}
```
## IfOnSpaceRig
Returns True on the Space Rig. 

## Max 
Returns the maximum of a value.

## Min 
Returns the minimum of a value.
## RandomChoice
Given an array of choices, choose one at random. It accepts an optional second list with weights for a weighted sampling of the choices.

Example: add either arbalests or lacerators to the enemy pool with a higher chance for arbalests.

```json
{
    "EnemyPool"{
        "add" {
            "Mutate": "RandomChoice", 
            "Choices": ["ED_Spider_Boss_TwinA", "ED_Spider_Boss_TwinB"],
            "Weights": [0.6, 0.4]
        }
    }
}
```

## RandomChoicePerMission
Choose one of a set of values for each mission. The choice is fixed to the seed of the mission. Subsequent plays of the same seed will use the same value. This mutator can be used with just `Choices`. In that case it will uniformly sample from the choices.
Optionally, a second list `Weights` provides weights for weighted sampling of the choices.

Example:

```json
{
  "Mutate": "RandomChoicePerMission",
  "Choices": [
    "bedrock",
    "hotrock",
    "dirt"
  ]
}
```

The following will be false 95 % of the time:

```json
{
  "Mutate": "RandomChoicePerMission",
  "Choices": [
    false,
    true
  ],
  "Weights": [
    95,
    5
  ]
}
```
## ResupplyUsesLeft
The count among all supply pods of uses left on a resupply. By default, resupplies start with 4 uses.

Caveat: the counts goes up immediately when a resupply is called, before it lands.

## ResuppliesCalled
Number of resupplies the team has called during the mission. This should increment almost immediately after a resupply is initiated, before another resupply can be called.
## ResupplyUsesConsumed
The number of uses that have been consumed from resupplies this mission.
## ScoutCount
Number of scouts in the lobby. 
## SquareWave
Alternates between two values with a given period.

Example:
Add and remove stalkers on alternating periods of 250 seconds. 

```json
{
    "EnemyPool": {
        "clear": false,
        "add": [
            {
              "Mutate": "IfFloat",
              "Value": {
                "Mutate": "SquareWave",
                "Period": 250,
                "High": 1,
                "Low": 0
              },
              ">": 0.5,
              "Then": ["ED_Spider_Stalker"],
              "Else": []
            }
        ],
        "remove": [
            {
              "Mutate": "IfFloat",
              "Value": {
                "Mutate": "SquareWave",
                "Period": 250,
                "High": 1,
                "Low": 0
              },
              ">": 0.5,
              "Then": [],
              "Else": ["ED_Spider_Stalker"]
            }
        ],
    }
}
```
## TimeDelta
Change a value over time. Time matches the mission clock in the escape menu in-game, including starting before players receive control of their dwarves.
The value is determined by `InitialValue + RateOfChange * Max(0, Time - StartDelay)`.

Parameters:

* `InitialValue`: Value at time 0 and up until `StartDelay`
* `StartDelay`: Time in seconds to stay at the `InitialValue` before changing. 
* `RateOfChange`: Rate per second to change the value.

Example:

```json
{
    "Mutate": "TimeDelta",
    "InitialValue": 3.1,
    "RateOfChange": 0.0033,
    "StartDelay": 400
 }
```
## TotalResource
Sum of a resource held in players inventories and the group depot. Any resource can be referenced by the name as it appears in the in-game UI.
 
Example:
```json
{
    "Mutate": "TotalResource",
    "Resource": "Morkite"
}
```
