---
description: Is there room on the parcel to build a new accessory structure?
---

# Accessory-New

{% hint style="info" %}
[https://gis.stackexchange.com/questions/177518/calculating-setbacks-of-parcel-using-arcgis-for-desktop](https://gis.stackexchange.com/questions/177518/calculating-setbacks-of-parcel-using-arcgis-for-desktop)
{% endhint %}

#### Identify Parcel Geometry

* Parcel land area \[Source: Land Parcel Database, `lot_areaft`]
* Parcel front, side, rear segments <mark style="background-color:blue;">\[Calculated with parcel geometry]</mark>
* Lot frontage <mark style="background-color:blue;">\[Calculated with parcel geometry]</mark>
  * <mark style="background-color:yellow;">**Is this actually needed?**</mark>** **&#x20;
* Lot depth <mark style="background-color:blue;">\[Calculated with parcel geometry]</mark>
  * <mark style="background-color:yellow;">**Is this actually needed?**</mark>** **&#x20;

#### Identify Parcel Land Area, factoring setbacks

* <mark style="background-color:yellow;">**Need Land Use to confirm setbacks**</mark>
  * <mark style="background-color:yellow;">**In Outstanding Questions;**</mark> [<mark style="background-color:yellow;">**setbacks in Airtable**</mark>](../../../policy/assumptions-and-policy/citywide-dimensional-requirements.md)<mark style="background-color:yellow;">****</mark>
  * <mark style="background-color:yellow;">**Also: Is there a setback that will just apply to ADUs? Or in area of the parcel where ADUs may only be constructed?**</mark>
* Front setback: Remove parcel frontage x Setback (Or could we just do this spatially, as we might with a flood zone?)
* Side setbacks:&#x20;
* Rear setback:

