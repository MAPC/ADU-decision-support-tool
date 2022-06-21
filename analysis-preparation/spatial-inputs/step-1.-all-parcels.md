# 1. All Parcels

## Assemble Base Geography ("all\_parcels")

1. Retrieve spatial data for the parcels in the municipality with the draft ADU Bylaw or Ordinance, the "Study Municipality." We recommend sourcing parcel data from the Massachusetts Land Parcel Database, available for download at [https://www.mapc.org/learn/data/#landparceldb](https://www.mapc.org/learn/data/#landparceldb)
2. Discard any parcels not located within the Study Municipality, using the Municipal ID (muni\_id) field.&#x20;
3. _Recommended for faster operation, but not required:_ Eliminate all fields from the parcel data attribute table but the following:
   * Municipal ID (muni\_id)
   * Municipality (muni)
   * MassGIS Parcel ID (parloc\_id)
   * Gross Building Area (bldg\_area)
   * Finished Building Area (res\_area)
   * Lot Area (square feet) (lot\_areaft)
   * Percent Building Coverage (pct\_building)
   * <mark style="color:orange;background-color:blue;">\[Insert list of fields that must be retained.]</mark>
4. Export the resulting file to ADUTool.gdb, titled "all\_parcels."

**To Incorporate:**

{% hint style="danger" %}
From Caitlin's Transition Memo. Not yet edited.
{% endhint %}

Data Inputs: Prepare these in advance

The tool requires the following inputs:

* P
  * Option 1 (preferred/supported): From Massachusetts Land Parcel Database, select parcels WHERE (‘muni’ = ‘Muni Name’). Export the selected cells, save as ESRI shapefile, and record file path. This method is preferred because the script tool is currently designed to support the schema of the MA Land Parcel Database.
  * Option 2 (risky but possible reward): Use parcel geometry and attributes from local CAMA database. One reason to use this option would be that the ADU ordinance may involve parcel attributes which are included in detailed CAMA records, but would not be included in the standardized MA Land Parcel Database attributes. However, this option would require the analyst to edit the script and ADU ordinance excel sheet to work properly with the local CAMA parcel data schema.&#x20;

****
