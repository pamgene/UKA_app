# UKA_app
Upstream Kinase Analysis app for comparing all conditions in each column (for each supergroup). 
The direction of the comparison (contrast) is by default "Test vs Control" type: the condition starting with lower letter in the alphabet is used as the control condition.

## Versions:
* 0.0.1 - UKAdb 2025  (contains Array Layouts 86312, 86402, 86412, 87102, 87202, and no missing ids)
* 0.1.0 - UKAdb with Kinase Library db


## Inputs of the uka_operator:

Input projection|.
---|---
`y-axis`        | normalized data (log / VSN / Combat-corrected), single y value / cell
`row`           | peptides
`x axis` | grouping (test condition)
`column`| supergroup (required)
`label`| observations (samples, e.g. Barcode, Row)

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
