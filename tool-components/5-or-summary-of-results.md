# 5 | Summary of Results

The fifth model, 5 | Summary of Results, joins the outputs from the four Fit Tests back to the All Parcels, to generate a complete table of results, and summarizes these results by user-specified summary geography, such as neighborhood boundaries.

### Model Inputs

* [allparcels](../analysis-preparation/spatial-inputs/1-3.-all-parcels.md)
* <mark style="background-color:orange;">Results from ADU Typology Fit Tests</mark>
  * <mark style="background-color:orange;">Name of Type 1 Output</mark>
  * adjbuildarea2\_passadut3 (Parcels likely eligible for Type 2 or Principal-New, ADUs&#x20;
  * <mark style="background-color:orange;">Name of Type 3 Output</mark>
  * <mark style="background-color:orange;">Name of Type 4 Output</mark>
* <mark style="background-color:orange;">Summary Geography</mark>

### Model Outputs

* <mark style="background-color:orange;">XXX</mark>

### Key Assumptions

* <mark style="background-color:orange;">XXX</mark>

### Analysis

<mark style="background-color:orange;">The fifth model joins the Zoning Edits table to the Possible Parcels Feature Class and then to the Structures input. It generates two outputs:</mark>&#x20;

* <mark style="background-color:orange;">possparcels\_sjo\_zones, which has the same number of parcels as the Possible Parcels (possible\_parcels) Feature Class but has additional fields with the parcel's base zoning district, and the associated user-provided policy inputs.</mark>
* <mark style="background-color:orange;">relstructures\_sjo\_zones, which only contains structures that have their center in a parcel in the Possible Parcels Feature Class. As with the possparcels\_sjo\_zones output, the resulting structures data has additional fields with the associated parcel, that parcel's base zoning district, and the associated user-provided policy inputs.</mark>
