# UKA_app
Upstream Kinase Analysis app for comparing all conditions in each column (for each supergroup). 
The direction of the comparison (contrast) is by default "Test vs Control" type: the condition starting with lower letter in the alphabet is used as the control condition.

## Versions:

UKA_app version|UKAdb version|UKAdb year|UKA operator version|Description
---|---|---|---|---
0.0.1|0.3.0|2025|0.3|Used for UKA_app, does everything vs everything comparison for each supergroup.
0.1.0|0.4.0|2025|0.4|UKAdb includes Kinase Library (KL) db with all ranks = 1. New parameter in UKA operator: KL weight.
0.2.0|0.5.0|2025|0.5|UKA operator changes: FC input supported (new parameter: UKAType); exports kinase entrezid; bugfix: IDs previously not used bc of typo & special characters (H2B1B_ 27_40, VGFR1_1320_1332_C1320K/C1321K and VGFR1_1320_1332_C1320S/C1321S) are fixed. UKAdb changes: KL db with its own ranks; mutated PTK peptides with Protein matches from nonmutated sequences. Family of some kinases were manually added. 

Before this UKA app, different UKA apps were used:

UKA app type|UKAdb version|UKAdb year|UKA operator version|Description
---|---|---|---|---
-|0.0.1|2022|Local BioNavigator version|Used in local BioNavigator-
[UKA_shiny_app](https://github.com/pamgene/UKA_shiny_app)|0.1.0|2023|0.0-0.0.4|Contains Array Layouts 86312, 86402, 86412, 87102. Used for apps UKA_TGC, UKA_MTvC.
[UKA_TGC](https://github.com/pamgene/UKA_TGC_app), [UKA_MTvC](https://github.com/pamgene/UKA_MTvC_app)|0.2.0|2024|0.1.0|New array layout added: 87202. 
UKA_TGC, UKA_MTvC|0.3.0|2025|0.2.0|Bugfix: missing IDs are added: MK07_212_224, JAK1_1027_1039, DCX_67_79. 
UKA_TGC, UKA_MTvC|0.3.0|2025|0.2.4|Dual specificity kinases excluded from the results.

## Input projection of the uka_operator:

Input projection|.
---|---
`y-axis`        | normalized data (log / VSN / Combat-corrected), single y value / cell
`row`           | peptides
`x axis` | grouping (test condition)
`column`| supergroup (required)
`label`| observations (samples, e.g. Barcode, Row)

## Input Parameters of the uka_operator:

Input parameters|Default value|.
---|---|---
`Kinase_family`| PTK | Type of kinase family, either PTK or STK.
`MinimumSequenceHomology`| 0.9 | Minimum sequence homology between peptides and phosphosites
`MinimumKxsScore` | 300 | Minimum PhospoNET score for upstream kinases
`NumberOfPerms` | 500 | Number of permutations to calculate significance and specificity scores
`MinRank` | 4 | Minimum PhospoNET rank for upstream kinases
`MaxRank` | 12 | Maximum PhospoNET rank for upstream kinases
`IvivWeight` | 1 |  in vivo in vitro weight
`PNETWeight` | 1 | PhospoNET weight
`KLWeight` | 1 | Kinase Library weight
`MinimumSetSize` | 3 | Minimum peptide set size for a kinase
`rmDualSpecKinases` | True | Remove dual specificity kinases. For PTK, only TYR group is kept. For STK, TYR group is excluded.
`ReverseContrast` | True | The direction of the contrast (Test vs Control or Control vs Test). True means "Test vs Control" type comparison.

## Outputs:
- volcano
- shiny volcano
- export table 
- histogram of Median Final score
