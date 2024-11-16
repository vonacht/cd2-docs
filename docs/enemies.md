# Enemies / EnemiesNoSync
This module contains the enemy descriptors. The difficulty can only contain either the `Enemies` module or `EnemiesNoSync`: 

* `Enemies` can replicate some enemy characteristics to players, such as materials and scale, but in exchange it forces the clients to use CD2 or they will suffer a disconnect upon mission start. 
* `EnemiesNoSync` doesn't do replication to clients. A difficulty with `EnemiesNoSync` is compatible with all clients, regardless of whether they use CD1, CD2 or nothing at all. 

## Descriptor controls 

| Name                           | Type    |
| ------------------------------ | ------- |
| CanBeUsedForConstantPressure   | Boolean |
| CanBeUsedInEncounters          | Boolean |
| Rarity                         | Float   |
| DifficultyRating               | Float   |
| SpawnAmountModifier            | Float   |
| SpawnSpread                    | Float   |
| MaxSpawnCount                  | Int     |
| MinSpawnCount                  | Int     |
| UsesSpawnRarityModifiers       | Boolean |
| SpawnRarityModifiers           | *       |
| UsesVeteranLarge               | Boolean |
| VeteranClasses                 | **      |
| Significance                   | String, takes ("Swarmer", "Normal", "Critical", "Critter") |

## Enemy controls
Fields inside [[]] are special submodules that can be found in the sections that follow.

| Name                      | Type            | Comments |
| ------------------------- | --------------- | --------- |
| Alert                     | Boolean         | If True, the enemy will spawn aggroed to the player. It is True by default in enemies spawned by a [wave spawner](wavespawners.md). |
| CanPlayerStandOn          | Boolean         |  |
| CaveLeech                 | [[CaveLeech]]   | See the `CaveLeech` module below for special Cave Leech controls. |
| Courage                   | Float           | |
| DisplayName               | String          | |
| Elite                     | Float         | This field accepts a float number indicating the percentage of Elite enemies that will spawn for that descriptor. |
| EnemyHealthScaling        | String          | |
| Grabber                   | [[Grabber]]     | See the `Grabber` module below for special Grabber controls. |
| IsBossFight               | Boolean         | If True, the enemy will have a boss bar in the player UI similar to the vanilla dreadnoughts. The name in the bar will be the descriptor's `DisplayName`. |
| JellyBreeder              | [[JellyBreeder]] | See the `JellyBreeder` module below for special breeder controls. |
| Heal                      | Float           | A positive number `N` will heal the enemy `N` hps. A negative number will do `N` dps to the enemy. |
| HealthMultiplier          | Float           | |
| HealthRaw                 | Float           | |
| Materials                 | [[Materials]]   | A list of UE4 materials that will be applied to different parts of the enemy. Each enemy is different with regard to how many materials will it accept and how will they be applied, so trial and error is usually needed to get the expected results. |
| MEV                       | Special         | |
| Movement                  | [[Movement]]    | See the `Movement` submodule below. |
| NoSpawnWithin             | Float            | Removes enemies that spawn within the specified distance of the player, in cm. |
| Resistances               | [[Resistances]] | See the `Resistances` submodule below. |
| Scale                     | Float           | |
| ShowHealthBar             | Boolean         | |
| StaggerImmunityWindow     | Float           | |
| StaggerDurationMultiplier | Float           | |
| Temperature               | [[Temperature]] | See the `Temperature` submodule below. |
| TimeDilation              | Float           | Speeds up the enemy's attack and movement. Please note that time-dilating enemies can be a source of desync. |
| WeakpointHP               | Float           | |

## Resistances 
Fields for the resistances submodule. These controls can be used to define resistances to all types of damage in the game. `DamageMultiplier` is the catch-all for all damage types.

| Name                                | Type    |
| ----------------------------------- | ------- |
| InvulnerableToNonDefinedResistances | Boolean |
| DamageMultiplier                    | Float   |
| FireDamageMultiplier                | Float   |
| CorrosiveDamageMultiplier           | Float   |
| ElectricDamageMultiplier            | Float   |
| ColdDamageMultiplier                | Float   |
| KineticDamageMultiplier             | Float   |
| PhysicalDamageMultiplier            | Float   |
| ExplosionDamageMultiplier           | Float   |
| InternalDamageMultiplier            | Float   |
| RadiationDamageMultiplier           | Float   |
| PoisonDamageMultiplier              | Float   |
| PiercingDamageMultiplier            | Float   |

## Movement

| Name                          | Type                  |
| ----------------------------- | --------------------- |
| MaxPawnSpeed                  | Float                 |
| StrafeSpeed                   | Float                 |
| MinSlowdownAngle              | Float                 |
| MaxSlowdownAngle              | Float                 |
| MaxStrafeDistance             | Float                 |
| AlignDirectionSpeed           | Float                 |
| FleeSpeedBoostMultiplier      | Float                 |
| MaxAcceleration               | Float                 |
| MaxBrakingDeceleration        | Float                 |
| PathfinderSize                | Currently Unsupported |
| AlignToTargetMinRequiredAngle | Float                 |
| PathfinderPreference          | Currently Unsupported |

## CaveLeech 
Special controls for cave leeches.

| Name                       | Type  | Default |
| -------------------------- | ----- | ------- |
| BiteDamage                 | Float | 10      |
| BitesPerSecond             | Float | 1       |
| MaxDistanceXY              | Float | 1000    |
| GrapDelay                  | Float | 0.1     |
| TentacleSpeed              | Float | 600     |
| TentacleRetractSpeed       | Float | 1100    |
| TentaclePullSpeed          | Float | 2000    |
| TentacleDropPlayerSpeed    | Float | 1500    |
| TentacleDropGroundDistance | Float | 300     |
| MaxDropPlayerDuration      | Float | 2       |
| RevivedGracePeriod         | Float | 10      |

