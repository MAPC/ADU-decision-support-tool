# For Type 3 ADUs

## Building Footprint Lookup Table

{% hint style="warning" %}
\[Add something about building stories assumption]
{% endhint %}

1. Retrieve data on the size of existing accessory buildings in the Study Municipality. The analysis will require the following information, at the parcel level:
   1. Count of existing accessory buildings (
   2. &#x20;
2. Retrieve spatial data for the building footprints in the Study Municipality. If spatial data on building footprints exists locally, review the attribute table to confwe recommend sourcing parcel data from the MassGIS Building Structures (Rooftops) layer, available for download at [https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-](https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-)
3. Add the building footprints spatial data to ADUTool.gdb, titled "Structures."
4. If the Minimum Size of a Type 3 ADU (aduSFmn3) for the policy under consideration exceeds 150 square feet (the area minimum for the statewide database), discard any geometry where the building footprint area (AREA\_SQ\_FT) is less than this minimum. Title the file with the remaining structures, structures\_ov\[XX]sf, where XX is equal to aduSFmn3.
5. Execute a spatial join to relate the building footprints spatial data to the parcel data, using:
   1. Target Features = structures\_ov\[XX]sf
   2. Join Features = ZoneParcels
   3. Output Feature Class = **structures\_ov\[XX]sf\_joinZP**
      1. _Do not keep all target parcels_
   4. Join Operation = JOIN\_ONE\_TO\_MANY
   5. Execute a dissolve, using:

* Input Features = structures\_ov\[XX]sf\_joinZP
* Output Feature Class = **structures\_ov\[XX]sf\_joinZP\_Dis**
* Dissolve Field(s) = parloc\_id
* Statistics Field(s)
*
  * AREA\_SQ\_FT as a COUNT ("**COUNT\_AREA\_SQ\_FT**")
  * AREA\_SQ\_FT as a SUM ("**SUM\_AREA\_SQ\_FT**")
  * AREA\_SQ\_FT as a MAX ("**MAX\_AREA\_SQ\_FT**")
  * AREA\_SQ\_FT as a MIN ("**MIN\_AREA\_SQ\_FT**")
  * **NOTE: This process is automated in Catilin's code, but without the summary values.**

1. Open **structures\_ov\[XX]sf\_joinZP\_Dis** and a new field (Double) with the name "**REM\_AREA\_SQ\_FT**"
2. In **structures\_ov\[XX]sf\_joinZP\_Dis**, add the following values to the **REM\_AREA\_SQ\_FT** field:
3.
   * For parcels where COUNT\_AREA\_SQ\_FT =< 2: Calculate REM\_AREA\_SQ\_FT as REM\_AREA\_SQ\_FT = 0
   * For parcels where COUNT\_AREA\_SQ\_FT = 3: Calculate REM\_AREA\_SQ\_FT as REM\_AREA\_SQ\_FT = SUM\_AREA\_SQ\_FT - MAX\_AREA\_SQ\_FT - MIN\_AREA\_SQ\_FT.
   * For parcels where COUNT\_AREA\_SQ\_FT > 3: Calculate REM\_AREA\_SQ\_FT as NULL.
4. Clean up **structures\_ov\[XX]sf\_joinZP\_Dis, by:**
5.
   * Retitling fields:
   *
     * COUNT\_AREA\_SQ\_FT to "**StrCount**" (Short Integer)
     * SUM\_AREA\_SQ\_FT to "**StrSumSF**" (Double)
     * MAX\_AREA\_SQ\_FT to "**StrMxSF**" (Couble)
     * MIN\_AREA\_SQ\_FT to "**StrMnSF**" (Double)
     * REM\_AREA\_SQ\_FT to "**StrRmSF**"
   * Eliminating all fields but parloc\_id and StrCount, StrSumSF,StrMxSF,StrMnSF, and StrRmSF.
6. Join structures\_ov\[xx]sf\_joinZP\_Dis back to ZoneParcels using the parloc\_id field.
