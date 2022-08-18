# 3 | Prepare Spatial Data for Fit Tests

### Overview

The third model, 3 | Prepare Spatial Data for Fit Tests, joins the Zoning Edits table to the Possible Parcels Feature Class and to the Structures input. It generates two outputs: possparcels\_sjo\_zones, which has the same number of parcels as the Possible Parcels Feature Class, but with additional columns for the parcel's base zoning district, and the user-provided inputs for that zoning district...

![Screenshot of Model 3, Group 1: Join Possible Parcels to Zoning Edits. Click to expand.](<../.gitbook/assets/Model 3a.png>)

![Screenshot of Model 3, Group 2: Join Possible Parcels and Zoning Edits to Structures. Click to expand.](<../.gitbook/assets/Model 3b.png>)

### Inputs

* [zoningedits](../analysis-preparation/tabular-inputs/) Excel Spreadsheet and Cell Range
* [zoning\_base](../analysis-preparation/spatial-inputs/3-1.-zoning.md)
* [allstructures](../analysis-preparation/spatial-inputs/3-2.-all-structures.md)
* possible\_parcels (Generated from [2 | Define Possible Parcels](2-or-define-possible-parcels.md))

### Outputs

* possparcels\_sjo\_zones
* restructures\_sjo\_zones

### Key Assumptions

* XXX

