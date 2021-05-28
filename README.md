# CloudPandas Client

This module provides a client for working with the [CloudPandas](https://www.cloudpandas.com) API.  CloudPandas is a SaaS platform to streamline working with cloud based spreadsheets such as SmartSheet and Google Sheets using Python Pandas.  It allows users to read from and write to, these cloud based spreadsheets as DataFrames.  

See full documentation at https://www.cloudpandas.com/account/support/

---------
## Install CloudPandas Module
### Preferred Method:  PIP
`python3 -m pip install cloudpandas`

### Alternate Method:  Download from GitHub
`git clone https://github.com/jefalexa/cloudpandas.git`

---------
## Use CloudPandas Module
### Import
Once you have installed the module, you can then import it into your Python scripts.  

`import pandas as pd`

`import cloudpandas`

--
### Initialize Client
Get your API token from https://www.cloudpandas.com/account/tokenget/

`client = cloudpandas.Client('YOUR-API-TOKEN')`

--
### List Data Providers
You can see the data providers that are active in your account using:  

`client.dataproviders.list()`

--
### List Sheets
List the sheets in a given data provider using:  

`client.sheets.list(provider_name)`

--
### Get Sheet Info
You can optionally, get information about a sheet before loading it.  

`client.sheets.info(provider_name, sheet_name)`

--
### Load Data from Sheet
Load a sheet from the data provider as a Pandas DataFrame.  

`DF = client.sheets.get(provider_name, sheet_name)`

--
### Create a New Sheet
You can write data from a Pandas DataFrame to a new cloud sheet using:  

`client.sheets.create(DF, provider_name, sheet_name=sheet_name, sheet_type=sheet_type)`

sheet_type options are 'sheet' for creating a native cloud sheet in SmartSheet or Google Sheets, or 'excel' or 'csv' for writing a file to Box, Dropbox, Google Drive.  

--
### Update Existing Sheet
You can update an existing sheet with changes from a DataFrame using:  

`client.sheets.update(DF, provider_name, sheet_id=sheet_id)`

--
### Delete Existing Sheet
Sheets can be deleted using:

`client.sheets.delete(provider_name, sheet_id=sheet_id)`