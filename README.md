## PVPMC_2025

_Will Hobbs_

This is a repository for my 2025 PVPMC poster, "_Plant performance analysis with satellite resource data and public power data_".

<img src="presentation\2025_pvpmc_hobbs_ercot_sm.jpg" width="200"/> 

([view poster](presentation))

_Code for pulling from gridstatus.io and matching with EIA was based on code by Drumil Joshi, Southern Power Company._

## Why?
The goal of this work was to highlight a potentially valuable dataset from ERCOT: Power data are available for **every solar plant** in ERCOT at 15-min intervals back to 2012. I think **someone should analyze it all and publish results**.

This is just a small, informal preview of what could be done with that data.

## Details

A copy of the poster is in the [presentation](presentation) folder. I suggest you check it out first.

The notebook [Get_ERCOT_EIA_Data.ipynb](Get_ERCOT_EIA_Data.ipynb) gets plant metadata and timeseries power data from ERCOT and EIA. About 20 plants were initially selected semi-randomly with the following criteria:
- In service in 2022 or earlier
- Greater than 30 MW
- Then the first ~10 plants from each ERCOT region (alphabetical) with unique names were selected
- Plants where I had a known affiliation with the owner/operator were dropped (this is the non-random part)

I used https://github.com/gridstatus/gridstatusio to pull the timeseries data from https://www.gridstatus.io/. 

> _Note: data pulled form gridstatus.io are not included in this repository. Users will need to get that data using their own API key._

The list of plants was then filtered to plants that were operating for all of 2021, reducing the number to 10 plants.

Here's a sample of power data:

<img src="images\sample.png" width="400"/>

The notebook [Process_Specs_and_Data.ipynb](Process_Specs_and_Data.ipynb) converts specifications/metadata from ERCOT and EIA into parameters to model expected energy with the `model_pv_power()` function in `pv_model.py` from https://github.com/williamhobbs/pv-system-model and NREL NSRDB PSM4 weather data (pulled with the v0.12.1-alpha.1 release of https://github.com/pvlib/pvlib-python). It also includes some basic sample analyses.

Here's monthly performance index (PI) for the 10 plants, where 5 with subjectively large drops in PI are highlighted:

<img src="images\PI.png" width="400"/>

## Notes:

Things I didn't do, but *should* have, include:
- run more plants
- use pvanalytics 
  - clear sky filter, check tilt/az, try the new outlier check PR #223, ...
- use rdtools
- use solardatatools
- explore and explain the different data channels from ERCOT, like:
  - HSL = high sustainable limit, what the plant could procude when un-curtailed
  - Telemetered net output, what the plant actually produced
  - Basepoint, somehow a little different from telemetered net output??