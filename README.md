# City of Gainesville Team 3
Team 3 Digital Access Datasets
- - - 
The data we are using includes foreign born populations, computer ownership, internet subscriptions, bus routes, and vehicles per household, to name a few. We downloaded various .csv files from the Census Bureau and then cleaned the data by changing variable names, removing redundant columns, consolidating multiple reports into one data set, and confirming all geographical identifications are consistent. The data we cleaned was filtered by Alachua County census tracts with the exception of internet access which was converted to zip codes of Gainesville City. 

Currently, we are using these data sets to run T-tests in R. Our hope is to determine if there are any significant differences of the internet access between the various census tracts. This conclusion, along with the foreign born population data in each census tract, will give us insight into if there are possible underlying issues with respect to these themes. 

We produced our first prototype of an interactive map, using the cleaned data sets, which layered bus routes with foreign born population by census tracts. After doing some research on the resources that were available to Gainesville residents, we decided to include library locations on this map. We noticed from this inclusion that the Millhopper Branch, which has the most foot traffic, was located in areas densely populated by foreign-born residents. Our map, titled “Comprehensive Gainesville Map”, includes toggle options for bus routes + spots, libraries, city limits, populations, and census tracts. We expect to add elements to reflect vehicles per household and potentially computer access  We created this visualization using existing shapefiles and trajectories taken from both the City of Gainesville official website and the U.S. Census Bureau.

All analyses were conducted in R and all visualizations were created in Python. The file "proportion_of_households_with_computers_per_tract.Rmd" includes all code required to replicate our analyses, "internet_access_zip_code.ipynp" includes the code to replicate the internet_coverage.html map, and "gainesville_comprehensive_map.ipynb" includes the code to replicate the comprehensive_gnv_map.html map.
- - -
Data and File Overview
======================
## Description of the data and file structures

This dataset contains 4 types of files: 

i)  U. S. Census Bureau/ACS Data by location
- computer_internet_vehicles.csv
- c_t_sheet_1.csv
- foreign_born_zip_codes.csv
- internet_coverage_zip_codes.csv
- computer_broadband.xlsx

ii) R Scripts
- proportion_of_households_with_computers_per_tract.Rmd
- proportions_for_computers_and_internet_access_for_household_per_tract.Rmd

iii) Python Scripts
- gainesville_comprehensive_map.ipynb
- internet_coverage_zip_code.csv

iv) HTML Scripts (Maps)
- comprehensive_gnv_map.html
- internet_coverage_map.html

v) Geographical Files
- aclib.csv
- tl_2020_12_tract.dbf
- tl_2020_12_tract.shp
- layer_0_20260128.csv
- PlanningTest_DBO_MunicipalBoundary_data_20260128.csv
- Random.shp
- Random.dbf
- Spring2026_Weekday.shp
- Spring2026_Weekday.dbf
- par_citylm_2021.shp
- par_citylm_2021.dbf

Details for i) U. S. Census Bureau/ACS Data by location
---------------------------------------
Description: 

Format(s): .csv, .xlsx

-computer_internet_vehicles.csv: Census Tracts as column names, rows as count data for the variables below (stratified by level), more variables than needed just in case. This is a compiled dataset from where we are pulling individual variables and cleaning separately.
		
		Relevant Sections:
 		 * COMPUTERS_AND_INTERNET_USE
 		 * TYPES OF COMPUTER
  		 * TYPES OF INTERNET SUBSCRIPTION
		 * VEHICLES AVAILABLE 
-c_t_sheet_1.csv: Alachua County Census Tracts as row names, columns for counts of the foreign-born population per tract (separated by the continent of origin for the foreign-born people)
		
		Relevant Variables:
		* Total: total population of the corresponding tract
		* FB: total foreign-born population of the corresponding tract
		* FB_Nat: total naturalized foreign-born population of the corresponding tract
		* FB_NC: total non citizen foreign-born population of the corresponding tract
