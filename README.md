# Task
Find the maximum temperature for a given country and state, then write the result to a file on DBFS in parquet format.
Assumptions:
- Source data: https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data?resource=download (file: GlobalLandTemperaturesByState.csv)
- Solution: source code on github (with unit tests), package published in PyPI (package build and upload can be manual)
- Tools: PySpark + Databricks (Community Edition) - package installed with PyPI, file to run package can be in notebook
- Job parameters: input path and output path

# Solution documentation
Python lib name "climate_change_temp"
Data uploaded into 
- dbfs:/FileStore/shared_uploads/krzychzet@gmail.com/GlobalLandTemperaturesByState.csv

## Source code
  Directory: src
1. GlobalLandTemperaturesByState.py - 1st  non object version
2. GlobalLandTemperaturesByStateObj.py - 2nd obj version

## Databricks scripts 
Requirements :  PySpark + Databricks (Community Edition) Spark 3.0.1
  /test/databrick_scripts/
1. File: V_climate_change_with_lib_short.dbc - databrick with non object lib version
2. File: V_climate_change_with_lib_obj_short.dbc -  databrick with object lib version

Example ussage :
``` Databrick_notebook V_climate_change_with_lib_short
#import custom package
from climate_change_temp.GlobalLandTemperaturesByState import *
#source csv  https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data?resource=download (file: GlobalLandTemperaturesByState.csv) uploaded to dbfs:/FileStore/shared_uploads/krzychzet@gmail.com/ 
source_csv_filename="dbfs:/FileStore/shared_uploads/krzychzet@gmail.com/GlobalLandTemperaturesByState.csv"
#destination parquet dir 
permanent_parquet_dir = "dbfs:/FileStore/shared_uploads/krzychzet@gmail.com/GlobalLandTemperaturesByState_parquet"
#transpormation execution 
maxtemp(spark,source_csv_filename,permanent_parquet_dir)
```
## Pytphon package  
  Directory: dist
  Name: climate_change_temp
1. climate_change_temp-0.1.0-py3-none-any.whl - py whl package



## Python library build
   py -m build
