# warframe-public-export-plus

[Warframe's Public Export](https://github.com/calamity-inc/warframe-public-export) with extra love:
- Items missing in Public Export included.
- Data and localizations split into separate files.
- More fields provided for some exports.

## Notes

- In ExportWarframes, the `health`, `shield`, `armor`, and `power` values represent the state at rank 0. [See here for an approach to level-scaling these stats.](https://github.com/Sainan/warframe-build-evaluator/blob/d05257f704e688ec387c697c6768b951cf3d5389/evaluator.pluto#L438-L500)
- [ExportRecipes](https://github.com/calamity-inc/warframe-public-export/blob/senpai/ExportRecipes.json) and [ExportManifest](https://raw.githubusercontent.com/calamity-inc/warframe-public-export/senpai/ExportManifest.json) will not be included in this project at present because those exports are already pretty good.
- ExportRelics does not have a `name` field, instead the added `category` and `era` fields can be used in conjuction with `/Lotus/Language/Relics/VoidProjectionName` to construct the name.
