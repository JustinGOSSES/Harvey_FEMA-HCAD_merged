# Harvey_FEMA-HCAD_merged
A dataset that combines FEMA modeled flood damage and Harris County Appraisal District property data &amp; code built on top of that dataset

## Original Datasets

A. FEMA <a href="https://data.femadata.com/NationalDisasters/HurricaneHarvey/Data/DepthGrid/FEMA/Riverine_Modeled_Preliminary_Observations/20170901_Harris_Riverine_v2.gdb.zip">data</a> came from a 2017-09-01 model of flood damage. It isn't actual flood damage and new models are being made daily. *This model is not the latest!*

B. 2017 Real_acct_owner.zip on <a href="http://pdata.hcad.org/download/index.html"> here </a> is HCAD (Houston County Appraisal District) 2017 real-estate property details. It can be tied to (A or C) on the basis of HCAD ID number od Account number. 


C. 2017 Real_building_land.zip on <a href="http://pdata.hcad.org/download/index.html"> here </a> is land-use data tied to (A or B) Real_acct_owner data on the basis of HCAD ID number od Account number. 


D. Harris County <a href="http://data.houstontx.gov/en/dataset/harris-county-watersheds/resource/76a403db-77bd-4d40-816c-e3aa9a2b895b">watersheds</a>. This data was original in shape-file format by converted to geojson using <a href="/notebooks/HCAD-FEMAdamage-Watersheds.ipynb"> this notebook</a>. 

## Merged Datasets

1. The merged file of A, B, and C is called: *Harvey_FEMA_HCAD_Damage.json.zip* It can be found in the data folder and is zipped due to its size. Several columns are redundant or not really that useful. For example, one column says damage type is flood for every single row. It is a geojson of points. 

2. *Harvey_FEMA_HCAD_Damage_reduced.geojson.zip* is the same as (1) but has many of the redundant or not useful columns take out to reduce the file size and rendering speed. 

3. *Harvey_FEMA_HCAD_Damage_reduced_katy2.geojson.zip* is the same as (2) but it only includes properties in the city of Katy, Texas, which is a suburb on the west side of Houston. 

4. *HarrisCounty_Watersheds_poly.geojson* is a geojson of polygons representing all the watersheds of Harris County. While many of the other geojsons are feature collections of point features, this is a feature collection of just polygons. 

5. *Harvey_FEMA_HCAD_Damage_reduced_ws.geojson.zip* is the same as (2), but it adds a column for which watershed each property is within. This was done via a spatial join in <a href="/notebooks/HCAD-FEMAdamage-Watersheds.ipynb"> this notebook</a>.  

6. <a href="/data/Watershed_GeoJSONs/"> Watersheds_GeoJSONs folder</a> is a folder with a separate geojson for each watershed cut out of (5) using <a href="/notebooks/HCAD-FEMAdamage-Watersheds-makingByWatershedExcepts.ipynb">this</a> notebook. *Adding these as they are smaller and would be interesting to visualize themselves without dealing with the larger files.* 

### NOTE: PLEASE DO NOT UNZIP LARGE FILES AND LEAVE IT IN PLACE AND TRY TO PUSH BACK TO ORIGIN. It will gum up your git.
#### Many of these files are too big for github (>100mb) that is why they are zipped. I move unzipped files to a folder named, 'big_data_leave', which I think put in .gitignore file. 

