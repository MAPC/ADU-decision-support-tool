# For Type 3 ADUs

### Create Structures Lookup Table

1. Retrieve spatial data for the building footprints in the Study Municipality. If spatial data on building footprints does not exist locally, we recommend sourcing parcel data from the MassGIS Building Structures (Rooftops) layer, available for download at [https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-](https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-)
2. Add the building footprints spatial data to ADUTool.gdb, titled "structures\_poly\_\[muniID]," replacing \[muniID] with the Municipal ID for the Study Municipality.
3. If the Minimum Size of a Type 3 ADU (aduSFmn3) exceeds 300 square feet, discard any geometry where the building footprint area (AREA\_SQ\_FT) is less than this minimum. Title the file with the remaining structures, **structures\_poly\_\[muniID]\_ov\[XX]sf**, where XX is equal to 3ADUMn/StrStor.
4. Execute a spatial join, using:

* Target Features = structures\_poly\_\[muniID]\_ov\[XX]sf
* Join Features = ZoneParcels
* Output Feature Class = **structures\_ov\[XX]sf\_joinZP**
* _Do not keep all target parcels_
* Join Operation = JOIN\_ONE\_TO\_MANY

1. Execute a dissolve, using:

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
