# For Type 3 ADUs

## Building Roofprints Lookup Table

{% hint style="warning" %}
\[Add something about building stories assumption]
{% endhint %}

1. If it has not already been retrieved in an earlier step, retrieve spatial data for the building roofprints in the Study Municipality. We recommend sourcing this data from the MassGIS Building Structures layer, available for download at [https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-](https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-) Add the downloaded spatial data to ADUTool.gdb, titled "all\_structures."
2. If the Minimum Size of a Type 3 ADU (aduSFmn3) for the policy under consideration exceeds 150 square feet (the minimum area for inclusion in the MassGIS layer), discard any geometry where the building roofprint area (area\_sq\_ft) is less than this minimum. Title the file with the remaining structures, structures\_ov\[XX]sf, replacing \[XX] with aduSFmn3.
3. Execute a spatial join to relate the building roofprints spatial data to the parcel data, using:
   * Target Features = structures\_ov\[XX]sf
   * Join Features = all\_parcels
   * Output Feature Class = structures\_ov\[XX]sf\_joinap
     * Uncheck "Keep All Target Parcels"
   * Join Operation = JOIN\_ONE\_TO\_MANY
   * Match Option = HAVE\_THEIR\_CENTER\_IN
4. Open structures\_ov\[XX]sf\_joinap. Execute a dissolve, using:
   * Input Features = structures\_ov\[XX]sf\_joinap
   * Output Feature Class = structures\_ov\[XX]sf\_byparcel
   * Dissolve Fields = parloc\_id
   * Statistics Fields
     * area\_sq\_ft as a Count (count\_area\_sq\_ft)
     * area\_sq\_ft as a Sum (sum\_area\_sq\_ft)
     * area\_sq\_ft as a Max (max\_area\_sq\_ft)
     * area\_sq\_ft as a Min (min\_area\_sq\_ft)
5. Open structures\_ov\[XX]sf\_byparcel. **** Retitle the Statistics Fields from the Dissolve:
   * Retitle count\_area\_sq\_ft as "strucount" (Type = Short Integer)
   * Retitle sum\_area\_sq\_ft as "struSFsum" (Type = Double)
   * Retitle max\_area\_sq\_ft as "struSFmx" (Type = Double)
   * Retitle min\_area\_sq\_ft as "struSFmn" (Type = Double)
6. Add a new field with the name "struSFrm" (Type = Double). Populate it as follows:
   * For parcels where the count of structures is less than or equal to 2 (strucount <= 2), calculate struSFrm as struSFrm = 0
   * For parcels where the count of structures is equal to 3 (strucount = 3), calculate struSFrm as struSFrm = \[struSFsum] - \[struSFmx] - \[struSFmn].
   * For parcels where the count of structures is greater than 3 (strucount > 3), calculate struSFrm as struSFrm = <<mark style="color:orange;background-color:blue;">NULL></mark>
7. Eliminate all fields from structures\_ov\[XX]sf\_byparcel attribute table but:
   * parloc\_id
   * strucount
   * struSFsum
   * struSFmx
   * struSFmn
   * struSFrm
8. Export the attribute table as a File and Personal Geodatabase Table, titled, "table\_structures\_ov\[xx]sf\_byparcel"
9. Join table\_structures\_ov\[XX]sf\_byparcel to possible\_parcels using the parloc\_id field, keeping only matching records.&#x20;
