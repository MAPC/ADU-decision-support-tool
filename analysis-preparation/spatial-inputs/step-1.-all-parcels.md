# 3. All Parcels

The **All Parcels** input comprises all parcels in the Study Municipality.

#### Input Preparation

* [ ] Retrieve spatial data for the parcels in the Study Municipality. We highly recommend sourcing parcel data from the Massachusetts Land Parcel Database, available for download at [https://www.mapc.org/learn/data/#landparceldb](https://www.mapc.org/learn/data/#landparceldb)
* [ ] Discard any parcels not located within the Study Municipality, using the Municipal ID (muni\_id) field.&#x20;
* [ ] Export the resulting file to ADU-Analytical-Tool\_Spatial-Inputs.gdb, titled "allparcels."

{% hint style="info" %}
Blank and example "allparcels" layers are available within the ADU-Analytical-Tool\_Spatial-Inputs.gdb file, titled, "allparcels" and "ex\_allparcels," respectively.
{% endhint %}

Note: If you do not wish to proceed with the Massachusetts Land Parcel Database, the following fields must be present in the parcel data used in the automated analysis:

* MassGIS Parcel ID (parloc\_id)
* Type of Parcel (poly\_type)
* Gross Building Area (bldg\_area)
* Finished Building Area (res\_area)
* <mark style="color:orange;background-color:blue;">\[Insert list of fields that must be retained.]</mark>

****
