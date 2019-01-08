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
__Table 1: top softsite increase after adopting new Far values (by CD)__

| cd|softsites_new|softsites|diff|
|---|-------------|---------|----|
|503|        37489|    37467|  22|
|111|         1514|     1496|  18|
|302|         5126|     5122|   4|
|595|           18|       16|   2|
|307|        11232|    11230|   2|
|404|         9101|     9099|   2|
|305|        17627|    17625|   2|
|413|        37981|    37979|   2|
|484|           10|        8|   2|
|501|        31319|    31317|   2|
|411|        20874|    20872|   2|
|409|        18288|    18287|   1|
|208|         2589|     2588|   1|

__Table 2: top softsite increase after adopting new Far values (by borough)__

|borough|softsites_new|softsites|diff|
|-------|-------------|---------|----|
|     SI|        95252|    95226|  26|
|     MN|        14265|    14246|  19|
|     QN|       268405|   268392|  13|
|     BK|       229191|   229183|   8|
|     BX|        64052|    64049|   3|

__Table 3: complete list of zoning districts with maxfar increase__

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

__Table 4: Avergage residential maxfar and builtfar__

|   avg(maxfar_new)|       avg(maxfar)|     avg(builtfar)|
|------------------|------------------|------------------|
|1.1085407715997209|1.1666834392287233|0.8391015326831988|

__Table 5: Comparing pctunbuilt for maxfar vs new maxfar__

|                    |maxfar > maxfar_new|maxfar == maxfar_new| maxfar < maxfar_new |
|--------------------| ---------------|----------------|----------------|
|pctunbuilt_new > 0.5|           27705|           92399|            1076|
|    pctunbuilt > 0.5|           43285|           92399|             758|
|--------------------| ---------------|----------------|----------------|
|pctunbuilt_new = 0.5|            1686|            3655|               3|
|    pctunbuilt = 0.5|            2821|            3655|              30|
|--------------------| ---------------|----------------|----------------|
|pctunbuilt_new < 0.5|          285100|          259160|             381|
|    pctunbuilt < 0.5|          268385|          259160|             602|





# Explanation:
After switching to the new FAR values, we are seeing an increase in softsites all across the city.



## Resources
1. find new far lookup table [here](https://github.com/NYCPlanning/db-pluto/blob/master/pluto_build/data/dcp_zoning_maxfar.csv)
