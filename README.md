# db-softsite-analysis

## Procedure
1. select only units 6 or less ```UnitsRes <= 6```
2. remove landmarks ```NOT Landmark is NULL```
3. remove irregular lot ```IrrLotCode = 'Y```
4. remove house of worship ```BldgClass LIKE 'M%'```
5. remove public institutions ```landuse = '08'```
6. remove lots with easement ```Easements > 0```

## Computing Maxfar and Pctpctunbuilt:
1. ``` MaxFar = max(ResidFar, CommFair) ```
2. ``` Pctpctunbuilt = (MaxFar - BuiltFar)/Maxfar```

## Results:
__Table 1: top softsite increase (by CD)__

| cd|softsites_new|softsites|diff|
|---|-------------|---------|----|
|302|         1018|     1008|  10|
|301|         2927|     2917|  10|
|206|         1670|     1666|   4|
|308|         1777|     1773|   4|
|309|         2402|     2399|   3|
|102|          262|      259|   3|
|303|         2916|     2913|   3|
|201|         1568|     1566|   2|
|202|         1459|     1457|   2|
|484|            9|        7|   2|
|316|         3911|     3909|   2|
|304|         2599|     2597|   2|
|110|          810|      808|   2|
|205|         1252|     1250|   2|
|595|           18|       16|   2|
|204|         1299|     1298|   1|
|306|         1740|     1739|   1|
|203|         1471|     1470|   1|
|207|         1223|     1223|   0|
|101|           45|       45|   0|

__Table 1: top softsite decrease (by CD)__

| cd|softsites_new|softsites| diff|
|---|-------------|---------| ----|
|412|         4827|     6697|-1870|
|503|         6591|     8251|-1660|
|501|         6623|     8234|-1611|
|502|         5577|     6762|-1185|
|413|         4771|     5918|-1147|
|410|         1881|     2919|-1038|
|318|         2686|     3721|-1035|
|407|         3080|     3906| -826|
|405|         2518|     3169| -651|
|212|         3408|     4003| -595|
|315|         2686|     3205| -519|
|409|         1861|     2309| -448|
|408|         1501|     1925| -424|
|414|         2463|     2876| -413|
|210|         2016|     2428| -412|
|211|         1779|     2180| -401|
|411|         2136|     2524| -388|
|108|          687|      972| -285|
|317|         4578|     4842| -264|
|106|          347|      536| -189|

__Table 3: softsite change by borough__

|borough|softsites_new|softsites| diff|
|-------|-------------|---------| ----|
|     MN|         5575|     6106| -531|
|     BX|        20241|    21727|-1486|
|     BK|        48361|    50568|-2207|
|     SI|        18810|    23264|-4454|
|     QN|        33537|    41283|-7746|

__Table 4: complete list of zoning districts with maxfar increase__

|zonedist1|counts|
|---------|------|
|R8A      |591   |
|M1-1     |133   |
|R3-2     |79    |
|R6B      |71    |
|R3A      |66    |
|R5       |59    |
|PARK     |52    |
|R4       |51    |
|C8-1     |51    |
|R6       |43    |
|C8-2     |36    |
|R3X      |36    |
|M1-4/R8A |20    |
|R4A      |20    |
|R4B      |19    |
|M1-6/R9  |18    |
|R5B      |18    |
|R2       |13    |
|R7-1     |11    |
|C8-3     |11    |
|R6A      |10    |
|M1-2     |10    |
|R3-1     |8     |
|R4-1     |7     |
|M1-4/R7X |7     |
|M1-4/R7D |5     |
|R2A      |4     |
|M1-5     |4     |
|M1-4     |3     |
|C8-4     |2     |
|R7-2     |2     |
|R8B      |2     |
|M1-1/R6A |2     |
|M3-1     |2     |
|R8       |1     |
|M1-4D    |1     |
|R10      |1     |
|R7A      |1     |
|R5D      |1     |
|M2-1     |1     |

__Table 5: Avergage residential maxfar and builtfar__

|   avg(maxfar_new)|       avg(maxfar)|     avg(builtfar)|
|------------------|------------------|------------------|
|1.1085407715997209|1.1666834392287233|0.8391015326831988|

__Table 6: Maxfar change counts__

|increase|decrease|unchanged|
|--------|--------|---------|
|    1472|  315182|   356009|

__Table 7: Percentunbuilt value comparison, old vs new__

|                    |   >0.5|   =0.5|   <0.5|
|------------------  |-------|-------|-------|
|Old Percentunbuilt  | 136442|   6506| 528148|
|New Percentunbuilt  | 121180|   5344| 544641|
|New - Old difference| -15262|  -1162|  16493|


# Explanation:
After switching to the new FAR values, we are seeing an increase in softsites all across the city.



## Resources
1. find new far lookup table [here](https://github.com/NYCPlanning/db-pluto/blob/master/pluto_build/data/dcp_zoning_maxfar.csv)