-foreign_born_zip_codes.csv: Variables as row names and columns as the ZCTA values of Gainesville, excluding the UF ZIP codes
		
		Relevant Variables:
		* Europe: total foreign-born population in the corresponding ZCTA originally 
		from Europe
		* Latin_America: total foreign-born population in the corresponding ZCTA 
		originally from Latin America
		*Asia: total foreign-born population in the corresponding ZCTA 
		originally from Latin America
		*Other: total foreign-born population in the corresponding ZCTA 
		originally from Africa, Oceana, or North America
-internet_coverage_zip_codes.csv: Variables are Zip Code and Percent Internet Coverage as columns
		
		Relevant Variables:
		*Zip Code: There are 10 ZIP codes listed, for the 10 ZTCA values of Gainesville, excluding UF
		*Percent Internet Coverage: This is the percentage of households in the corresponding ZCTA that have an internet subscription or have internet access 
-computer_broadband.xlsx: Columns are Census Tracts in all of Alachua County, not just Gainesville CCD, and it tells us the number of households, the number of households with a computer, and the number of households with an internet subscription
		
		Relevant Variables:
		*Total_households: The total number of households in the corresponding Census tract
		*With_a_computer: The total number of households in the corresponding Census tract with at least one computer
		*With_a_broadband_Internet_subscription:  The total number of households in the corresponding Census tract with a broadband Internet subscription

Details for ii) R Scripts
---------------------------------------
Includes the R-code to run Bonferroni tests for significant differences, ANOVA, and a logistic regression. These files have the codes to our current exploratory data analyses, finding significant differences between tracts using a Bonferroni method. This is currently in progress, and we will update this file to provide the most accurate analyses it has completed.

*Format(s): .Rmd
  
Details for iii) Python Scripts
---------------------------------------
Includes the Python code to replicate the maps of Gainesville.

*Format(s): .ipynb

Details for iv) HTML Scripts (Maps)
---------------------------------------
The Python code outputs HTML maps.

*Format(s): .html

Details for v) Geographical Files
---------------------------------------
These files include data for the map to have features such as locations (for libraries), Gainesville city borders, Census Tract borders, ZIP Code Tabulation Areas, RTS bus routes, and RTS bus stops.

*Format(s): .csv, .cpg, .dbf, .prj, .sbn, .sbx, .shp, shp.xml, .shx


##Sharing/Access information
======================

Data on digital access was extracted from the following sources:
- https://data.census.gov/table?q=s2504&g=050XX00US12001$1400000
- https://data.census.gov/table?q=S2801&g=050XX00US12001$1400000
- https://data.census.gov/table?t=Foreign-Born:Telephone,+Computer,+and+Internet+Access&g=050XX00US12001$1400000
- https://data.census.gov/table?q=B05002&g=050XX00US12001$1400000
- https://bestneighborhood.org/tv-and-internet-gainesville-fl/
- https://data.census.gov/table?q=B05002&g=860XX00US32601,32603,32605,32606,32607,32608,32609,32641,32653,32669

Data on geographical features was extracted from the following sources:
- https://catalog.data.gov/dataset/tiger-line-shapefile-2020-state-florida-census-tracts
- https://data.cityofgainesville.org/Geospatial-Maps-/Bus-Stops/kxwd-siv3
- https://catalog.data.gov/dataset/tiger-line-shapefile-2022-nation-u-s-2020-census-5-digit-zip-code-tabulation-area-zcta5/resource/1f3037ff-283c-40ac-9018-2de80e343f69
- https://data.cityofgainesville.org/Geospatial-Maps-/Municipal-Boundary/8snj-9ywy
- https://go-rts.com/rts-data/
- https://experience.arcgis.com/experience/23f2a92f6f814f94b919a6e964233329
- https://fgdl.org/zips/metadata/xml/par_citylm_2021.xml

## Code Software
======================

Code is provided for R version 4.5.1 (2025-06-13)

- Package ‘readxl’ version 1.4.5
- Package ‘tidyr’ version 1.3.1
- Package ‘stringr’ version 1.5.2
- Package ‘dplyr’ version 1.5.2
- Package ‘emmeans’ version 2.0.1

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
