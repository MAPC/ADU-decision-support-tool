# 4-3 | Type 3 ADU Fit Test

This model, 4-3 | Type 3 ADU Fit Test, uses the policy parameters recorded in the [zoningedits](../../analysis-preparation/tabular-inputs/#tabular-inputs) Excel spreadsheet to evaluate what parcels meet the eligibility requirements for a Type 3 ADU, that is, an ADUs developed within an existing accessory structure, without any expansion of that building's foundation.

### Model Inputs

* Already present in the [zoningedits](../../analysis-preparation/tabular-inputs/) Excel spreadsheet:
  * Minimum Size for a Type 3 ADU (aduSFmn3)
  * Parcel Attribute Requirements:&#x20;
    * Type 3 ADU Permitted (adu1perm)
    * Minimum Size for a Type 3 Principal Building, in GSF (pGSFmn1)
    * Minimum Size for a Type 3 Principal Building, in FSF (pFSFmn1)
* [allstructures\_estsf](../../analysis-preparation/tabular-inputs/type-3-adus-accessory-existing.md)
* possparcels\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../../analysis-steps/3-or-prepare-spatial-data-for-fit-tests.md))

### Model Outputs

* parcels\_passforadu3 (Geometry and attributes of parcels that have passed through the Type 3 ADU Fit tests and are likely eligible.)&#x20;

### Key Assumptions

* Level 3 Parcel Data does not contain square footage figures for accessory structures, so the tool uses estimates of square footage created by analyzing building footprints. This means parcels with two-story accessory structures may be unnecessarily eliminated.
* The tool does not test accessory structures for a minimum dimension.

### Analysis

This model uses the policy parameters recorded in the zoningedits Excel spreadsheet (attached to the parcel data and structure data in the previous step) to evaluate what parcels and accessory structures meet the eligibility requirements for a Type 3 ADU. It does this by restricting the Possible Parcels data to only those parcels meeting the parcel attribute requirements, then checking the accessory structures to make sure at least one accessory structure could accomodate .&#x20;

_<mark style="background-color:orange;">Model Design</mark>_

![Screenshot of Model 4, Group 1: Type 2 ADU Parcel Attribute Tests. Click to expand.](../../.gitbook/assets/4-1a.png)


