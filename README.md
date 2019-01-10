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
|---|-------------:|---------:|----:|
|111|          942|      923|  19|
|302|         1,018|     1,008|  10|
|301|         2,927|     2,917|  10|
|206|         1,670|     1,666|   4|
|108|          976|      972|   4|
|308|         1,777|     1,773|   4|
|102|          262|      259|   3|
|303|         2,916|     2,913|   3|
|104|          620|      617|   3|
|309|         2,402|     2,399|   3|
|316|         3,911|     3,909|   2|
|304|         2,599|     2,597|   2|
|595|           18|       16|   2|
|106|          538|      536|   2|
|484|            9|        7|   2|
|110|          810|      808|   2|
|205|         1,252|     1,250|   2|
|204|         1,300|     1,298|   2|
|201|         1,568|     1,566|   2|
|202|         1,459|     1,457|   2|

__Table 1: top softsite decrease (by CD)__

| cd|softsites_new|softsites| diff|
|---|-------------|---------| ----|
|412|         4,827|     6,697|-1,870|
|503|         6,591|     8,251|-1,660|
|501|         6,623|     8,234|-1,611|
|502|         5,577|     6,762|-1,185|
|413|         4,771|     5,918|-1,147|
|410|         1,881|     2,919|-1,038|
|318|         2,686|     3,721|-1,035|
|407|         3,080|     3,906| -826|
|405|         2,518|     3,169| -651|
|212|         3,408|     4,003| -595|
|315|         2,686|     3,205| -519|
|409|         1,861|     2,309| -448|
|408|         1,501|     1,925| -424|
|414|         2,463|     2,876| -413|
|210|         2,016|     2,428| -412|
|211|         1,779|     2,180| -401|
|411|         2,136|     2,524| -388|
|317|         4,578|     4,842| -264|
|311|         2,026|     2,166| -140|
|403|         1,208|     1,342| -134|

__Table 3: softsite change by borough__

|borough|softsites_new|softsites| diff|
|-------|-------------:|---------:| ----:|
|     MN|         6,140|     6,106|   34|
|     BX|        20,242|    21,727|-1,485|
|     BK|        48,361|    50,568|-2,207|
|     SI|        18,810|    23,264|-4,454|
|     QN|        33,537|    41,283|-7,746|

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
|C8-1     |51    |
|R4       |51    |
|R6       |43    |
|C8-2     |36    |
|R3X      |36    |
|R4A      |20    |
|M1-4/R8A |20    |
|R4B      |19    |
|M1-6/R9  |18    |
|R5B      |18    |
|R2       |13    |
|R7-1     |11    |
|R6A      |11    |
|C8-3     |11    |
|M1-2     |10    |
|M1-5     |9     |
|R3-1     |8     |
|M1-4     |8     |
|R4-1     |7     |
|M1-4/R7X |7     |
|M1-4/R7D |5     |
|R2A      |4     |
|R8B      |4     |
|C8-4     |4     |
|R8       |3     |
|R7B      |3     |
|R7-2     |3     |
|M1-5M    |2     |
|M1-1/R6A |2     |
|M3-1     |2     |
|M1-4D    |1     |
|R5D      |1     |
|R10      |1     |
|M3-2     |1     |
|M2-1     |1     |
|R7A      |1     |

__Table 5: Avergage residential maxfar and builtfar__

|   avg(maxfar_new)|       avg(maxfar)|     avg(builtfar)|
|------------------|------------------|------------------|
|1.1086672562662478|1.1666834392287233|0.8391015326831988|

__Table 6: Maxfar change counts__

|increase|decrease|unchanged|
|--------:|--------:|---------:|
|    1,496|  356,678|   314,489|

__Table 7: Percentunbuilt value comparison, old vs new__

|                    |   >0.5|   =0.5|   <0.5|
|------------------  |-------:|-------:|-------:|
|Old PercentUnbuilt  | 136,442|   6,506| 528,148|
|New PercentUnbuilt  | 121,755|   5,335| 544,075|
|New - Old Difference| -14,687|  -1,171|  15,927|


# Explanation:
After switching to the new FAR values, we are seeing an increase in softsites all across the city.



## Resources
1. find new far lookup table [here](https://github.com/NYCPlanning/db-pluto/blob/master/pluto_build/data/dcp_zoning_maxfar.csv)
