## HC Dungeon’s in Normal Greece monsters always dropping Titanic Energy potions:
database\records\xpack4\creatures\monster\chaos monster\greece

LootMisc1item1
Records\xpack\item\loottables\misc\potion_mana_l01.dbr;records\XPack4\Item\LootTables\HCDungeon\x4_DungeonLoot_Potion_Fodder_Greek_E_01.dbr;records\XPack4\Item\LootTables\HCDungeon\x4_DungeonLoot_Potion_Fodder_Greek_L_01.dbr

Solution: change reference
records\xpack4\item\loottables\hcdungeon\x4_dungeonloot_potion_fodder_greek_n_01.dbr;records\XPack4\Item\LootTables\HCDungeon\x4_DungeonLoot_Potion_Fodder_Greek_E_01.dbr;records\XPack4\Item\LootTables\HCDungeon\x4_DungeonLoot_Potion_Fodder_Greek_L_01.dbr

## HC Dungeon - Normal Greece dropping Legendary tier items on end/half way chest
records\game\xpack4\item\containers\loot tables\HCDungeon\x4_HCDung_Greek_N_End_ContainerLoot.dbr
records\game\xpack4\item\containers\loot tables\HCDungeon\x4_hcdung_greek_n_half_containerloot.dbr


All instances of legendary tables: records\XPack4\Item\LootTables\Electrum_Xpack0\Amulet\Amulet_Master_Dynamic_3L_1.dbr
Changed to N_ variant table (can be changed to E_ if you want)
[N] Lupine claw and [E] Djed of Osiris cannot be enchanted on Thrown Weapons
records\item\animalrelics\01_act2_lupineclaw.dbr
Records\item\relics\02_act2_djedofosiris.dbr

rangedOneHand,1, missing from .dbr contents
Add manually, or change inside AM from 1 > 0 > 1 for it to be automatically written to


## Hydra can’t drop Unique arms from it’s loot table
records\item\containers\DefaultLoot\Hydra_Default_55-57.dbr

loot5Name3
Records\Item\LootTables\Arms\MasterTables\Uniques\ArmAll_L01.dbr

Broken reference, typo should be ..\Unique\ArmAll_l01.dbr

## Bonecaster shawl not dropping

Records\xpack2\creatures\monster\troll\as_bonecaster_40 to 44
Records\xpack2\creatures\monster\troll\bs_bonecaster_43 to 47
Records\xpack2\creatures\monster\troll\x2hero_bonecaster_44.dbr

Every instance of:
LootTorsoItem4,records\xpack2\item\loottables\torso\monster\ni_troll.dbr -> Records\xpack2\item\loottables\torso\monster\ni_trollmage.dbr

## Bear Rider Leggings (L) not dropping 
\records\xpack2\creatures\monster\yerren

Every instance of: 
Records\xpack2\item\loottables\legs\monster\il_yerren.dbr -> records\xpack2\item\loottables\legs\monster\li_yerren.dbr 


## Triton launcher not dropping from Triton’s (merfolk)
Records\xpack3\creatures\monster\merfolk\ar_archer_33 ~ 37.dbr
Records\xpack3\creatures\monster\merfolk\br_archer_37 ~ 41.dbr

Previously, archer merfolk were completely missing their monster bow loot table, as well as their MI bow loot table, both added:

LootLeftHanditem2,records\xpack3\items\loottables\weapons\monster\bow\m_n_tritonwarrior.dbr;records\xpack3\items\loottables\weapons\monster\bow\m_e_tritonwarrior.dbr;records\xpack3\items\loottables\weapons\monster\bow\m_l_tritonwarrior.dbr,

LootLeftHandItem3,records\xpack3\items\loottables\weapons\monster\bow\mi_n_tritonwarrior.dbr;records\xpack3\items\loottables\weapons\monster\bow\mi_e_tritonwarrior.dbr;records\xpack3\items\loottables\weapons\monster\bow\mi_l_tritonwarrior.dbr
(chancetoEquipLootLeftHandItem3,25,)


## Hydromancer staff’s not dropping from Potamoi

