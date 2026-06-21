Builders are in ".xlsx" format and placed in the "data/build-orders" folder. The name of the file will be used as the name of the build-order. Each tab is described below. All strategies are loaded and the script figures out which are compatible with the current map-style, map sub-type, position, and civ. Then out of all allowed strategies, the final strategy is selected at random.

### 'build-order' tab
---
- This specifies which units/techs/buildings (collectively called items) are desired for the build-order.
- Each row contains a single item and additional info to control how many of them and when to get it
    - **limit** is the total number of items to get, or *-1* for no limit.
    - **eco-level** specifies the minimum economy level before we may get the item. This is roughly equal to the number of villagers (but may be increased in certain cituations).
    - **age-status** is the minimum age-status required before getting the item: 0=dark, 100=feudal, 200=castle, and 300=imperial. It increases gradually during age-up.
    - **deps** sets a minmum number of other items that are required before getting this item. The syntax is '&lt;min-count&gt; &lt;item-dependency&gt;, ...' but &lt;min-count&gt; can be excluded for a count of 1.
    - **options** is used to set verious options that control how we get the item (see below).

**Additional Info**
- All items are in lower case, with spaces changed to '-'.
- Unit items/deps must *always* be the base unit name, not an upgraded-unit or unit-line.
- Research items are prefixed with 'ri-' followed by the research name.
- You must use either gold-mining-camp or stone-mining-camp for mining-camps. 
- You cannot use civ-specific dropsites like mule-cart, folwark, or settlement. Just use regular dropsite names and the appropriate dropsite will be built.
- deps of units can alternatively be classes (such as class-infantry), or villager sets (such as villager-food). In this case the count always refers to the total number currently on the map.

