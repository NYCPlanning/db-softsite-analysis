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

## Resources
1. find new far lookup table [here](https://github.com/NYCPlanning/db-pluto/blob/master/pluto_build/data/dcp_zoning_maxfar.csv)