Potatomoi mastertables for staves, (both monster and MI), e.g.
records\xpack3\items\loottables\weapons\mastertables\...
static_staff_potamoiwarrior_e.dbr
static_staff_potamoiwarrior_ei.dbr
static_staff_potamoiwarrior_l.dbr
static_staff_potamoiwarrior_li.dbr
static_staff_potamoiwarrior_n.dbr
static_staff_potamoiwarrior_ni.dbr

Inside contain typo’d references, meaning it links to no item on the loottable e.g.
records\xpack3\items\loottables\weapons\monster\staff\mi_l_PotamoiWarrior_fire.dbr
records\xpack3\items\loottables\weapons\monster\staff\mi_l_PotamoiWarrior_frost.dbr
records\xpack3\items\loottables\weapons\monster\staff\mi_l_PotamoiWarrior_lightning.dbr

Ammended to records\xpack3\items\loottables\weapons\monster\staff\mi_l_PotamoiMage_lightning.dbr, etc..

(yes, the master table labelled as warrior makes no sense, but no point in changing it’s just a name and will require more backend of changing all references towards it in creatures).

## All Potamoi mages equipping legendary monster cold staves even on Non Legendary
records\xpack3\creatures\monster\potamoi

Any dbr referencing “mage” e.g. 
records\xpack3\creatures\monster\potamoi\as_potamoi_mage_37.dbr
records\xpack3\creatures\monster\potamoi\as_potamoi_mage_ambush_37.dbr
Records\xpack3\creatures\monster\potamoi\bs_potamoi_mage_38.dbr
And subsequently, named unique monsters that equip staves
records\xpack3\creatures\monster\potamoi\x3hero_pliplup_39.dbr
records\xpack3\creatures\monster\potamoi\x3sq11_leadera_39.dbr

Use LootLeftHandItem2,records\xpack3\items\loottables\weapons\monster\staff\m_l_potamoimage_frost.dbr;records\xpack3\items\loottables\weapons\monster\staff\m_l_potamoimage_frost.dbr;records\xpack3\items\loottables\weapons\monster\staff\m_l_potamoimage_frost.dbr

Which means when they equip Item2 (their monster item), they always get a legendary quality cold staff. Changed to use their regular monster mastertable, which we fixed above, the _n, _e, _l variant that already exists besides their MI one. 

E.g.

LootLeftHandItem2, records\xpack3\items\loottables\weapons\mastertables\static_staff_potamoiwarrior_n.dbr;records\xpack3\items\loottables\weapons\mastertables\static_staff_potamoiwarrior_e.dbr;records\xpack3\items\loottables\weapons\mastertables\static_staff_potamoiwarrior_l.dbr

## Thrall Mage Torso, Thrall Bracers and Three Venom Shield predominately rolling as broken (no affixes)
records\xpack4\item\loottables\arms\monster\china_m_l_tigerman_arms.dbr
records\\xpack4\item\loottables\arms\monster\china_m_l_tigerman_arms_ranged.dbr
records\\xpack4\item\loottables\shields\monster\egypt_m_l_threevenom_shield.dbr
records\\xpack4\item\loottables\torso\monster\china_m_l_tigerman_torso_mage.dbr

Removed brokenOnly weight, set bothPrefixSuffix, prefixOnly SuffixOnly, to conventional 2,9,9 that rest of game MI randomiser uses



## Arachne Queen first Chest doesn’t appear on Epic, because Boarsnatcher uses the same AccessoryPool/Proxy.


Create a separate accessory pool, with the same exact Arachne queen container so they don’t interfere with each other. This can be easily done by just copy and pasting the Accessory pool and just renaming it. Make sure to reference it back in the original Proxy.

E.g. records\item\containers\boss\accessorypools\bosschestpool04_arachne_epic.dbr, _arachne_legendary.dbr, and duplicated it to records\item\containers\boss\accessorypools\bosschestpool04_arachne_epicX.dbr
& _arachne_legendaryX.dbr)

Then referenced it back in: records\proxies boss\le_new\01_tegealakearach.dbr
AccessoryEpic1,records\item\containers\boss\accessorypools\bosschestpool04_arachne_epic.dbr
AccessoryLegendary1,records\item\containers\boss\accessorypools\bosschestpool04_arachne_legendary.dbr


## Troll's splitter now has duration
Item’s stats: chance of bleeding and reduced armor, had Min/Max values assigned, but no duration listed, so they wouldn’t exist in game.
50.0% Chance of 30 ~ 90 Bleeding Damage
50.0% Chance of 180.0 Reduced Armor

