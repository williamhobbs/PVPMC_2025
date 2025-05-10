### PVPMC_2025

_Will Hobbs_

This is a repository for the 2025 PVPMC poster, "_Plant performance analysis with satellite resource data and public power data_".

The notebook [Get_ERCOT_EIA_Data.ipynb](Get_ERCOT_EIA_Data.ipynb) gets plant metadata and timeseries power data from ERCOT and EIA. It uses https://github.com/gridstatus/gridstatusio to pull the timeseries data from https://www.gridstatus.io/. 

> _Note: data pulled form gridstatus.io are not included in this repository. Users will need to get that data using their own API key._

The notebook [Process_Specs_Updated.ipynb](Process_Specs_Updated.ipynb) converts specifications/metadata from ERCOT and EIA into parameters to model expected energy with the `model_pv_power()` function in `pv_model.py` from https://github.com/williamhobbs/pv-system-model and NREL NSRDB PSM4 weather data (pulled with the v0.12.1-alpha.1 release of https://github.com/pvlib/pvlib-python). It also includes some basic sample analyses.

A copy of the poster is in the [presentation](presentation) folder.