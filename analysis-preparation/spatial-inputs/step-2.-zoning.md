# Step 2. Zoning

## Assemble Zoning Data ("Zoning")

{% hint style="info" %}
In the scripted analysis, zoning districts are associated with parcels through a spatial join. This association allows users to vary the parameters of the ADU Bylaw or Ordinance by zoning district.
{% endhint %}

1. Retrieve spatial data for the zoning districts in the Study Municipality.&#x20;
2. Review the zoning data attribute table for the following fields, creating them if they do not exist:
   * Zone Code (zo\_code): Concatenation of muni\_id and zo\_abbr. Formula: muni\_id\&zo\_abbr
     * Municipal ID (muni\_id): Municipality ID, as assigned by MassGIS.
     * Zone Abbreviation (zo\_abbr): Zoning district abbreviation, as it appears in the municipality's zoning by-law.
3. Export the resulting file to ADUTool.gdb, titled "Zoning."



****
