# For Type 3 ADUs

## Building Footprint Lookup Table

{% hint style="warning" %}
\[Add something about building stories assumption]
{% endhint %}

1. Retrieve spatial data for the building footprints in the Study Municipality. We recommend sourcing this data from the MassGIS Building Structures layer, available for download at [https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-](https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-)
2. Add the downloaded spatial data to ADUTool.gdb, titled "Structures."
3. If the Minimum Size of a Type 3 ADU (aduSFmn3) for the policy under consideration exceeds 150 square feet (the minimum area for inclusion in the MassGIS layer), discard any geometry where the building footprint area (area\_sq\_ft) is less than this minimum. Title the file with the remaining structures, structures\_ov\[XX]sf, replacing \[XX] with aduSFmn3.
4. Execute a spatial join to relate the building footprints spatial data to the parcel data, using:
   * Target Features = structures\_ov\[XX]sf
   * Join Features = ZoneParcels
   * Output Feature Class = structures\_ov\[XX]sf\_joinZP
     1. _Do not keep all target parcels_
   * Join Operation = JOIN\_ONE\_TO\_MANY
5. Execute a dissolve on structures\_ov\[XX]sf\_joinZP, using:
   * Input Features = structures\_ov\[XX]sf\_joinZP
   * Output Feature Class = structures\_ov\[XX]sf\_joinZP\_Dis
   * Dissolve Field(s) = parloc\_id
   * Statistics Field(s)
     * area\_sq\_ft as a Count (count\_area\_sq\_ft)
     * area\_sq\_ft as a Sum (sum\_area\_sq\_ft)
     * area\_sq\_ft as a Max (max\_area\_sq\_ft)
     * area\_sq\_ft as a Min (min\_area\_sq\_ft)
6. Open **structures\_ov\[XX]sf\_joinZP\_Dis** and a new field (Double) with the name "**REM\_AREA\_SQ\_FT**"
7. In **structures\_ov\[XX]sf\_joinZP\_Dis**, add the following values to the **REM\_AREA\_SQ\_FT** field:
8.
   * For parcels where COUNT\_AREA\_SQ\_FT =< 2: Calculate REM\_AREA\_SQ\_FT as REM\_AREA\_SQ\_FT = 0
   * For parcels where COUNT\_AREA\_SQ\_FT = 3: Calculate REM\_AREA\_SQ\_FT as REM\_AREA\_SQ\_FT = SUM\_AREA\_SQ\_FT - MAX\_AREA\_SQ\_FT - MIN\_AREA\_SQ\_FT.
   * For parcels where COUNT\_AREA\_SQ\_FT > 3: Calculate REM\_AREA\_SQ\_FT as NULL.
9. Clean up **structures\_ov\[XX]sf\_joinZP\_Dis, by:**
10.
    * Retitling fields:
    *
      * COUNT\_AREA\_SQ\_FT to "**StrCount**" (Short Integer)
      * SUM\_AREA\_SQ\_FT to "**StrSumSF**" (Double)
      * MAX\_AREA\_SQ\_FT to "**StrMxSF**" (Couble)
      * MIN\_AREA\_SQ\_FT to "**StrMnSF**" (Double)
      * REM\_AREA\_SQ\_FT to "**StrRmSF**"
    * Eliminating all fields but parloc\_id and StrCount, StrSumSF,StrMxSF,StrMnSF, and StrRmSF.
11. Join structures\_ov\[xx]sf\_joinZP\_Dis back to ZoneParcels using the parloc\_id field.





Retrieve data on existing, accessory buildings in each parcel in the Study Municipality. The analysis will require the following information:

1. Number of Existing, Accessory Buildings on the Parcel (StrCount)
2. For each Existing, Accessory Building: Gross Square Footage (Str\[#]GSF) and/or Finished Square Footage (Str\[#]FSF).
3. Assemble this information in an attribute table that can be joined&#x20;
