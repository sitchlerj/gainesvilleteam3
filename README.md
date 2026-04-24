# City of Gainesville Team 3
Team 3 Digital Access Datasets
- - - 
The data we are using includes foreign born populations, computer ownership, internet subscriptions, bus routes, and vehicles per household, to name a few. We downloaded various .csv files from the Census Bureau and then cleaned the data by changing variable names, removing redundant columns, consolidating multiple reports into one data set, and confirming all geographical identifications are consistent. The data we cleaned was filtered by Alachua County census tracts with the exception of internet access which was converted to zip codes of Gainesville City. 

We produced our first prototype of an interactive map, using the cleaned data sets, which layered bus routes with foreign born population by census tracts. After doing some research on the resources that were available to Gainesville residents, we decided to include library locations on this map. We noticed from this inclusion that the Millhopper Branch, which has the most foot traffic, was located in areas densely populated by foreign-born residents. Our map, titled “Gainesville Comprehensive Map”, includes toggle options for bus routes, bus stops, libraries, and city commission districts. The layers include Foreign Born Population (FB), % of Households w/ at Least One Vehicle, Computer Access & Broadband, Gross Rent as a % of Household Income, % Units with No Mortgage, and % Units with Mortgage. All layers are choropleth maps where the darker colors represent a higher density of populations/percentages of households, with the exception of the computer access which is denoted with hatching density.

All visualizations are reproducible in Google Colab, using mostly Python, but also some HTML and JavaScript. The file "current_gnv_comprehensive_map_code.ipynb" includes the code to replicate the current_gnv_comprehensive_map.html output, created with assistance from Anthropic's LLM.
- - -
Data and File Overview
======================
## Description of the data and file structures

This dataset contains 4 types of files: 

i)  U. S. Census Bureau/ACS Data by location
- vehicles.csv
- c_t_sheet_1.csv
- prop_computer_internet_household.csv
- with_mortgage.csv
- no_mortgage.csv
- newhousingdata.csv

ii) Google Colab Scripts
- current_gnv_comp_map.ipynb
  
iii) HTML Scripts (Maps)
- current_gnv_comprehensive_map.html

iv) Geographical Files
- aclib.csv
- tl_2020_12_tract.dbf
- tl_2020_12_tract.shp
- layer_0_20260128.csv
- Random.shp
- Random.dbf
- Spring2026_Weekday.shp
- Spring2026_Weekday.dbf
- par_citylm_2021.shp
- par_citylm_2021.dbf
- City_Commission_District_Export.shp
- City_Commission_District_Export.dbf

Details for i) U. S. Census Bureau/ACS Data by location
---------------------------------------
Description: 

Format(s): .csv

-vehicles.csv: Census Tracts as column names, rows as count data for the variables below (stratified by level), more variables than needed just in case. This is a compiled dataset from where we are pulling individual variables and cleaning separately.
		
		Relevant Sections:
 		 * 0: Number of households with 0 vehicles available
		 * 1: Number of households with 1 vehicle available
		 * 2: Number of households with 2 vehicles available
		 * 3: Number of households with 3 or more vehicles available
		 * Total: Total number of households per Census Tract
-c_t_sheet_1.csv: Alachua County Census Tracts as row names, columns for counts of the foreign-born population per tract (separated by the continent of origin for the foreign-born people)
		
		Relevant Variables:
		* Total: total population of the corresponding tract
		* FB: total foreign-born population of the corresponding tract
		* FB_Nat: total naturalized foreign-born population of the corresponding tract
		* FB_NC: total non citizen foreign-born population of the corresponding tract
-prop_computer_internet_household.csv: Columns are Census Tracts, Total Number of Households, Number of Households with Computer, Number of Households with Broadband Access, Proportion of Households with a Computer, Proportion of Households with Broadband Access (not separated by Foreign Born/Native)

		Relevant Variables:
		* Total_households: Total Number of Households
		* With_a_computer: Number of Households with Computer
		* With_a_broadband: Number of Households with Broadband Access
		* prop_computer: Proportion of Households with a Computer
		* prop_broadband: Proportion of Households with Broadband Access
