# 2. Parcel-level Exclusions

The **Parcel-level Exclusions** inputs collectively describe characteristics of parcels that yield a parcel ineligible for an ADU, regardless of whether that parcel is located within the Effective ADU Boundary. In contrast with ADU Exclusions, Parcel-level Exclusions are not a function of where a given parcel is located; in theory, the parcel could be moved to a different area within the Study Municipality and would remain ineligible due to the characteristics inherent to that parcel and its associated structures.

As with the ADU Boundary and ADU Exclusions layers, Parcel-level Exclusions will be determined by the policy under consideration. There are two main types of inputs for parcel-level exclusions:

* Excluded Parcel IDs: Parcels will be excluded from the analysis if they have a Parcel ID (parloc\_id) that matches a Parcel ID in the Excluded Parcels layer. In this manner, users can specify parcels that should be excluded due to tabular attributes, such as having a Property Type Classification Code other than 101 (Single-family Residential). Users can also specify parcels that should be excluded due to the presence of an excluding feature in cases where spatial data for that feature does not exist. For example, if only one ADU is allowed on a parcel, users can list all the Parcel IDs where an ADU has already been permitted.&#x20;
* Excluding Features (Points, Lines, Polygons): Parcels will be excluded from the analysis if an excluding feature intersects the parcel. For example, the exclusion of all parcels with a historical building point.

The pages linked below provide instructions for the preparation of the four excluding layers: Excluded Parcel IDs, Excluding Points, Excluding Lines, and Excluding Polygons.  If the policy does not reference exclusions of this kind, no inputs need to be created. The preexisting excl\_parcels, excl\_points, excl\_lines, and excl\_polygons Feature Classes may be used instead.

{% content-ref url="2-1.-excluded-parcel-ids.md" %}
[2-1.-excluded-parcel-ids.md](2-1.-excluded-parcel-ids.md)
{% endcontent-ref %}

{% content-ref url="2-2.-excluding-points.md" %}
[2-2.-excluding-points.md](2-2.-excluding-points.md)
{% endcontent-ref %}

{% content-ref url="2-3.-excluding-lines.md" %}
[2-3.-excluding-lines.md](2-3.-excluding-lines.md)
{% endcontent-ref %}

{% content-ref url="2-4.-excluding-polygons.md" %}
[2-4.-excluding-polygons.md](2-4.-excluding-polygons.md)
{% endcontent-ref %}





****
