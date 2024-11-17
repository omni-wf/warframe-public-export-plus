# warframe-public-export-plus

The most complete data source for all your Warframe needs and interests. Contains everything missing in Public Export and more.

## Localisations

Data and localisations are entirely split here (into Export\*.json and dict.\*.json, respectively). This should make it trivial to handle localisations in your projects without tons of duplicated data. Unfortunately, this may make it difficult to manually browse the data; however, you can type whatever you're looking for into [omni.wf](https://omni.wf/), which is uses this data and [is open-source](https://github.com/calamity-inc/omni.wf).

## Images

Most exports here have an `icon` field, which contains a path, e.g. `/Lotus/Interface/Icons/Player/LotusSymbol.png`. There are a few ways to obtain an image from such a path:
- [Puxtril's Warframe Exporter](https://github.com/Puxtril/Warframe-Exporter) can be used entirely offline to export textures from your game files.
- browse.wf hosts all images and can be queried like this: <https://browse.wf/Lotus/Interface/Icons/Player/LotusSymbol.png>
- ExportImages can be used to find out if an image is hosted on `content.warframe.com/PublicExport`, in which case it can be obtained using by adding an exclamation mark followed by the `contentHash`, like so: <https://content.warframe.com/PublicExport/Lotus/Interface/Icons/Player/LotusSymbol.png!00_WC8orfy4NOtWelndlH7qmQ>

## Notes

### ExportRegions
- Crossfire missions can be detected by the `secondaryFactionIndex` field being present. The `/Lotus/Language/Missions/MissionName_Crossfire` label may be used for their mission type.
- Tyana Pass (`SolNode450`) is a bit special in that it uses the `/Lotus/Language/Missions/DualDefenseCompare` label for the faction.

### ExportRelics
- There is no `name` field, instead the added `category` and `era` fields can be used in conjuction with `/Lotus/Language/Relics/VoidProjectionName` to construct the name.

### ExportRewards
- There are some special tables where rewards have a `rarity` instead of a `probability`. These cases are void relics and archon hunt shard rewards. In the former case, the probabilities depend on the [relic refinement](supplementals/relic-chances.pluto).

### ExportUpgrades
- Several mods share the same name, e.g. for "Vitality" and "Pressure Point" there's 3 mods each. Some of these might be [flawed variants](https://warframe.fandom.com/wiki/Flawed_Mods), but others might simply be forgotten development artefacts. These can be avoided by checking that `isStarter` and `isFrivilous` are both absent.
- Challenge complications are combined using `/Lotus/Language/Challenges/Challenge_Complication_Combiner`.

### ExportWarframes
- The `health`, `shield`, `armor`, and `power` values represent the state at rank 0. [See here for an approach to level-scaling these stats.](https://github.com/Sainan/warframe-build-evaluator/blob/d05257f704e688ec387c697c6768b951cf3d5389/evaluator.pluto#L438-L500)

### ExportWeapons
- Non-weapon items such as modular parts are in here as well. These can be filtered by checking if `behaviors` is absent.
- Kitgun Chambers also have a `primeOmegaAttenuation` \[sic\] field, this is the Riven Disposition for when the Kitgun is a primary instead of secondary weapon.
- The `damagePerShot` array is documented [here](https://warframe.fandom.com/wiki/Public_Export#Guns), although the `behaviors` array should be preferred.
