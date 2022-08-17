# 2. ADU Exclusions

The **ADU Exclusions** input delineates areas _inside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted. In general, the areas comprising the ADU Exclusions layer will be smaller than the areas comprising the ADU Boundary layer.

As with the ADU Boundary input, the ADU Exclusions input will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a historic district or flood zones; it could also (or additionally) be defined by proximity to certain features, such as the area within 100 feet of a particular zoning district. If the policy does not reference specific spatial exclusions, the ADU Exclusions input does not need to be created. The preexisting "aduexclusions" Feature Class may be used instead.

#### Input Preparation

* [ ] Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all Categorical Spatial Exclusions. Retrieve and/or create the data layer(s).&#x20;
* [ ] If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
* [ ] Buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer the polygon geometries to expand them by the policy-mandated distance.
* [ ] If working with multiple data layers, merge them into a single layer. Then, produce a **single-part polygon**, where the enclosed area represents geography where ADUs _are not_ permitted. **The layer must contain a field "adu\_excl" (Data Type: Short, Suggested Alias: ADU Exclusions) populated with a value of "1".**

{% hint style="info" %}
Blank and example "aduexclusions" layers are available within the ADU-Analytical-Tool\_Spatial-Inputs.gdb file, titled, "aduexclusions" and "ex\_aduexclusions," respectively.
{% endhint %}

* [ ] Export the resulting file to ADU-Analytical-Tool\_Spatial-Inputs.gdb, titled "aduexclusions."

### ****
