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

* Parcel spatial dataset with, at a minimum, parcel polygon geometry and one field identifying the zoning at each parcel through a standardized code. Standard Level 3 attributes required for other parts of the analysis, but not the fit test. The analyst may need to manipulate the parcel dataset to identify parcels located in areas relevant to the proposed ADU ordinance(s) which are not reflected by zoning alone. For example, the analyst may wish to add a binary column to the parcel dataset which has a value of “1” if the parcel is within a half mile of a transit area or “0” if the parcel is further than half a mile from a transit station of ADU dimensional requirements differ depending on whether the ADU is within a transit area.&#x20;
  * Option 1 (preferred/supported): From Massachusetts Land Parcel Database, select parcels WHERE (‘muni’ = ‘Muni Name’). Export the selected cells, save as ESRI shapefile, and record file path. This method is preferred because the script tool is currently designed to support the schema of the MA Land Parcel Database.
  * Option 2 (risky but possible reward): Use parcel geometry and attributes from local CAMA database. One reason to use this option would be that the ADU ordinance may involve parcel attributes which are included in detailed CAMA records, but would not be included in the standardized MA Land Parcel Database attributes. However, this option would require the analyst to edit the script and ADU ordinance excel sheet to work properly with the local CAMA parcel data schema.&#x20;

****