Sciron's Thanks, Spear of Thule, Dagger Tooth skills don’t work properly, projectiles travel into the ground
records\xpack2\skills\item skills\proj_iceshard.dbr (manually created for Spear of Thule [records\xpack2\item\equipmentweapons\spear\u_n_03.dbr], has to be then referenced in the item’s dbr)
records\xpack2\skills\item skills\proj_flashbang.dbr (Sciron’s Thanks)
records\xpack3\skills\item skills\proj_daggertooth.dbr (Dagger Tooth)

Skill_attackprojectileburst.tpl is bugged on itemSkillAutoController’s, and has to be changed to Skill_attackprojectileFan.tpl. For Spear of Thule, a new skill had to be created because it’s safer to not change the original storm mastery’s ice shard template.

For Dagger tooth, it’s SkillProjectileName has a typo that links to a nonexisting reference 
Records\XPack3\items\equipmentweapon\1hranged\projectiles\u_l_01s.dbr - > Records\XPack3\items\equipmentweapon\1hranged\projectiles\u_l_01.dbr




## Huge list of EE Set pieces unobtainable/undroppable in game
Full list of obtainable items: https://docs.google.com/document/d/1TQNmCBlcHCzFMQihj8nS8tvXzUXCtCyfAnTnW2_Vib4/edit?tab=t.0#heading=h.wwwspe4k9siy

All added into existing …\records\xpack4\item\loottables\... (which affects both electrum + campaign)
Electrum orbs for xpack4 now uses LootItemTable_FixedWeight.tpl instead of LootItemTable_DynWeight.tpl, because for whatever reason dyn weight made it so even after 1000 orbs opening, I still couldn’t find the items despite it being on the table. 




## Ceremonial, Atenite spear no longer drop, removed in a update by loot table human error

The Atenite spear was moved on the array to the epic index, and thus only drops in Epic, which can’t be found on Eternal Embers, disabling the item from being obtainable. 
Supposedly the two monsters that previously dropped the items based on revision history (but not 100% accurate) were: 
records\xpack4\creatures\monster\skeleton\bm_skeleton_80.dbr 
records\xpack4\creatures\monster\bandits\cm_bandit_egypt_81.dbr

Created a mastertable with both Ceremonial, Atenite spear on it, with equal chances, then assigned it to the legendary index of the monster’s …lootRightHandItem4,-;-;records\xpack4\item\loottables\weapons\mastertables\spearMI.dbr

If you want to go even farther, you can add Ceremonial Axe and Desert Dweller’s club to the master table, so those creatures still keep intact all the items on their array that were maybe “intended” to drop for variety, not doing so though won’t make them unobtainable, records\xpack4\creatures\monster\bandits\cm_bandit_80.dbr still equips ceremonial axe on lootRightHandItem2, and desert dweller club on lootRightHandItem5. 
## Alcyoneus colour updated to be consistent with all other MI

Alycyoneus never got the Lime tag update in Anniversary Edition, like other Monster Rare’s did. Very easy fix, just add {^l} to the name tags. E.g.
xtagUArmor135=Alcyoneus’ Breastplate
-> 
xtagUArmor135={^l}Alcyoneus’ Breastplate

## Electrum Orbs not dropping other respec potions, aside from Str
records\xpack4\item\containers\loot tables\electrumorbs\....
E.g. records\xpack4\item\containers\loot tables\electrumorbs\x4_electrumorb_3_scandia_3l_loot.dbr
Loot3Name1, records\item\HCDungeon\x4pot_PotionOfSkillReset_Str_01.dbr

The only correct orbs to list the Potion mastertable are, Antiquity type
E.g. records\xpack4\item\containers\loot tables\electrumorbs\x4_electrumorb_1_antiquity_3l_loot.dbr
Loot6Name2,records\XPack4\Item\LootTables\Electrum MasterTables\x4_RespecPotion_LootTable_01.dbr

Removed all instances of records\item\HCDungeon\x4pot_PotionOfSkillReset_Str_01.dbr, and replaced with 
records\XPack4\Item\LootTables\Electrum MasterTables\x4_RespecPotion_LootTable_01.dbr



