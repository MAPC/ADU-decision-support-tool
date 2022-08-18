# 2. Parcel-level Exclusions

The **Parcel-level Exclusions** inputs collectively describe characteristics of parcels that yield a parcel ineligible for an ADU, regardless of whether that parcel is located within the Effective ADU Boundary. In contrast with ADU Exclusions, Parcel-level Exclusions are not a function of where in the Study Municipality a given parcel is located; in theory, the parcel could be moved to a different area within the municipality and would remain ineligible due to the characteristics inherent to that parcel and its associated structures.

As with the ADU Boundary and ADU Exclusions layers, Parcel-level Exclusions are determined by the policy under consideration. There are two main types of inputs for parcel-level exclusions:

* Excluding Features (Points, Lines, Polygons): Parcels are excluded from the analysis if an excluding feature is present on the parcel. For example, a user could introduce point data defining locations of historical buildings, and exclude all parcels with historical buildings from the analysis.
* Excluded Parcel IDs: Parcels are excluded from the analysis if they have a Parcel ID (parloc\_id) that matches a Parcel ID in the Excluded Parcels table. In this manner, users can specify parcels that should be excluded due to tabular attributes, such as having a Property Type Classification Code other than 101 (Single-family Residential). Users can also specify parcels that should be excluded due to the presence of an excluding feature, in cases where spatial data for that feature does not exist. For example, if only one ADU is allowed on a parcel, users can list all the Parcel IDs where an ADU has already been permitted, and exclude all parcels with existing ADUs from the analysis.&#x20;

The pages linked below provide instructions for the preparation of the four excluding layers: Excluding Points, Excluding Lines, Excluding Polygons, and Excluded Parcel IDs.  If the policy does not reference exclusions of this kind, no inputs need to be created. The preexisting excl\_points, excl\_lines, excl\_polygons, and excl\_parcels Feature Classes may be used instead.

{% content-ref url="2-1.-excluding-points.md" %}
[2-1.-excluding-points.md](2-1.-excluding-points.md)
{% endcontent-ref %}

{% content-ref url="2-2.-excluding-lines.md" %}
[2-2.-excluding-lines.md](2-2.-excluding-lines.md)
{% endcontent-ref %}

{% content-ref url="2-3.-excluding-polygons.md" %}
[2-3.-excluding-polygons.md](2-3.-excluding-polygons.md)
{% endcontent-ref %}

{% content-ref url="2-4.-excluded-parcel-ids.md" %}
[2-4.-excluded-parcel-ids.md](2-4.-excluded-parcel-ids.md)
{% endcontent-ref %}





****
