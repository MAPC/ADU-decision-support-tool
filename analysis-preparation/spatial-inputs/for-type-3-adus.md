# For Type 3 ADUs

Type 3 (Accessory-Existing) ADUs involve the conversion of an existing accessory structure to an ADU. This requires an assessment of whether any of the existing accessory structures on the parcel is sufficiently large to accommodate the smallest allowable ADU. Unfortunately, Level 3 Parcel Data does not contain square footage figures for accessory structures, so the tool uses estimates of square footage created by analyzing building footprints. The following provides instructions for generating a lookup table, **allstructures\_estsf,** with this information.

#### Input Preparation

* [ ] If it has not already been retrieved in an earlier step, retrieve spatial data for the structures in the Study Municipality. The ADU Tool was developed using structure data from the MassGIS Building Structures layer, and we highly recommend continuing to use this data as the source for the All Structures Input. Data is available here: [https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-](https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-) Add the downloaded spatial data to ADU-Analytical-Tool\_Spatial-Inputs.gdb, titled "allstructures."
* [ ] Execute a spatial join to relate the structures data to the parcel data, using:
  * Target Features = allstructures
  * Join Features = allparcels
  * Output Feature Class = allstru\_sjo\_allparc
    * Uncheck "Keep All Target Parcels"
  * Join Operation = JOIN\_ONE\_TO\_MANY
  * Match Option = HAVE\_THEIR\_CENTER\_IN
* [ ] Open allstru\_sjo\_allparc. Execute a dissolve, using:
  * Input Features = allstru\_sjo\_allparc
  * Output Feature Class = allstructures\_estsf
  * Dissolve Fields = parloc\_id
  * Statistics Fields
    * area\_sq\_ft as a Count (count\_area\_sq\_ft)
    * area\_sq\_ft as a Sum (sum\_area\_sq\_ft)
    * area\_sq\_ft as a Max (max\_area\_sq\_ft)
    * area\_sq\_ft as a Min (min\_area\_sq\_ft)
* [ ] Open allstructures\_estsf. **** Retitle the Statistics Fields from the Dissolve:
  * Retitle count\_area\_sq\_ft to "strucount"
  * Retitle sum\_area\_sq\_ft to "struSFsum"
  * Retitle max\_area\_sq\_ft to "struSFmx"
  * Retitle min\_area\_sq\_ft to "struSFmn"
* [ ] Add a new field to allstructures\_estsf with the name "struSFrm" (Type = Double). Populate it as follows:
  * For parcels where the count of structures is less than or equal to 2 (strucount <= 2), calculate struSFrm as struSFrm = 0.
  * For parcels where the count of structures is equal to 3 (strucount = 3), calculate struSFrm as struSFrm = \[struSFsum] - \[struSFmx] - \[struSFmn].
  * For parcels where the count of structures is greater than 3 (strucount > 3), calculate struSFrm as struSFrm = (\[struSFsum] - \[struSFmx] - \[struSFmn]) / (\[strucount] - 2)
* [ ] Eliminate all fields from allstructures\_estsf attribute table but:
  * parloc\_id
  * strucount
  * struSFsum
  * struSFmx
  * struSFmn
  * struSFrm
* [ ] Add allstructures\_estsf as a table to ADU-Analytical-Tool\_Spatial-Inputs.gdb.