-with_mortgage.csv: Alachua County Census Tracts as column names, rows for percentages of owner occupied units with a mortgage (not separated by Foreign Born/Native)

		Relevant Variables:
		* Housing units with a mortgage (excluding units where SMOCAPI cannot be computed): Total Units with a Mortgage
		* value_1: < 20% with a mortgage
		* value_2: 20-24.9% with a mortgage
		* value_3: 25-29.9% with a mortgage
		* value_4: 30-34.9% with a mortgage
		* value_5: > 35% with a mortgage
		* value_6: not computed

-no_mortgage.csv: Alachua County Census Tracts as column names, rows for percentages of owner occupied units without a mortgage (not separated by Foreign Born/Native)

		Relevant Variables:
		* value_1: < 10% without a mortgage
		* value_2: 10-14.9% without a mortgage
		* value_3: 15-19.9% without a mortgage
		* value_4: 20-24.9% without a mortgage
		* value_5: 25-29.9% without a mortgage
		* value_6: 30-34.9% without a mortgage
		* value_7: > 35% without a mortgage
		* value_8: not computed

-newhousingdata.csv: Alachua County Census Tracts as column names, rows for percentages of rent cost per household income (not separated by Foreign Born/Native)

		Relevant Variables:
		* value_1: < 15% total income
		* value_2: 15-19% total income
		* value_3: 20-24% total income
		* value_4: 25-29% total income
		* value_5: 30-34% total income
		* value_6: > 35% total income
		* value_7: not computed

Details for ii) Google Colab Scripts
---------------------------------------
Includes the Python, JavaScript, and HTML code to replicate the maps of Gainesville.

*Format(s): .ipynb

Details for iii) HTML Scripts (Maps)
---------------------------------------
The Python code outputs HTML maps.

*Format(s): .html

Details for iv) Geographical Files
---------------------------------------
These files include data for the map to have features such as locations (for libraries), Gainesville city borders, Gainesville City Commission Districts, Census tract borders, RTS bus routes, and RTS bus stops.

*Format(s): .csv, .cpg, .dbf, .prj, .sbn, .sbx, .shp, shp.xml, .shx


Sharing/Access information
======================

Data on digital access and households were extracted from the following sources:
- https://data.census.gov/table?q=s2504&g=050XX00US12001$1400000
- https://data.census.gov/table?q=S2801&g=050XX00US12001$1400000
- https://data.census.gov/table?t=Foreign-Born:Telephone,+Computer,+and+Internet+Access&g=050XX00US12001$1400000
- https://data.census.gov/table?q=B05002&g=050XX00US12001$1400000
- https://data.census.gov/table?q=B05002:+Place+of+Birth+by+Nativity+and+Citizenship+Status&g=050XX00US12001$1400000
- https://data.census.gov/table?q=DP04:+Selected+Housing+Characteristics&g=050XX00US12001$1400000

Data on geographical features was extracted from the following sources:
- https://catalog.data.gov/dataset/tiger-line-shapefile-2020-state-florida-census-tracts
- https://data.cityofgainesville.org/Geospatial-Maps-/Bus-Stops/kxwd-siv3
- https://catalog.data.gov/dataset/tiger-line-shapefile-2022-nation-u-s-2020-census-5-digit-zip-code-tabulation-area-zcta5/resource/1f3037ff-283c-40ac-9018-2de80e343f69
- https://go-rts.com/rts-data/
- https://fgdl.org/zips/metadata/xml/par_citylm_2021.xml
- GIS Specialist Juan Villa via the Department of Sustainable Development at the City of Gainesville

## Code Software
======================

Code is provided for Python version 3.12.12

- Package ‘pandas’ version 2.2.2
- Package ‘folium’ version 0.20.0
- Package ‘geopandas’ version 1.1.2
- Package ‘requests’ version 2.32.4
- Package ‘shapely.geometry’ version 2.1.2
- Package ‘google.colab’ version 1.0.0
- Package ‘branca’ version 0.8.2
- - -
END OF README