**Item counts for *limit*/*deps***
- For military units (except siege) it refers to the max count that existed throughout the game. E.g. if you set a limit of 5 militia which then are trained and killed in combat, no further militia will be trained.
- For all other units it is the current count (including all upgrades /varients).
- For dropsites, it includes all the various dropsits that may be used to gather the resource (and only if that resource exists nearby). 
- For mill, it only includes those with hunt/berries/fish nearby (not farms!).
- For techs it should be 1 (it can't detect if the same tech is researched multiple times).

**The following *options* are available**
- **<num> drop-res**: drop resourses to get the first <num> items more quickly.
- **<num> buy-res**: buy resourses to get the first <num> items more quickly.
- **cancel-queue**: cancel the relevant building queue to get a research more quickly.
- **<num> vill-f/w/s/g**: specify <num> villagers of a particular type should build a building item.
- **build-forward**: building item should be built in a forward position.
- **wall-team**: specify that a team wall should be built (only for palisade-wall or stone-wall).
- **wall-player**: specify that a player wall should be built (only for palisade-wall or stone-wall).
- **check-available**: checks that the tech tree-requirements are met before reserving resources for the item.

**Unit Selection**
- You cannot train unique-units directly. Instead you must use my-unique-unit. To train unique-ships, use my-unique-ship.
- You cannot train certain civ-specific units directly; instead you must use another unit as a replacement. Most of the replacement units come from the same building
    - archer (cavalry-archer)
    - hand-cannoneer (slinger, grenadier, xianbei-raider)
    - war-wagon (elephant-archer)
    - skirmisher (genitour)
    - eagle-scout (condottiero, champi-scout, flemish-militia-trained, fire-lancer)
    - huskarl (jian-swordsman-healthy)
    - knight (xolotl-warrior, shrivamsha-rider, hei-guang-cavalry)
    - mangonel (mounted-trebuchet)
    - scorpion (war-chariot-focus-fire, rocket-cart)
- there are also a few unusual ones that come from a different building
    - war-elephant (steppe-lancer)
    - eagle-scout (warrior-priest, missionary)
- regarding cavalry-archer (and genitor when available), the AI will pick this replacement if it's better for the civ, insetead of archer (or skirmisher)

**Further details**
- You can start a wall with just a single wall piece and the rest will be slowly be built automatically. Other buildings, besides walls, may also be included in the wall.
- *build-forward* for town-center will try to build it in range of the enemy town-center. You can add the option *delete* to delete the starting town-center.
- *build-forward* on island-style maps will try to build on the enemy island. Villagers will be transported automatically.

**Automatic items**
- villager and fishing-ship will be traied automatically when not included.
- transport-ship will be trained automatically on island-style/baltic-style/migration-style maps when units try to move to other islands and no transport ship is available.
- Houses will be build automatically and dont need to be provided at all.
- Military buildings will be built automatically when not included, but additional buildings will be very delayed.
- Building dependencies will be built automatically when not provided.
- Farms will be built automatically when running low on food sources, but very delayed..
- Relevant researches / upgrades will always be completed but delayed if not provided

**Comments about delays**
- Most automatic delays are present for low villager-count / before castle age. 
- After around 40 vills (or less in castle-age) these delays are absent, as there's less risk in getting un unnecessary item.

**Automatic options**
- The first 2 buildings of each type will always be dropped for.
- Critical villagers / fishing-ships / houses will always be dropped for.
- Will always buy town-centers / castles in emergency.
- Will automatically build forward military buildings on island-style maps in some situations.

### 'vill-numbers' tab
---
This is used to control the villager distribution. The villager distribution is specified at a set of points and linearly interpolated between the points.
- *V* is the total number of villagers
- *A* is the age status (see description above)
- *F,W,S,G* are the number of villagers allocated to food, wood, stone and gold
- *U* is the number of unallocated villagers.

**Additional comments**
- The age-status is used to change villager distributions during age-up. Most commonly F->W for fast-feudal build-orders.
- Unallocated villagers will be allocated automatically by the EcoBalance 'model'. The model calculates villager requirements based on number of town-centers, and desired army composition. There are 2 ways in which this is typically used.
    1. Setting a small number of unallocated for unique-unit build-orders which may include units with differnt costs. Then the vill numbers will be allocated based on the cost of the units.
    2. Setting all villagers as unallocated. This simplifies the process of constructing the table in cases where the model is already accurate (typically after castle age or 40+ vills).
- There is no way to allocate builders or explorers. This is done automatically.
- There is a limit of up to 30 build-order rows.
- Vill-numbers may be adapted for civs and maps when not fully supported by the build-order.
- Vill-numbers may be adapted by the control-system to avoid floating resources.

### 'positions' tab
This sets the allowed positions for the build-order. These should be either 0 for not-allowed, or 1 for allowed.
- *1v1* allowed in 1v1 games.
- *flank* allowed in flank position in team games.
- *pocket* allowed in pocket position in team games.
- *deep-pocket* allowed in deep-pocket position in team games (where there is at least 5 players on the AI's team).

### 'civs' tab
---
- Here you specifiy what civs are compatible with your build-order. Each civ is listed on the first column. Use '1' for compatible, or '0' for not compatible.
- If your build-order is compatible with more than 1 civ then adaptations will be turned on. This means that minor changes will be made to the build-order and vill-numbers for civ compatibility.
- The Indian civ is only available for Wololo Kingdoms. The hindustanis civ is only available for Definitive Edition. 

### 'maps' tab
---
On this tab you specify what map-styles / map-sub-types you build-order is compatible, 0 = not-compatible; 1 = compatible; or leave blank for potentially compatible.
- First you must specify the map-styles. Usually it should be compatible with just 1 of these. There are 5 map style which depend on the distribution of land and water. Each map gets put into one of these styles.
    - style-arabia: the players are connected only by land. May still include small ponds.
	- style-baltic: the players are connected by land and water; includes maps like rivers and scandinavia; ship warfare is likely but may also attack with land units.
    - style-islands: players fully separated by water; require ships/transport-ships.
    - style-migration: players start on basic island but need to migrate to big island later (doesn't include instant migration start). The map-style changes to style-baltic after migration completed.
    - style-bog-islands: players connected by shallows; allows both ships and land units.
    - style-random: used for mega-random-like maps with unknown land/water; map change to a different style as the map is explored.
- next you should specify which map sub-types your build-order is compatible with. It's possible for a map to have any number of sub-types.
    - map-multipleTCs: starts with multiple town-centers (might have multiple towns too).
    - map-startingWalls: starts with full walls.
    - map-nomadStart: start without a town-center.
    - map-resCentral: important resources in middle.
    - map-resOuter: important resources on outside.
    - map-waterPrivate: map has likely private ponds.
    - map-waterPublic: map has likely public ponds.
    - map-landToAlly: has a direct land path to the ally.
    - map-landToEnemy: has a direct land path to the enemy.
    - map-closeEnemy: players start close together.
    - map-migrationStart: require immidiate migration with transport ship.
    - map-wallable: how wallable is the map; 0=easy, 1=medium, 2=hard.

**Adaptations**
If your AI plays on a map-style that it is not supposed to be compatible with, then adaptations may be applied automatically. In particular AIs built for style-arabia that play on style-islands / style-baltic / style-migration will be adapted to include fishing-ships, and transport ships will be made to transport the land units. It is not possible for water maps to be adapted for style-arabia

### 'options' tab
---
This includes addtional options not found in the other tabs. They can be set to a single value, or one value for each age (fomat x,x,x,x)
- **land-unit-percent**: baseline percent of land units (vs water units). Though this may be changed situations.
- **allow defensive spearmen**: allow defensive spearmen for defending scout-rush.
- **allow defensive monks**: allow defensive monks for defending knight-rush.
- **allow defensive siege**: allow defensive siege for defending archer-rush.
- **counter-unit-factor**: determines how many counter units the AI will make; 0=few to 100=many.
- **agressivness-factor**: determines how likely attack will be triggered; 0=passive to 100=aggressive.
- **micro-level**: controls the strength of the military micro: 5=super-human, 4=expert-level, 3, 2, 1 gets progressively weaker.
- **economy-speed**: used to slow down training time to decrease difficulty.
- **population-percent**: used to reduce avaliable pop-cap to resuce difficulty.