## Grabber
Special controls for grabbers.

| Name                  | Type  | Default |
| --------------------- | ----- | ------- |
| WanderingSpeed        | Float | 250     |
| WanderingAcceleration | Float | 1000    |
| ChaseSpeed            | Float | 750     |
| ChaseAcceleration     | Float | 4000    |
| CarrySpeed            | Float | 500     |
| CarryAcceleration     | Float | 3000    |
| FleeSpeed             | Float | 800     |
| FleeAcceleration      | Float | 1000    |
| ExtraUpForce          | Float | 15      |
| PreventGrabAfterSpawn | Float | 3       |
| GrabTime              | Float | 20      |
| DamageTimeLimit       | Float | 4       |
| DamageThreshold       | Float | 25      |
| RevivedGravePeriod    | Float | 5       |

## JellyBreeder 
Special controls for breeders.

| Name                        | Type     | Default | Comments |
| --------------------------- | -------- | ------- | ----------- |
| EnemyToSpawn                | ED       |         | Can be mutated. |
| TimeBetweenBursts           | Float    | 20      |             |
| TimeBetweenEggs             | Float    | 3       |             |
| CloseToSpawnEggTime         | Float    | 3       |             |
| EggBurstSize                | Int      | 3       |             |
| MaxJellies                  | Int      | 25      |             |
| MultiplierOnHighPlayerCount | Float    | 1.5     |             |
| SpawnAmount                 | Int      | 4       |             |
| EggName                     | String   |         |             |
| EggMaterial                 | Material |         |             |
| EggHealth                   | Float    | 125     |             |
| EggSpeed                    | Float    | 1.0     |             |
| EggTime                     | Float    | 17      |             |

Example:

```json
{
  "Name": "CD2 Beta 6 Test - Breeder Update",
  "Enemies": {
    "ED_GruntBreeder": {
      "Base": "ED_JellyBreeder",
      "DisplayName": "Greeder",
      "Materials": [
        "M_Spider_Grunt_Body_Generic",
        "M_Spider_Grunt_Armor_Guard01",
        "M_Spider_Grunt_Armor_Generic",
        "M_Spider_Grunt_Armor_Guard01",
        "M_Jelly_Breeder_Spike",
        "M_Spider_Grunt_Armor_SlasherClaws"
      ],
      "JellyBreeder": {
        "EnemyToSpawn": "ED_Spider_Grunt",
        "SpawnAmount": 1,
        "TimeBetweenBursts": 40,
        "EggBurstSize": 18,
        "TimeBetweenEggs": 0.5,
        "EggName": "Grunt Egg",
        "EggMaterial": "M_Spider_Grunt_Armor_Guard01",
        "EggHealth": 5,
        "EggTime": 1
      }
    },
    "ED_StalkerBreeder": {
      "Base": "ED_JellyBreeder",
      "DisplayName": "Stalker Breeder",
      "ShowHealthBar": false,
      "Materials": [
        "M_Spider_Stalker_Camouflage",
        "M_Spider_Stalker_Camouflage",
        "M_Spider_Stalker_Camouflage",
        "M_Spider_Stalker_Camouflage",
        "M_Spider_Stalker_Camouflage",
        "M_Spider_Stalker_Camouflage",
        "M_Spider_Stalker_Camouflage"
      ],
      "JellyBreeder": {
        "EnemyToSpawn": "ED_Spider_Stalker",
        "SpawnAmount": 1,
        "TimeBetweenBursts": 40,
        "EggBurstSize": 1,
        "TimeBetweenEggs": 2,
        "EggName": "Stalker Egg",
        "EggMaterial": "M_Spider_Stalker_Camouflage",
        "EggHealth": 80,
        "EggTime": 40
      }
    }
  }
}
```

## Temperature
Special temperature controls to change how enemies react to heat and cold.

| Name                   | Type    |
| ---------------------- | ------- |
| DieIfFrozen            | Boolean |
| DieIfBurning           | Boolean |
| IsHeatsourceWhenOnFire | Boolean |
| OnFireHeatRange        | Float   |
| BurnTemperature        | Float   |
| DouseFireTemperature   | Float   |
| FreezeTemperature      | Float   |
| UnfreezeTemperature    | Float   |
| WarmingRate            | Float   |
| CoolingRate            | Float   |
| TemperatureChangeScale | Float   |
| FozenDamageBonusScale  | Float   |
| MaxColdSlowdown        | Float   |

Example: the following snippet use the `Temperature` module to make dreadnoughts ignitable.

```json
{ 
    "Enemies": {
        "ED_Spider_Boss_Heavy": {
          "Resistances": {"DamageMultiplier": 1.23, "FireDamageMultiplier": 1.2},
          "Temperature": {"BurnTemperature": 100, "DouseFireTemperature": 50}
        },
        "ED_Spider_Boss_TwinA": {
          "Resistances": {"DamageMultiplier": 1.3, "FireDamageMultiplier": 1.2},
          "Temperature": {"BurnTemperature": 100, "DouseFireTemperature": 50}
        },
        "ED_Spider_Boss_TwinB": {
          "Resistances": {"DamageMultiplier": 1.23, "FireDamageMultiplier": 1.2},
          "Temperature": {"BurnTemperature": 100, "DouseFireTemperature": 50}
        }
    }
}
```
