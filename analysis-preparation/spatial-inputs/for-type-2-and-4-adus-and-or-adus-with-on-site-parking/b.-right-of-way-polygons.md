# B. Right-of-Way Polygons

{% hint style="danger" %}
From Caitlin's Transition Memo. Not yet edited.
{% endhint %}

* Streets or “right of way” lines or parcels dataset. At a minimum, their geometry. The tool currently supports spatial data inputs in ESRI shapefile format, but could be easily tweaked by a knowledgeable analyst to read in the data in&#x20;
  * o Option 1: Get vector file from municipality.
  * o Option 2: From Massachusetts Land Parcel Database, select parcels WHERE (‘muni’ = ‘Muni Name’) AND (‘type’ IN (‘ROW’, ‘PRIV\_ROW’, ‘RAIL\_ROW’)). Check for variant right-of-way file types. Export the selected cells, save as ESRI shapefile, and record file path for future reference.
