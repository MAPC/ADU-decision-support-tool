# For Type 3 ADUs

## Building Roofprints Lookup Table

{% hint style="warning" %}
\[Add something about building stories assumption]
{% endhint %}

1. Retrieve spatial data for the building rootprints in the Study Municipality. We recommend sourcing this data from the MassGIS Building Structures layer, available for download at [https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-](https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-)
2. Add the downloaded spatial data to ADUTool.gdb, titled "Structures."
3. If the Minimum Size of a Type 3 ADU (aduSFmn3) for the policy under consideration exceeds 150 square feet (the minimum area for inclusion in the MassGIS layer), discard any geometry where the building rootprint area (area\_sq\_ft) is less than this minimum. Title the file with the remaining structures, structures\_ov\[XX]sf, replacing \[XX] with aduSFmn3.
4. Execute a spatial join to relate the building rootprints spatial data to the parcel data, using:
   * Target Features = structures\_ov\[XX]sf
   * <mark style="color:orange;background-color:blue;">Join Features = ZoneParcels</mark>
   * Output Feature Class = structures\_ov\[XX]sf\_joinZP
     * _Do not keep all target parcels_
   * Join Operation = JOIN\_ONE\_TO\_MANY
5. Open structures\_ov\[XX]sf\_joinZP. Execute a dissolve, using:
   * Input Features = structures\_ov\[XX]sf\_joinZP
   * Output Feature Class = structures\_ov\[XX]sf\_joinZP\_Dis
   * Dissolve Fields = parloc\_id
   * Statistics Fields
     * area\_sq\_ft as a Count (count\_area\_sq\_ft)
     * area\_sq\_ft as a Sum (sum\_area\_sq\_ft)
     * area\_sq\_ft as a Max (max\_area\_sq\_ft)
     * area\_sq\_ft as a Min (min\_area\_sq\_ft)
6. Open structures\_ov\[XX]sf\_joinZP\_Dis. **** Retitle the Statistics Fields from the Dissolve:
   * Retitle count\_area\_sq\_ft as "strucount" (Type = Short Integer)
   * Retitle sum\_area\_sq\_ft as "struSFsum" (Type = Double)
   * Retitle max\_area\_sq\_ft as "struSFmx" (Type = Double)
   * Retitle min\_area\_sq\_ft as "struSFmn" (Type = Double)
7. Add a new field with the name "struSFrm" (Type = Double). Populate it as follows:
   * For parcels where the count of structures is less than or equal to 2 (strucount =< 2), calculate struSFrm as struSFrm = 0
   * For parcels where the count of structures is equal to 3 (strucount = 3), calculate struSFrm as struSFrm = struSFsum - struSFmx - struSFmn.
   * For parcels where the count of structures is greater than 3 (strucount > 3), calculate struSFrm as struSFrm = <mark style="color:orange;background-color:blue;">NULL</mark>
8. Eliminating all fields from structures\_ov\[XX]sf\_joinZP\_Dis attribute table but:
   * parloc\_id
   * strucount
   * struSFsum
   * struSFmx
   * struSFmn
   * struSFrm
9. <mark style="color:orange;background-color:blue;">Join structures\_ov\[xx]sf\_joinZP\_Dis back to ZoneParcels using the parloc\_id field.</mark>
