# InediaInfectedAIConfig.json
    {
        "Zombies": {
            "Groups": {
                "police": [
                    "ZmbF_PoliceWomanNormal_Base",
                    "ZmbM_PolicemanFat_Base",
                    "ZmbM_PolicemanSpecForce_Base"
                ],
                "highstr": [
                    "military",
                    "police",
                    "firefighters",
                    "hunters",
                    "ZmbM_Gamedev_Base"
                ],
                "highdef": [
                    "military",
                    "police",
                    "firefighters",
                    "hunters",
                    "ZmbM_Gamedev_Base"
                ],
                "priests": [
                    "ZmbM_priestPopSkinny_Base"
                ],
                "lowstr": [
                    "city",
                    "villagers",
                    "fishermen"
                ],
                "industrial": [
                    "ZmbF_BlueCollarFat_Base",
                    "ZmbF_MechanicNormal_Base",
                    "ZmbM_ConstrWorkerNormal_Base",
                    "ZmbM_HandymanNormal_Base",
                    "ZmbM_HeavyIndustryWorker_Base",
                    "ZmbM_MechanicSkinny_Base",
                    "ZmbM_OffshoreWorker_Base"
                ],
                "villagers": [
                    "ZmbF_Runner_Base",
                    "ZmbF_MilkMaidOld_Base",
                    "ZmbF_MilkMaidOld_LT_Base",
                    "ZmbF_VillagerOld_Base",
                    "ZmbF_VillagerOld_LT_Base",
                    "ZmbM_FarmerFat_Base",
                    "ZmbM_FarmerFat_LT_Base",
                    "ZmbM_Jacket_Base",
                    "ZmbM_Jacket_LT_Base",
                    "ZmbM__Runner_Base",
                    "ZmbM_VillagerOld_Base",
                    "ZmbM_VillagerOld_LT_Base",
                    "ZmbF_HikerSkinny_Base",
                    "ZmbM_HermitSkinny_Base",
                    "ZmbM_HikerSkinny_Base"
                ],
                "mediumdef": [
                    "medics",
                    "industrial",
                    "priests",
                    "prisoners"
                ],
                "bears": [
                    "Animal_UrsusArctos"
                ],
                "lowdef": [
                    "city",
                    "villagers",
                    "fishermen"
                ],
                "wolves": [
                    "Animal_CanisLupus"
                ],
                "city": [
                    "ZmbF_CitizenANormal_Base",
                    "ZmbF_CitizenBSkinny_Base",
                    "ZmbF_Clerk_Normal_Base",
                    "ZmbF_Clerk_Normal_LT_Base",
                    "ZmbF_JournalistNormal_Base",
                    "ZmbF_JournalistNormal_LT_Base",
                    "ZmbF_ShortSkirt_Base",
                    "ZmbF_ShortSkirt_LT_Base",
                    "ZmbF_SkaterYoung_Base",
                    "ZmbM_SkaterYoung_Base",
                    "ZmbM_SkaterYoung_LT_Base",
                    "ZmbF_SurvivorNormal_Base",
                    "ZmbF_SurvivorNormal_LT_Base",
                    "ZmbM_CitizenASkinny_Base",
                    "ZmbM_CitizenASkinny_LT_Base",
                    "ZmbM_CitizenBFat_Base",
                    "ZmbM_ClerkFat_Base",
                    "ZmbM_ClerkFat_LT_Base",
                    "ZmbF_ClerkFat_Base",
                    "ZmbM_CommercialPilotOld_Base",
                    "ZmbM_CommercialPilotOld_LT_Base",
                    "ZmbM_JournalistSkinny_Base",
                    "ZmbM_MotobikerFat_Base"
                ],
                "firefighters": [
                    "ZmbM_FirefighterNormal_Base"
                ],
                "medics": [
                    "ZmbF_DoctorSkinny_Base",
                    "ZmbF_NurseFat_Base",
                    "ZmbF_ParamedicNormal_Base",
                    "ZmbM_ParamedicNormal_Base",
                    "ZmbM_DoctorFat_Base",
                    "ZmbF_PatientOld_Base",
                    "ZmbM_PatientSkinny_Base"
                ],
                "prisoners": [
                    "ZmbM_PrisonerSkinny_Base"
                ],
                "mediumstr": [
                    "medics",
                    "industrial",
                    "priests",
                    "prisoners"
                ],
                "hunters": [
                    "ZmbM_HunterOld_Base"
                ],
                "military": [
                    "ZmbM_SoldierNormal_Base"
                ],
                "fishermen": [
                    "ZmbM_FishermanOld_Base"
                ]
            },
            "CustomIrritants": {
                "matches": {
                    "Classes": [
                        "Single_Match",
                        "New_Candle"
                    ],
                    "RadiusOutdoorDay": 0.0,
                    "RadiusOutdoorNight": 40.0,
                    "RadiusIndoorDay": 0.0,
                    "RadiusIndoorNight": 8.0,
                    "Type": 0.0,
                    "Priority": 1.0
                }
            },
            "ThrowingProjectiles": {
                "PoliceProjectile": {
                    "ItemClasses": [
                        "Glock19",
                        "MakarovIJ70",
                        "Mp133Shotgun",
                        "CombatKnife",
                        "CombatKnife"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "HuntersProjectile": {
                    "ItemClasses": [
                        "GlassBottle",
                        "HuntingKnife",
                        "HuntingKnife",
                        "Canteen",
                        "Binoculars"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "FirefightersProjectile": {
                    "ItemClasses": [
                        "FirefightersHelmet_Red",
                        "FirefightersHelmet_White",
                        "FirefightersHelmet_Yellow",
                        "FirefighterAxe",
                        "FirefighterAxe"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "MilitaryProjectile": {
                    "ItemClasses": [
                        "Binoculars",
                        "Ssh68Helmet",
                        "GorkaHelmet",
                        "BallisticHelmet_Green",
                        "Canteen",
                        "CombatKnife",
                        "AK_Bayonet",
                        "SKS_Bayonet",
                        "M9A1_Bayonet",
                        "Mosin_Bayonet"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "CityProjectile": {
                    "ItemClasses": [
                        "GlassBottle",
                        "WaterBottle",
                        "BaseballBat",
                        "Pipe",
                        "Flashlight",
                        "CombinationLock",
                        "KitchenKnife",
                        "KitchenKnife",
                        "SteakKnife"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "FlashGrenade": {
                    "ItemClasses": [
                        "FlashGrenade"
                    ],
                    "Parameters": {
                        "DestroyProjectileAfterSeconds": -1.0,
                        "ThrowConditionAmountOfProjectiles": 1.0,
                        "ActivateGrenadeAfterSeconds": 0.0
                    }
                },
                "GasGrenade": {
                    "ItemClasses": [
                        "Grenade_ChemGas"
                    ],
                    "Parameters": {
                        "DestroyProjectileAfterSeconds": -1.0,
                        "ThrowConditionAmountOfProjectiles": 1.0,
                        "ActivateGrenadeAfterSeconds": 0.0
                    }
                },
                "VillagersProjectile": {
                    "ItemClasses": [
                        "GlassBottle",
                        "FryingPan",
                        "Firewood",
                        "Pot",
                        "Hammer",
                        "MeatTenderizer",
                        "KitchenKnife",
                        "Pitchfork",
                        "Hatchet",
                        "Sickle",
                        "WoodAxe",
                        "Cleaver",
                        "Shovel",
                        "FarmingHoe"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "GarbageIfPlayerOnObstacle": {
                    "ItemClasses": [
                        "WoodenStick",
                        "SmallStone"
                    ],
                    "Parameters": {
                        "ThrowConditionZombieTargetVerticalDistanceMin": 0.5,
                        "TargetStunChancePercent": 50.0,
                        "ThrowConditionGroundTargetDistanceMin": 0.5,
                        "TargetShockDamage": 20.0,
                        "TargetHealthDamage": 5.0,
                        "TargetBleedingChancePercent": 5.0,
                        "ThrowConditionCooldownSeconds": 5.0
                    }
                },
                "IndustrialProjectile": {
                    "ItemClasses": [
                        "GlassBottle",
                        "Pipe",
                        "PipeWrench",
                        "Wrench",
                        "LugWrench",
                        "Hammer",
                        "WeldingMask",
                        "Crowbar",
                        "HandSaw",
                        "Hacksaw",
                        "Screwdriver",
                        "Pliers"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "GarbageIfPlayerNonObstacle": {
                    "ItemClasses": [
                        "WoodenStick",
                        "SmallStone"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "TargetBleedingChancePercent": 5.0,
                        "TargetStunChancePercent": 50.0,
                        "TargetShockDamage": 20.0,
                        "TargetHealthDamage": 5.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "MedicsProjectile": {
                    "ItemClasses": [
                        "GlassBottle",
                        "KitchenKnife",
                        "KitchenKnife",
                        "SteakKnife",
                        "GasMask_Filter",
                        "IodineTincture",
                        "DisinfectantAlcohol",
                        "DisinfectantSpray"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "FishermenProjectile": {
                    "ItemClasses": [
                        "GlassBottle",
                        "HuntingKnife",
                        "KitchenKnife",
                        "Canteen",
                        "FishingRod",
                        "Shovel"
                    ],
                    "Parameters": {
                        "ThrowConditionAmountOfProjectiles": 2.0,
                        "ThrowConditionThrowChancePercent": 10.0,
                        "ThrowConditionCooldownSeconds": 10.0
                    }
                },
                "HEGrenade": {
                    "ItemClasses": [
                        "RGD5Grenade",
                        "M67Grenade"
                    ],
                    "Parameters": {
                        "DestroyProjectileAfterSeconds": -1.0,
                        "ThrowConditionAmountOfProjectiles": 1.0,
                        "ActivateGrenadeAfterSeconds": 5.0
                    }
                }
            },
            "BreakingDoorsHandlerIsActive": {
                "all": 1
            },
            "BreakingDoorsRestrictedDoors": {
                "all": {
                    "DNA_Lockout_OneWayDoor": [],
                    "Jmc_Security_Door": [],
                    "DNA_Lockout_Dbl_ColourBase": [],
                    "land_bunker_entrance": [],
                    "land_bunker_entrance1": [],
                    "land_bunker_entrance2": [],
                    "DNA_Lockout_ColourBase": [],
                    "DNA_Strongroom_ColourBase": [],
                    "Jmc_Security_Door_Carrier": [],
                    "land_bunker_door_base": [],
                    "Land_KlimaX_T3Door": [],
                    "EVG_KeycardDoor": [],
                    "DNA_Strongroom_Open_Base": [],
                    "land_bunker_door_area04": [],
                    "DNA_WarpDoor_NoLock": [],
                    "DNA_Door_NoLock_Dbl_ColourBase": [],
                    "Land_KlimaX_T1Door": [],
                    "DNA_LockoutSteel_ColourBase": [],
                    "Land_KlimaX_T2Door": [],
                    "DNA_Door_NoLock_ColourBase": [],
                    "Land_WarheadStorage_Main": []
                }
            },
            "BreakingDoorsDestroyAfterOpenChancePercent": {
                "all": 30.0,
                "highstr": 50.0,
                "mediumstr": 40.0,
                "lowstr": 30.0
            },
            "BreakingDoorsOpenChancePercent": {
                "all": 30.0,
                "highstr": 50.0,
                "mediumstr": 40.0,
                "lowstr": 30.0
            },
            "BreakingDoorsOpenLockPickChancePercent": {
                "all": 5.0
            },
            "BreakingDoorsLossInterestAfterHitChancePercent": {
                "all": 5.0
            },
            "BreakingDoorsLossInterestAfterHitLockPickChancePercent": {
                "all": 25.0
            },
            "BreakingDoorsCrawlersChanceMultiplier": {
                "all": 0.0
            },
            "AttackPlayersUnconsciousHandlerIsActive": {
                "all": 1
            },
            "AttackPlayersUnconsciousHitsLimit": {
                "all": 5.0
            },
            "AttackAnimalsHandlerIsActive": {
                "all": 1
            },
            "AttackAnimalsWildBoar": {
                "all": 1
            },
            "AttackAnimalsPig": {
                "all": 1
            },
            "AttackAnimalsSheep": {
                "all": 1
            },
            "AttackAnimalsDeer": {
                "all": 1
            },
            "AttackAnimalsRoeDeer": {
                "all": 1
            },
            "AttackAnimalsGoat": {
                "all": 1
            },
            "AttackAnimalsCow": {
                "all": 1
            },
            "AttackAnimalsCustom": {
                "all": {
                    "all": 0
                }
            },
            "FriendlyNPC": {
                "all": []
            },
            "SearchHandlerIsActive": {
                "all": 1
            },
            "SearchSphereRadiusIncreaseEverySeconds": {
                "all": 0.20000000298023225
            },
            "SearchSphereDistanceToRadiusMultiplier": {
                "all": 0.30000001192092898
            },
            "SearchSphereRadiusMin": {
                "all": 0.0
            },
            "SearchSphereRadiusMax": {
                "all": 50.0
            },
            "SearchSphereRadiusBurst": {
                "all": 60.0
            },
            "SpeedHandlerIsActive": {
                "all": 1
            },
            "SpeedMinimumInCalmMode": {
                "all": 0.0
            },
            "SpeedLimitInCalmMode": {
                "all": 3.0
            },
            "SpeedMultiplierInCalmMode": {
                "all": 1.0
            },
            "SpeedMinimumInSearchMode": {
                "all": 0.0
            },
            "SpeedLimitInSearchMode": {
                "all": 3.0
            },
            "SpeedMultiplierInSearchMode": {
                "all": 1.0
            },
            "SpeedMinimumInChaseMode": {
                "all": 0.0
            },
            "SpeedLimitInChaseMode": {
                "all": 3.0
            },
            "SpeedMultiplierInChaseMode": {
                "all": 1.0
            },
            "SpeedNoLimitsFromDistanceMeters": {
                "all": 0.0
            },
            "SmellsHandlerIsActive": {
                "all": 1
            },
            "SmellsSphereRadius": {
                "all": 2.0
            },
            "SmellsAllowStealthKills": {
                "all": 1
            },
            "SmellsLossInterestAfterReactionForSeconds": {
                "all": 0.0
            },
            "UpJumpHandlerIsActive": {
                "all": 1
            },
            "UpJumpHeightMax": {
                "all": 1.7999999523162842
            },
            "UpJumpImpulseDamageChancePercent": {
                "all": 50.0
            },
            "UpJumpChancePercent": {
                "all": 100.0
            },
            "UpJumpCooldownSeconds": {
                "all": 0.0
            },
            "DownJumpHandlerIsActive": {
                "all": 1
            },
            "DownJumpHeightMax": {
                "all": 30.0
            },
            "StuckJumpHandlerIsActive": {
                "all": 1
            },
            "FallHandlerIsActive": {
                "all": 1
            },
            "FallHandlerLegBreakHeightMin": {
                "all": 3.0
            },
            "FallHandlerLegBreakHeightMax": {
                "all": 15.0
            },
            "FallHandlerDeathHeightMin": {
                "all": 10.0
            },
            "FallHandlerDeathHeightMax": {
                "all": 20.0
            },
            "InjuryHandlerIsActive": {
                "all": 1
            },
            "InjuryHandlerInjuryOnExplosiveDamageChancePercent": {
                "all": 100.0
            },
            "InjuryHandlerDamageThresholdToInjuryArm": {
                "all": 30.0
            },
            "InjuryHandlerRestoreInjuredArmAfterSeconds": {
                "all": 0.0
            },
            "InjuryHandlerInjuredOneArmAttackMultiplier": {
                "all": 0.5
            },
            "InjuryHandlerInjuredBothArmsAttackMultiplier": {
                "all": 0.20000000298023225
            },
            "InjuryHandlerInjuredOneArmBreakingDoorChanceMultiplier": {
                "all": 0.5
            },
            "InjuryHandlerInjuredBothArmsBreakingDoorChanceMultiplier": {
                "all": 0.0
            },
            "InjuryHandlerInjuredOneArmStunChanceMultiplier": {
                "all": 0.5
            },
            "InjuryHandlerInjuredBothArmsStunChanceMultiplier": {
                "all": 0.0
            },
            "InjuryHandlerInjuredOneArmPainMultiplier": {
                "all": 0.5
            },
            "InjuryHandlerInjuredBothArmsPainMultiplier": {
                "all": 0.0
            },
            "InjuryHandlerInjuredOneArmBleedingChanceMultiplier": {
                "all": 0.5
            },
            "InjuryHandlerInjuredBothArmsBleedingChanceMultiplier": {
                "all": 0.0
            },
            "InjuryHandlerSpawnWithInjuredOneArmChancePercent": {
                "all": 0.0
            },
            "InjuryHandlerSpawnWithInjuredBothArmsChancePercent": {
                "all": 0.0
            },
            "InjuryHandlerDamageThresholdToInjuryLeg": {
                "all": 30.0,
                "bears": 50.0
            },
            "InjuryHandlerRestoreInjuredLegAfterSeconds": {
                "all": 0.0,
                "AnimalBase": 900.0
            },
            "InjuryHandlerInjuredOneLegSpeedLimit": {
                "all": 2.0999999046325685
            },
            "InjuryHandlerInjuredBothLegsSpeedLimit": {
                "all": 1.0
            },
            "InjuryHandlerInjuredOneLegJumpHeightMultiplier": {
                "all": 0.5
            },
            "InjuryHandlerInjuredBothLegsJumpHeightMultiplier": {
                "all": 0.0
            },
            "InjuryHandlerSpawnWithInjuredOneLegChancePercent": {
                "all": 0.0
            },
            "InjuryHandlerSpawnWithInjuredBothLegsChancePercent": {
                "all": 0.0
            },
            "AttackCarHandlerIsActive": {
                "all": 1
            },
            "AttackCarPlayersIsActive": {
                "all": 1
            },
            "AttackCarPlayersDistanceMeters": {
                "all": 2.0
            },
            "AttackCarElementsIsActive": {
                "wolves": 0,
                "all": 1
            },
            "AttackCarElementsDistanceMeters": {
                "all": 2.0
            },
            "AttackCarElementsGlobalDamageMultiplier": {
                "all": 1.0,
                "bears": 3.0
            },
            "AttackCarElementsByCollisionsIsActive": {
                "all": 1
            },
            "AttackCarElementsByCollisionsGlobalDamageMultiplier": {
                "all": 1.0
            },
            "AttackCarElementsMultiplierByCarClassId": {
                "all": {
                    "all": 1.0,
                    "ExpansionTractor": 0.3499999940395355,
                    "Expansion_Landrover": 0.6000000238418579,
                    "OffroadHatchback": 0.800000011920929,
                    "ExpansionUh1h": 0.30000001192092898,
                    "Truck_01_Covered": 0.3499999940395355,
                    "Offroad_02": 0.20000000298023225,
                    "ExpansionMh6": 0.4000000059604645,
                    "ExpansionMerlin": 0.20000000298023225,
                    "ExpansionVodnik": 0.20000000298023225,
                    "ExpansionUAZ": 0.6000000238418579,
                    "ExpansionBus": 0.3499999940395355
                }
            },
            "AttackCarWindowDamagePercent": {
                "all": 25.0
            },
            "AttackCarDoorDamagePercent": {
                "all": 20.0
            },
            "AttackCarDoorChancePercent": {
                "all": 60.0
            },
            "AttackCarRadiatorDamagePercent": {
                "all": 10.0
            },
            "AttackCarCarBatteryDamagePercent": {
                "all": 10.0
            },
            "AttackCarPlugDamagePercent": {
                "all": 25.0
            },
            "AttackCarEngineDamagePercent": {
                "all": 10.0
            },
            "AttackCarLightsDamagePercent": {
                "all": 50.0
            },
            "AttackCarFenderDamagePercent": {
                "all": 10.0
            },
            "AttackCarBumperDamagePercent": {
                "all": 10.0
            },
            "AttackCarHoodDamagePercent": {
                "all": 10.0
            },
            "AttackCarFuelTankDamagePercent": {
                "all": 5.0
            },
            "ReactHandlerIsActive": {
                "all": 1
            },
            "ReactBehindVisualMultiplier": {
                "all": 0.20000000298023225
            },
            "ReactBehindNoiseMultiplier": {
                "all": 0.6000000238418579
            },
            "ReactFireplaceVisual": {
                "all": 1.0
            },
            "ReactFireplaceDayVisual": {
                "all": 1.0
            },
            "ReactFlashlightsVisual": {
                "all": 1.0
            },
            "ReactHeadtorchRedVisual": {
                "all": 1.0
            },
            "ReactRoadflareVisual": {
                "all": 1.0
            },
            "ReactRoadflareNoise": {
                "all": 1.0
            },
            "ReactChemlightVisual": {
                "all": 1.0
            },
            "ReactChemlightRedVisual": {
                "all": 1.0
            },
            "ReactPortableGasLampVisual": {
                "all": 1.0
            },
            "ReactFlammablesVisual": {
                "all": 1.0
            },
            "ReactSpotlightVisual": {
                "all": 1.0
            },
            "ReactCarLightVisual": {
                "all": 1.0
            },
            "ReactPowerGeneratorNoise": {
                "all": 1.0
            },
            "ReactCarHornNoise": {
                "all": 1.0
            },
            "ReactAlarmClockNoise": {
                "all": 1.0
            },
            "ReactKitchenTimerNoise": {
                "all": 1.0
            },
            "ReactFuelStationNoise": {
                "all": 1.0
            },
            "ReactFireworksNoise": {
                "all": 1.0
            },
            "ReactExplosiveItemNoise": {
                "all": 1.0
            },
            "ReactCarEngineNoise": {
                "all": 1.0
            },
            "ReactSmokeGrenadeVisual": {
                "all": 1.0
            },
            "ReactScreamNoise": {
                "all": 1.0
            },
            "ReactWeaponShotNoise": {
                "all": 1.0
            },
            "ReactFootstepsJogDayNoise": {
                "all": 1.0
            },
            "ReactFootstepsJogNightNoise": {
                "all": 1.0
            },
            "ReactFootstepsCrouchSprintDayNoise": {
                "all": 0.699999988079071
            },
            "ReactFootstepsCrouchSprintNightNoise": {
                "all": 0.699999988079071
            },
            "ReactFootstepsSprintDayNoise": {
                "all": 1.0
            },
            "ReactFootstepsSprintNightNoise": {
                "all": 1.0
            },
            "ReactDoorsDayNoise": {
                "all": 1.0
            },
            "ReactDoorsNightNoise": {
                "all": 1.0
            },
            "ReactPlayerFallDayNoise": {
                "all": 1.0
            },
            "ReactPlayerFallNightNoise": {
                "all": 1.0
            },
            "ReactBodyfallDayNoise": {
                "all": 0.5
            },
            "ReactBodyfallNightNoise": {
                "all": 0.5
            },
            "ReactBodyfallBackstabDayNoise": {
                "all": 0.0
            },
            "ReactBodyfallBackstabNightNoise": {
                "all": 0.0
            },
            "ReactSymptomsDayNoise": {
                "all": 1.0
            },
            "ReactSymptomsNightNoise": {
                "all": 1.0
            },
            "ReactVoiceWhisperDayNoise": {
                "all": 1.0
            },
            "ReactVoiceWhisperNightNoise": {
                "all": 1.0
            },
            "ReactVoiceTalkDayNoise": {
                "all": 1.0
            },
            "ReactVoiceTalkNightNoise": {
                "all": 1.0
            },
            "ReactVoiceShoutDayNoise": {
                "all": 1.0
            },
            "ReactVoiceShoutNightNoise": {
                "all": 1.0
            },
            "ReactMiningLightDayNoise": {
                "all": 1.0
            },
            "ReactMiningLightNightNoise": {
                "all": 1.0
            },
            "ReactMiningHardDayNoise": {
                "all": 1.0
            },
            "ReactMiningHardNightNoise": {
                "all": 1.0
            },
            "ReactBuildingDayNoise": {
                "all": 1.0
            },
            "ReactBuildingNightNoise": {
                "all": 1.0
            },
            "ReactSawPlanksDayNoise": {
                "all": 1.0
            },
            "ReactSawPlanksNightNoise": {
                "all": 1.0
            },
            "ReactVanillaMindstateChange": {
                "all": 1.0
            },
            "ReactCustomIrritants": {
                "all": {
                    "matches": {
                        "React": 1.0,
                        "Destroy": 1.0
                    }
                }
            },
            "ReactAndDestroyFlashlightsVisual": {
                "all": 1.0
            },
            "ReactAndDestroyHeadtorchRedVisual": {
                "all": 1.0
            },
            "ReactAndDestroyRoadflareVisual": {
                "all": 1.0
            },
            "ReactAndDestroyRoadflareNoise": {
                "all": 1.0
            },
            "ReactAndDestroyChemlightVisual": {
                "all": 1.0
            },
            "ReactAndDestroyChemlightRedVisual": {
                "all": 1.0
            },
            "ReactAndDestroyPortableGasLampVisual": {
                "all": 1.0
            },
            "ReactAndDestroyFlammablesVisual": {
                "all": 0.5
            },
            "ReactAndDestroySpotlightVisual": {
                "all": 0.25
            },
            "ReactAndDestroyFireplaceVisual": {
                "all": 0.25
            },
            "ReactAndDestroyFireplaceDayVisual": {
                "all": 0.25
            },
            "ReactAndDestroyCarLightVisual": {
                "all": 1.0
            },
            "ReactAndDestroyFireworksNoise": {
                "all": 0.25
            },
            "ReactAndDestroyPowerGeneratorNoise": {
                "all": 0.10000000149011612
            },
            "ReactAndDestroyAlarmClockNoise": {
                "all": 1.0
            },
            "ReactAndDestroyKitchenTimerNoise": {
                "all": 1.0
            },
            "ReactAndDestroySmokeGrenadeVisual": {
                "all": 0.5
            },
            "DamageToPlayerHandlerIsActive": {
                "all": 1
            },
            "DamageToPlayerHealthMultiplier": {
                "all": 1.2000000476837159,
                "highstr": 1.399999976158142,
                "mediumstr": 1.2999999523162842,
                "lowstr": 1.2000000476837159
            },
            "DamageToPlayerShockMultiplier": {
                "all": 1.2000000476837159,
                "highstr": 1.399999976158142,
                "mediumstr": 1.2999999523162842,
                "lowstr": 1.2000000476837159
            },
            "DamageToPlayerStaminaPercent": {
                "all": 12.0,
                "highstr": 20.0,
                "mediumstr": 16.0,
                "lowstr": 12.0
            },
            "DamageToPlayerBloodPercent": {
                "all": 0.0
            },
            "DamageToPlayerBleedingHandlerIsActive": {
                "all": 1
            },
            "DamageToPlayerBleedingChancePercent": {
                "all": 10.0,
                "highstr": 16.0,
                "mediumstr": 13.0,
                "lowstr": 10.0
            },
            "DamageToPlayerInBlockHealthMultiplier": {
                "all": 0.6000000238418579,
                "highstr": 0.699999988079071,
                "mediumstr": 0.6499999761581421,
                "lowstr": 0.6000000238418579
            },
            "DamageToPlayerInBlockShockMultiplier": {
                "all": 0.6000000238418579,
                "highstr": 0.699999988079071,
                "mediumstr": 0.6499999761581421,
                "lowstr": 0.6000000238418579
            },
            "DamageToPlayerInBlockStaminaPercent": {
                "all": 6.0,
                "highstr": 10.0,
                "mediumstr": 8.0,
                "lowstr": 6.0
            },
            "DamageToPlayerInBlockBloodPercent": {
                "all": 0.0
            },
            "DamageToPlayerInBlockBleedingChancePercent": {
                "all": 5.0,
                "highstr": 8.0,
                "mediumstr": 6.5,
                "lowstr": 5.0
            },
            "StunToPlayerChancePercent": {
                "all": 25.0,
                "highstr": 35.0,
                "mediumstr": 30.0,
                "lowstr": 25.0
            },
            "StunToPlayerInBlockChancePercent": {
                "all": 12.5,
                "highstr": 17.5,
                "mediumstr": 15.0,
                "lowstr": 12.5
            },
            "DisarmToPlayerChancePercent": {
                "all": 0.0
            },
            "DisarmToPlayerInBlockChancePercent": {
                "all": 0.0
            },
            "DiseasesToPlayerHandlerIsActive": {
                "all": 1
            },
            "DiseasesToPlayerAgents": {
                "AnimalBase": [
                    {
                        "AgentId": 64,
                        "AddChance": 10.0,
                        "AddChanceInBlock": 5.0,
                        "AddAmount": 10.0,
                        "AddAmountInBlock": 5.0,
                        "AddAmountNoMoreThan": 50.0,
                        "AddOnlyIfBleeding": 1
                    }
                ],
                "all": [],
                "highstr": [
                    {
                        "AgentId": 64,
                        "AddChance": 20.0,
                        "AddChanceInBlock": 10.0,
                        "AddAmount": 10.0,
                        "AddAmountInBlock": 5.0,
                        "AddAmountNoMoreThan": 50.0,
                        "AddOnlyIfBleeding": 1
                    }
                ],
                "mediumstr": [
                    {
                        "AgentId": 64,
                        "AddChance": 15.0,
                        "AddChanceInBlock": 7.5,
                        "AddAmount": 10.0,
                        "AddAmountInBlock": 5.0,
                        "AddAmountNoMoreThan": 50.0,
                        "AddOnlyIfBleeding": 1
                    }
                ],
                "lowstr": [
                    {
                        "AgentId": 64,
                        "AddChance": 10.0,
                        "AddChanceInBlock": 5.0,
                        "AddAmount": 10.0,
                        "AddAmountInBlock": 5.0,
                        "AddAmountNoMoreThan": 50.0,
                        "AddOnlyIfBleeding": 1
                    }
                ]
            },
            "CameraShakeToPlayerIntensity": {
                "all": 10.0
            },
            "PainToPlayerHandlerIsActive": {
                "all": 1
            },
            "PainToPlayerHeadMultiplier": {
                "all": 1.2000000476837159,
                "SurvivorBase": 1.0,
                "highstr": 1.399999976158142,
                "mediumstr": 1.2999999523162842,
                "lowstr": 1.2000000476837159
            },
            "PainToPlayerHeadInBlockMultiplier": {
                "all": 0.6000000238418579,
                "SurvivorBase": 0.5,
                "highstr": 0.699999988079071,
                "mediumstr": 0.6499999761581421,
                "lowstr": 0.6000000238418579
            },
            "PainToPlayerArmsMultiplier": {
                "all": 1.2000000476837159,
                "SurvivorBase": 1.0,
                "highstr": 1.399999976158142,
                "mediumstr": 1.2999999523162842,
                "lowstr": 1.2000000476837159
            },
            "PainToPlayerArmsInBlockMultiplier": {
                "all": 0.6000000238418579,
                "SurvivorBase": 0.5,
                "highstr": 0.699999988079071,
                "mediumstr": 0.6499999761581421,
                "lowstr": 0.6000000238418579
            },
            "PainToPlayerArmsDisarmMultiplier": {
                "all": 0.30000001192092898,
                "SurvivorBase": 0.30000001192092898,
                "highstr": 0.5,
                "mediumstr": 0.4000000059604645,
                "lowstr": 0.30000001192092898
            },
            "PainToPlayerArmsInBlockDisarmMultiplier": {
                "all": 0.15000000596046449,
                "SurvivorBase": 0.15000000596046449,
                "highstr": 0.25,
                "mediumstr": 0.20000000298023225,
                "lowstr": 0.15000000596046449
            },
            "PainToPlayerLegsMultiplier": {
                "all": 1.2000000476837159,
                "SurvivorBase": 1.0,
                "highstr": 1.399999976158142,
                "mediumstr": 1.2999999523162842,
                "lowstr": 1.2000000476837159
            },
            "PainToPlayerLegsInBlockMultiplier": {
                "all": 0.6000000238418579,
                "SurvivorBase": 0.5,
                "highstr": 0.699999988079071,
                "mediumstr": 0.6499999761581421,
                "lowstr": 0.6000000238418579
            },
            "PainToPlayerTorsoMultiplier": {
                "all": 1.2000000476837159,
                "SurvivorBase": 1.0,
                "highstr": 1.399999976158142,
                "mediumstr": 1.2999999523162842,
                "lowstr": 1.2000000476837159
            },
            "PainToPlayerTorsoInBlockMultiplier": {
                "all": 0.6000000238418579,
                "SurvivorBase": 0.5,
                "highstr": 0.699999988079071,
                "mediumstr": 0.6499999761581421,
                "lowstr": 0.6000000238418579
            },
            "PainToPlayerLimbsBreakChancesMultiplier": {
                "all": 1.0
            },
            "PainToPlayerLimbsDeepWoundChancesMultiplier": {
                "all": 1.0
            },
            "DamageToZombieHandlerIsActive": {
                "all": 1
            },
            "DamageToZombieHealthPoints": {
                "all": -1.0
            },
            "DamageToZombieHealthPointsLeg": {
                "all": -1.0
            },
            "DamageToZombieHeadMeleeMultiplier": {
                "mediumdef": 0.30000001192092898,
                "all": 0.4000000059604645,
                "lowdef": 0.4000000059604645,
                "highdef": 0.20000000298023225
            },
            "DamageToZombieHeadRangeMultiplier": {
                "all": 1.0
            },
            "DamageToZombieBodyMeleeMultiplier": {
                "mediumdef": 0.30000001192092898,
                "all": 0.4000000059604645,
                "lowdef": 0.4000000059604645,
                "highdef": 0.20000000298023225
            },
            "DamageToZombieBodyRangeMultiplier": {
                "mediumdef": 0.30000001192092898,
                "all": 0.4000000059604645,
                "lowdef": 0.4000000059604645,
                "highdef": 0.20000000298023225
            },
            "DamageToZombieFromCarsMultiplier": {
                "mediumdef": 0.30000001192092898,
                "all": 0.4000000059604645,
                "lowdef": 0.4000000059604645,
                "highdef": 0.20000000298023225
            },
            "DamageToZombieFromExplosionsMultiplier": {
                "mediumdef": 0.30000001192092898,
                "all": 0.4000000059604645,
                "lowdef": 0.4000000059604645,
                "highdef": 0.20000000298023225
            },
            "DamageToZombieFromHotItemsHp": {
                "all": 10.0
            },
            "DamageToZombieBodyPartsPiercingIsActive": {
                "all": 1
            },
            "DamageToZombieAlwaysKillOnBackstab": {
                "all": 1
            },
            "DamageToZombieShockToStunHandlerIsActive": {
                "all": 1
            },
            "DamageToZombieShockToStunLightHeavyAnimationThresholdMeleeHeavy": {
                "all": 0.0
            },
            "DamageToZombieShockToStunLightHeavyAnimationThresholdRange": {
                "all": 70.0
            },
            "DamageToZombieShockToStunThresholdMeleeHeavy": {
                "all": 0.0
            },
            "DamageToZombieShockToStunThresholdRange": {
                "all": 0.0
            },
            "DamageToZombieShockToStunFromButtstockHit": {
                "all": 2.0
            },
            "DamageToZombieShockToStunCumulativeDamage": {
                "all": 1
            },
            "DamageToZombieWeaponsMultipliers": {
                "all": {
                    "all": 1.0
                }
            },
            "MeleeAttacksDodgeHandlerIsActive": {
                "all": 1
            },
            "MeleeAttacksDodgeChance": {
                "all": 50.0
            },
            "MeleeAttacksDodgeCooldownSeconds": {
                "all": 10.0
            },
            "JumpAttackHandlerIsActive": {
                "all": 1
            },
            "JumpAttackChance": {
                "all": 10.0
            },
            "JumpAttackCooldownSeconds": {
                "all": 60.0
            },
            "BloodHandlerIsActive": {
                "all": 1
            },
            "BloodVolumeMl": {
                "all": 0.0,
                "Horse_Base": 30000.0,
                "Animal_BosTaurus": 30000.0,
                "Animal_BosTaurusF": 30000.0
            },
            "BloodLossRateMinMl": {
                "all": 5.0
            },
            "BloodLossRateMaxMl": {
                "all": 60.0
            },
            "BloodLossRateRegenMl": {
                "all": 0.20000000298023225
            },
            "BloodOnExplosiveDamageChancePercent": {
                "all": 50.0
            },
            "BloodSplatParticlesIsActive": {
                "all": 1
            },
            "BloodTrailParticlesIsActive": {
                "all": 1
            },
            "BloodPoolParticlesIsActive": {
                "all": 1
            },
            "ResistContaminatedEffectHandlerIsActive": {
                "all": 1
            },
            "ResistContaminatedEffect": {
                "all": 0,
                "ZmbM_NBC_Grey": 1,
                "SurvivorBase": 0,
                "ZmbM_Mummy": 1,
                "ZmbM_NBC_Yellow": 1
            },
            "AllowCrawling": {
                "all": 1
            },
            "RespawnInCrawlingChancePercent": {
                "all": 0.0
            },
            "ScreamHandlerIsActive": {
                "all": 1
            },
            "ScreamAttractsZombiesInRadius": {
                "all": 50.0,
                "ZmbM_usSoldier_Officer_Desert": 120.0
            },
            "ScreamChancePercent": {
                "all": 25.0,
                "ZmbM_usSoldier_Officer_Desert": 100.0
            },
            "ScreamCooldownSeconds": {
                "all": 60.0
            },
            "ScreamNearbyInfectedSilenceSeconds": {
                "all": 60.0
            },
            "SearchBodyToViewCargo": {
                "all": 1
            },
            "SearchBodyToViewCargoSeconds": {
                "all": 3.0
            },
            "SearchBodyExtendLootingToPlayersInRadiusMeters": {
                "all": 30.0
            },
            "SearchBodyOnlyEmptyHands": {
                "all": 0
            },
            "SearchBodyWithoutGlovesBloodyHandsChancePercent": {
                "all": 50.0
            },
            "SearchBodyWithoutMaskVomitChancePercent": {
                "all": 10.0
            },
            "CanBeButchered": {
                "all": 1
            },
            "ButcheringSeconds": {
                "all": 20.0
            },
            "ButcheringWithoutGlovesBloodyHandsChancePercent": {
                "all": 100.0
            },
            "ButcheringWithoutMaskVomitChancePercent": {
                "all": 50.0
            },
            "ItemsAfterButchering": {
                "all": [
                    {
                        "ClassId": "Bone",
                        "DropChancePercent": 100.0,
                        "QuantityInStackFromPercent": 16.0,
                        "QuantityInStackToPercent": 84.0,
                        "ConditionFrom": 2,
                        "ConditionTo": 3,
                        "Foodstages": []
                    },
                    {
                        "ClassId": "Rag",
                        "DropChancePercent": 100.0,
                        "QuantityInStackFromPercent": 9.0,
                        "QuantityInStackToPercent": 74.0,
                        "ConditionFrom": 2,
                        "ConditionTo": 3,
                        "Foodstages": []
                    },
                    {
                        "ClassId": "Guts",
                        "DropChancePercent": 100.0,
                        "QuantityInStackFromPercent": 30.0,
                        "QuantityInStackToPercent": 100.0,
                        "ConditionFrom": 2,
                        "ConditionTo": 3,
                        "Foodstages": []
                    },
                    {
                        "ClassId": "Guts",
                        "DropChancePercent": 50.0,
                        "QuantityInStackFromPercent": 30.0,
                        "QuantityInStackToPercent": 100.0,
                        "ConditionFrom": 2,
                        "ConditionTo": 3,
                        "Foodstages": []
                    },
                    {
                        "ClassId": "HumanSteakMeat",
                        "DropChancePercent": 100.0,
                        "QuantityInStackFromPercent": 30.0,
                        "QuantityInStackToPercent": 100.0,
                        "ConditionFrom": 2,
                        "ConditionTo": 3,
                        "Foodstages": [
                            6
                        ]
                    },
                    {
                        "ClassId": "HumanSteakMeat",
                        "DropChancePercent": 50.0,
                        "QuantityInStackFromPercent": 30.0,
                        "QuantityInStackToPercent": 100.0,
                        "ConditionFrom": 2,
                        "ConditionTo": 3,
                        "Foodstages": [
                            6
                        ]
                    }
                ]
            },
            "CanBeBackstabbedHandlerIsActive": {
                "all": 0
            },
            "CanBeBackstabbed": {
                "all": 1
            },
            "VisionRangeMultiplierDay": {
                "all": 2.0
            },
            "VisionRangeMultiplierNight": {
                "all": 0.800000011920929
            },
            "SizeHandlerIsActive": {
                "all": 0
            },
            "SizeFromMultiplier": {
                "all": 0.8999999761581421
            },
            "SizeToMultiplier": {
                "all": 1.100000023841858
            },
            "SizeDamageScalingIsActive": {
                "all": 0
            },
            "SizeBloodVolumeScalingIsActive": {
                "all": 1
            },
            "SizeSpeedMultiplierScalingIsActive": {
                "all": 1
            },
            "ThrowingProjectilesHandlerIsActive": {
                "all": 1
            },
            "ThrowingProjectilesHandlerDamageMultiplier": {
                "all": 0.8999999761581421,
                "SurvivorBase": 1.100000023841858,
                "highstr": 1.100000023841858,
                "mediumstr": 1.0,
                "lowstr": 0.8999999761581421
            },
            "ThrowingProjectilesHandlerVehiclesDamageMultiplier": {
                "all": 1.7999999523162842,
                "SurvivorBase": 2.200000047683716,
                "highstr": 2.200000047683716,
                "mediumstr": 2.0,
                "lowstr": 1.7999999523162842
            },
            "ThrowingProjectilesHandlerProjectilesList": {
                "police": [
                    "GarbageIfPlayerOnObstacle",
                    "PoliceProjectile"
                ],
                "all": [],
                "priests": [
                    "GarbageIfPlayerOnObstacle",
                    "GarbageIfPlayerNonObstacle"
                ],
                "industrial": [
                    "GarbageIfPlayerOnObstacle",
                    "IndustrialProjectile"
                ],
                "villagers": [
                    "GarbageIfPlayerOnObstacle",
                    "VillagersProjectile"
                ],
                "city": [
                    "GarbageIfPlayerOnObstacle",
                    "CityProjectile"
                ],
                "firefighters": [
                    "GarbageIfPlayerOnObstacle",
                    "FirefightersProjectile"
                ],
                "medics": [
                    "GarbageIfPlayerOnObstacle",
                    "MedicsProjectile"
                ],
                "fishermen": [
                    "GarbageIfPlayerOnObstacle",
                    "FishermenProjectile"
                ],
                "hunters": [
                    "GarbageIfPlayerOnObstacle",
                    "HuntersProjectile"
                ],
                "military": [
                    "GarbageIfPlayerOnObstacle",
                    "MilitaryProjectile"
                ],
                "prisoners": [
                    "GarbageIfPlayerOnObstacle",
                    "GarbageIfPlayerNonObstacle"
                ]
            },
            "RangeAttacksHandlerIsActive": {
                "all": 0
            },
            "RangeAttacksHandlerZombiePlayerDistance": {
                "all": 2.0
            },
            "RangeAttacksHandlerPlayerOnObstacleHeight": {
                "all": 0.5
            }
        },
        "Players": {
            "SmellsHandlerIsActive": 1,
            "SmellLifetimeSeconds": 120.0,
            "SmellsCountOnMapLimit": 1000,
            "FootstepsNoiseHandlerIsActive": 1,
            "SearchBodyToViewCargo": 1,
            "SearchBodyToViewCargoSeconds": 3.0,
            "SearchBodyExtendLootingToPlayersInRadiusMeters": 30.0,
            "SearchBodyOnlyEmptyHands": 0,
            "QuietDoorOpeningMechanicIsActive": 1,
            "QuietDoorOpeningMechanicDisabledForOpening": 1,
            "QuietDoorOpeningMechanicSeconds": 3.0,
            "QuietDoorOpeningMechanicRestrictedBuildings": [
                "DNA_Strongroom_ColourBase",
                "DNA_Strongroom_Open_Base",
                "DNA_Lockout_ColourBase",
                "DNA_Lockout_OneWayDoor",
                "DNA_Door_NoLock_ColourBase",
                "DNA_WarpDoor_NoLock",
                "DNA_Lockout_Dbl_ColourBase",
                "DNA_Door_NoLock_Dbl_ColourBase",
                "DNA_LockoutSteel_ColourBase",
                "Land_KlimaX_T1Door",
                "Land_KlimaX_T2Door",
                "Land_KlimaX_T3Door",
                "EVG_KeycardDoor",
                "land_bunker_door_base",
                "land_bunker_entrance",
                "land_bunker_entrance1",
                "land_bunker_entrance2",
                "land_bunker_door_area04",
                "Land_WarheadStorage_Main",
                "Jmc_Security_Door",
                "Jmc_Security_Door_Carrier"
            ],
            "DisableVanillaDoorNoiseSystem": 1,
            "OverrideGetHitComponentChances": 1,
            "PainSystemIsActive": 1,
            "PainSystemNotificationsType": 2.0,
            "ShowPainBadges": 1,
            "ShowPainBlur": 1,
            "ShowMedicationInfo": 1,
            "PainHealingRatePerSecondPercent": 0.10000000149011612,
            "HealthDrainWithOverPainedLimbPerSecondPercent": 0.10000000149011612,
            "VehicleCrashPainMultiplier": 1.0,
            "VehicleCollisionsPainMultiplier": 1.0,
            "FallPainMultiplier": 1.0,
            "ExplosionsPainMultiplier": 1.0,
            "UnconsciousWhenOverPainedHeadReceivingHits": 1,
            "CrouchWhenOverPainedTorsoReceivingHits": 1,
            "ArmsLowerWhenAimingWithPainedArms": 1,
            "ArmsLowerWhenOverPainedArmsReceivingHits": 1,
            "ArmsPainShockDamageActions": {
                "all": 2.0,
                "ActionMineRock": 4.0,
                "ActionPushCar": 4.0,
                "ActionForceConsume": 0.0,
                "ActionConsume": 0.0,
                "ActionForceConsumeSingle": 0.0,
                "ActionDisinfectTarget": 0.0,
                "ActionDisinfectSelf": 0.0,
                "ActionInjectTarget": 0.0,
                "ActionInjectSelf": 0.0,
                "ActionConsumeSingle": 0.0,
                "ActionUnrestrainSelf": 1.0,
                "ActionMineTree": 4.0
            },
            "ArmsPainUnrestrainItems": {
                "MetalWireLocked": 4.0,
                "all": 2.0,
                "BarbedWireLocked": 3.0,
                "HandcuffsLocked": 8.0
            },
            "AuditoryHallucinationsWithPainedHead": 1,
            "VomitWithPainedHead": 1,
            "TinnitusWhenHeadReceivingHits": 1,
            "BlurWhenHeadReceivingHits": 1,
            "SoundAttenuationWhenHeadReceivingHits": 1,
            "MovementCoordinationImpairmentWhenHeadReceivingHits": 1,
            "PainArmsWhenHitWithoutGloves": 1,
            "ShockIfRunsWithPainedLegs": 1,
            "ShockIfAttackingWithPainedArms": 1,
            "LimbsBreakSystemIsActive": 1,
            "LimbsBreakPainThresholdPercent": 30.0,
            "HeadBreakDurationSeconds": 1800.0,
            "ArmsBreakDurationSeconds": 1800.0,
            "LegsBreakDurationSeconds": 1800.0,
            "TorsoBreakDurationSeconds": 1800.0,
            "LimbsBreakFromFalls": 1,
            "LegsBreakFromTraps": 1,
            "UnconsciousWhenHeadBreak": 1,
            "LimbsDeepWoundSystemIsActive": 1,
            "HeadDeepWoundDurationSeconds": 1800.0,
            "ArmsDeepWoundDurationSeconds": 1800.0,
            "LegsDeepWoundDurationSeconds": 1800.0,
            "TorsoDeepWoundDurationSeconds": 1800.0,
            "LimbsDeepWoundVanillaCutBleedRateMultiplier": 0.10000000149011612,
            "LimbsDeepWoundFromFalls": 1,
            "LegsDeepWoundFromTraps": 1,
            "LimbsBulletSystemIsActive": 1,
            "LimbsBulletTimeToSecondStageSeconds": 3600.0,
            "InternalBleedingSystemIsActive": 1,
            "InternalBleedingBloodLossRateMl": 2.0,
            "DestroyedDoorNotificationType": 2.0,
            "NoiseMultiplierDay": 2.0,
            "NoiseMultiplierNight": 2.0,
            "NoiseMultiplierCrouchDay": 1.0,
            "NoiseMultiplierCrouchNight": 1.0,
            "NoiseMultiplierLadderDay": 0.20000000298023225,
            "NoiseMultiplierLadderNight": 0.20000000298023225,
            "CamoClothingVisibilityMultipliers": {
                "GhillieSuit_ColorBase": 0.800000011920929,
                "all": 1.0,
                "GhillieTop_ColorBase": 0.800000011920929,
                "GhillieHood_ColorBase": 0.800000011920929
            }
        },
        "Vehicles": {
            "Noise": {
                "all": {
                    "RpmMaxMeters": 120.0,
                    "RpmIdleMeters": 40.0
                },
                "Offroad_02": {
                    "RpmMaxMeters": 140.0,
                    "RpmIdleMeters": 50.0
                },
                "Truck_01_Base": {
                    "RpmMaxMeters": 150.0,
                    "RpmIdleMeters": 60.0
                },
                "Bicycle_Base": {
                    "RpmMaxMeters": 40.0,
                    "RpmIdleMeters": 20.0
                }
            },
            "CollisionsSoundThreshold": {
                "all": 30.0
            },
            "CollisionsSpeedReductionMultiplier": {
                "all": 1.0
            },
            "CollisionsDamageSpeedThresholdKmH": {
                "all": 10.0,
                "Bicycle_Base": 0.0
            }
        },
        "LossInterestToIrritantAfterSeconds": 120.0,
        "LightInHouseMultiplier": 0.20000000298023225,
        "SoundInHouseMultiplier": 0.5,
        "BloodParticlesLimit": 1000.0,
        "BloodParticleDurationSeconds": 600.0,
        "SaveConfigAfterInit": 0
    }