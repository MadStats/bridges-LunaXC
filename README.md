###  Bridges of the USA.  
[I think this data is so interesting.](https://www.fhwa.dot.gov/bridge/nbi/ascii.cfm)  When you find some data, you should always look for the [data descriptions](https://www.fhwa.dot.gov/bridge/mtguide.pdf).  From page 38, we have the ratings of bridge conditions (for Deck, Superstructure, and Substructure), for *every bridge in the US*, for every year back to 1991.  Lots of other data on each bridge (e.g. county FIPS code of the bridge). 

Warm up:  make a file with bridge ID, year, fips codes, condition ratings, and a few other variables that interest you.  Make your code reproducible and post to github.  


CODE:

Bridge2000 = read.csv("Bridges Data.txt", sep = ",")
ID = Bridge2000$STRUCTURE_NUMBER_008
year = Bridge2000$YEAR_BUILT_027
state = formatC(Bridge2000$STATE_CODE_001, width=2, flag="0")
county = state = formatC(Bridge2000$COUNTY_CODE_003, width=3, flag="0")
FIPS = paste(state, county, sep = "")
operation_R = Bridge2000$OPERATING_RATING_064
inventory_R = Bridge2000$INVENTORY_RATING_066
SR = Bridge2000$SUFFICIENCY_RATING
reconstruct_year = Bridge2000$YEAR_RECONSTRUCTED_106
ADT = Bridge2000$YEAR_ADT_030
future_ADT = Bridge2000$YEAR_OF_FUTURE_ADT_115
B2000 = data.frame(ID, year, FIPS, operation_R, inventory_R, SR, reconstruct_year, ADT, future_ADT)