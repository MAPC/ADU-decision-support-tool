# 4-1 | Type 1 ADU Fit Test

This model, 4-1 | Type 1 ADU Fit Test, uses the policy parameters recorded in the [zoningedits](../../analysis-preparation/tabular-inputs/#tabular-inputs) Excel spreadsheet to evaluate what parcels meet the eligibility requirements for a Type 1 ADU, that is, an ADUs developed within the principal building, without any expansion of that building's foundation.

### <mark style="background-color:orange;">Model Inputs</mark>

* Already present in the [zoningedits](../../analysis-preparation/tabular-inputs/) Excel spreadsheet:
  * Minimum Size for a Type 1 ADU (aduSFmn1)
  * Parcel Attribute Requirements:&#x20;
    * Type 1 ADU Permitted (adu1perm)
    * Minimum Size for a Type 1 Principal Building, in GSF (pGSFmn1)
    * Minimum Size for a Type 1 Principal Building, in FSF (pFSFmn1)
    * <mark style="background-color:orange;">Maximum Share of the Principal Building GSF a Type 1 ADU May Occupy (pmx1)</mark>
    * <mark style="background-color:orange;">Maximum Share of the Principal Building FSF a Type 1 ADU May Occupy (pFSFmxe1)</mark>
* Desired Setback Selection (see [Key Assumptions](4-1-or-type-1-adu-fit-test.md#key-assumptions)): Front Setback, Side Setback, or Rear Setback (This selection is made in the model tool parameters dialogue box.)
* possparcels\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../../analysis-steps/3-or-prepare-spatial-data-for-fit-tests.md))
* relstructures\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../../analysis-steps/3-or-prepare-spatial-data-for-fit-tests.md))

### <mark style="background-color:orange;">Model Outputs</mark>

* adjbuildarea2\_passadut3 (Geometry and attributes of parcels that have passed through the three Type 2 ADU Fit tests and are likely eligible.)&#x20;

### Key Assumptions

* While the tool is able to apply a different parcel setback for each zoning district and each ADU typology, the tool is not capable of applying different setbacks to each parcel at this time. This means that it cannot correctly render a zoning policy where the parcel front setback differs from the parcel side setback and/or the parcel rear setback. To provide as much flexibility as possible within this limitation, the model tool parameters dialogue box allows a user to define their preferred setback.

### Analysis

The fourth model uses the policy parameters recorded in the zoningedits Excel spreadsheet (attached to the parcel data and structure data in the previous step) to evaluate what parcels meet the eligibility requirements for a Type 2 ADU and which of those parcels are large enough to fit a Type 2 ADU. It does this through a sequence of three tests: one that checks the parcels against required attributes, one that determines buildable areas on the remaining parcels and checks these buildable areas are sufficiently large and compact, and one that ensures there is enough depth between the structures and the buildable areas to meet the minimum dimension of a Type 2 ADU.

#### Parcel Attribute Test

The first part of the model restricts the Possible Parcels data to only those parcels meeting the parcel attribute requirements.&#x20;

_Model Design_

![Screenshot of Model 4, Group 1: Type 2 ADU Parcel Attribute Tests. Click to expand.](../../.gitbook/assets/4-1a.png)



