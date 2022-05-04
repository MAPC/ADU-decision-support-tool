# Data Inputs

{% hint style="danger" %}
From Caitlin's Transition Memo. Not yet edited.
{% endhint %}

Data Inputs: Prepare these in advance

The tool requires the following inputs:

* Parcel spatial dataset with, at a minimum, parcel polygon geometry and one field identifying the zoning at each parcel through a standardized code. Standard Level 3 attributes required for other parts of the analysis, but not the fit test. The analyst may need to manipulate the parcel dataset to identify parcels located in areas relevant to the proposed ADU ordinance(s) which are not reflected by zoning alone. For example, the analyst may wish to add a binary column to the parcel dataset which has a value of “1” if the parcel is within a half mile of a transit area or “0” if the parcel is further than half a mile from a transit station of ADU dimensional requirements differ depending on whether the ADU is within a transit area.&#x20;
  * Option 1 (preferred/supported): From Massachusetts Land Parcel Database, select parcels WHERE (‘muni’ = ‘Muni Name’). Export the selected cells, save as ESRI shapefile, and record file path. This method is preferred because the script tool is currently designed to support the schema of the MA Land Parcel Database.
  * Option 2 (risky but possible reward): Use parcel geometry and attributes from local CAMA database. One reason to use this option would be that the ADU ordinance may involve parcel attributes which are included in detailed CAMA records, but would not be included in the standardized MA Land Parcel Database attributes. However, this option would require the analyst to edit the script and ADU ordinance excel sheet to work properly with the local CAMA parcel data schema.&#x20;
* Streets or “right of way” lines or parcels dataset. At a minimum, their geometry. The tool currently supports spatial data inputs in ESRI shapefile format, but could be easily tweaked by a knowledgeable analyst to read in the data in&#x20;
  * o Option 1: Get vector file from municipality.
  * o Option 2: From Massachusetts Land Parcel Database, select parcels WHERE (‘muni’ = ‘Muni Name’) AND (‘type’ IN (‘ROW’, ‘PRIV\_ROW’, ‘RAIL\_ROW’)). Check for variant right-of-way file types. Export the selected cells, save as ESRI shapefile, and record file path for future reference.
* Table (excel sheet form) documenting the dimensional requirements in each type of municipal zoning. This table should also include the proposed dimensional requirements for an attached or detached ADU in each type of zoning and/or area which can be identified through parcel attributes within the municipality.&#x20;
  * Required zoning dimensional information:
    * ♣ Minimum front setback length, feet
    * ♣ Minimum side setback length, feet
    * ♣ Minimum rear setback length, feet
    * Required ADU dimensional information:
      * ♣ Minimum width in any dimension, feet
      * ♣ Minimum internal dwelling unit area in any dimension, square feet
      * ♣ Minimum distance between a structure on the parcel and detached ADU, feet
* Building roofprint spatial data
* o Web resource listed in spatial data browser: [http://www.mass.gov/anf/research-and-tech/it-serv-and-support/application-serv/office-of-geographic-information-massgis/datalayers/structures.html](http://www.mass.gov/anf/research-and-tech/it-serv-and-support/application-serv/office-of-geographic-information-massgis/datalayers/structures.html)
* o K drive local copy listed in spatial data browser: K:\DataServices\Datasets\MassGIS\Facilities\_Structures
* o Because only building roofprint geometry is needed, there is no reason not to use any comparable alternative. Currently, the script supports ESRI shapefile format.&#x20;
* • Excluded area polygon dataset. Must contain the geometry of any areas which would not be eligible for building new ADUs for example within 100 ft of a wetland, in flood zone, on steep slope, etc. as determined by analysts and planners. The script currently supports ESRI shapefile format.
