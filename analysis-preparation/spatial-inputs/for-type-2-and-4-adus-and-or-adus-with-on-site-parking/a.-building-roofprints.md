# A. Building Roofprints

{% hint style="info" %}
For Type 2 and 4 ADUs, which each involve construction beyond the existing parcel structures, data with the location of existing structures is required as an input. Without this information, the tool could erroneously assume an ADU fits on the parcel, but on top of an existing structure. The same input is required to ensure that ADU parking is not located on top of an existing structure.
{% endhint %}

1. Retrieve spatial data for the building roofprints in the Study Municipality. We recommend sourcing this data from the MassGIS Building Structures layer, available for download at [https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-](https://www.mass.gov/info-details/massgis-data-building-structures-2-d#downloads-)
2. Add the downloaded spatial data to ADUTool.gdb, titled "all\_structures."
