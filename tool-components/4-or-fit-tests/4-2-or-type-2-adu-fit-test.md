# 4-2 | Type 2 ADU Fit Test

The fourth model, 4-2 | Type 2 ADU Fit Test, uses the policy parameters recorded in the [zoningedits](../../analysis-preparation/tabular-inputs/#tabular-inputs) Excel spreadsheet to evaluate what parcels meet the eligibility requirements for a Type 2 ADU, that is, an ADU built as an addition to an existing structure. The model also evaluates which of those parcels are large enough to fit a Type 2 ADU.

### Model Inputs

* From the [zoningedits](../../analysis-preparation/tabular-inputs/) Excel spreadsheet:
  * Parcel Attribute Requirements: Type 2 ADU Permitted (adu2perm), Minimum Size for a Type 2 Principal Building, in GSF (pGSFmn2), Minimum Size for a Type 2 Principal Building, in FSF (pFSFmn2), Maximum Expansion of the GSF of a Type 2 Principal Building (pGSFmxe2), and Maximum Expansion of the FSF of a Type 2 Principal Building (pFSFmxe2).
  * Parcel Setback Requirements: Front (pafrStbk2), Side (pasiStbk2), or Rear (pareStbk2).
  * ADU Size Requirements: Minimum Size of a Type 2 ADU (aduSFmn2).
* possparcels\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../../analysis-steps/3-or-prepare-spatial-data-for-fit-tests.md))
* relstructures\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../../analysis-steps/3-or-prepare-spatial-data-for-fit-tests.md))

### Model Outputs

* adjbuildarea2\_passadut3

### Key Assumptions

* <mark style="background-color:orange;">XXX</mark>

### Analysis

The fourth model uses the policy parameters recorded in the zoningedits Excel spreadsheet (attached to the parcel data and structure data in the previous step) to evaluate what parcels meet the eligibility requirements for a Type 2 ADU and which of those parcels are large enough to fit a Type 2 ADU. <mark style="background-color:orange;">It does this through a sequence of three tests: one that checks the parcels against required attributes, one that evaluates...</mark>

#### Test One: Parcel Attributes

The first part of the model restricts the Possible Parcels data to only those parcels meeting the parcel attribute requirements.&#x20;

![Screenshot of Model 4, Group 1: Type 2 ADU Parcel Attribute Tests. Click to expand.](../../.gitbook/assets/4-1a.png)

#### Test Two: Parcel Fit Tests

Parcels meeting the parcel attribute requirements are then screened for ...&#x20;

_Generate Parcel Setbacks for Type 2 ADUs_

![Screenshot of Model 4, Group 2a: Generate Parcel Setbacks for Type 2 ADUs. Click to expand.](../../.gitbook/assets/4b.png)

_Combine Buildable Areas and Unbuildable Area (Structures)_

![Screenshot of Model 4, Group 2b: Combinate Buildable Areas and Unbuildable Areas (Structures). Click to expand.](<../../.gitbook/assets/4c (1).png>)

![](../../.gitbook/assets/4d.png)



###

