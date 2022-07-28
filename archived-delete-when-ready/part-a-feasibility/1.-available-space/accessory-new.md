---
description: Is there room on the parcel to build a new accessory structure?
---

# Accessory-New

### <mark style="background-color:orange;">Outstanding Questions (Copied to</mark> [<mark style="background-color:orange;">Proposed Next Steps</mark>](../../proposed-next-steps.md)<mark style="background-color:orange;">)</mark>

* [ ] Will detached ADUs be allowed to be constructed in parcel setbacks?
* [ ] Please confirm that the setbacks recorded in the Minimum Yards - Front, Minimum Yards - Side, and Minimum Yards - Rear [columns in the Airtable](../../assumptions-and-policy/citywide-dimensional-requirements.md) are correct. Will these setbacks be fixed or flexible parameters? For reference, options from Ella on minimum setbacks:
  * No change: Same as underlying lot size&#x20;
  * Potential changes:&#x20;
    * Rear, side, and/or front setbacks are decreased to x, x, and x feet&#x20;
    * No additional setback for ADUs within or attached to non-conforming existing structures&#x20;
* [ ] Is there a front yard setback that will only apply to ADUs? (Put differently, will there be an area of the parcel where ADUs may only be constructed?) This might relate to these options from Ella on yard requirements:
  * No change: None&#x20;
  * Potential changes:
    * If detached is allowed, minimum of x square feet of yard is required

#### For Data Services

* [ ] Data Services needs to devise a method to internally buffer a parcel's front, side, and rear lot lines by their respective setbacks to determine the subarea of the parcel which could theoretically be used for further development.&#x20;

### Identify Parcel Geometry

* [x] Parcel land area \[Source: Land Parcel Database, `lot_areaft`]
* [x] Parcel front, side, rear segments \[Calculated with parcel geometry]
* [x] Lot frontage \[Calculated with parcel geometry]
* [ ] Lot depth \[Calculated with parcel geometry] <mark style="background-color:orange;">**Questions above will resolve whether this actually needed**</mark>&#x20;

### Identify Parcel Land Area, Factoring Setbacks

**Possible Options for Analysis**

{% hint style="info" %}
[https://gis.stackexchange.com/questions/177518/calculating-setbacks-of-parcel-using-arcgis-for-desktop](https://gis.stackexchange.com/questions/177518/calculating-setbacks-of-parcel-using-arcgis-for-desktop)
{% endhint %}

