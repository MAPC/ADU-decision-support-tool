# 3. Effective ADU Boundary

## Assemble Effective Zone Boundary ("eff\_adu\_boudary")

### 3a.  Assemble the ADU Boundary input **("adu\_boundary")**

{% hint style="info" %}
The **ADU Boundary** input delineates the area _outside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted.&#x20;

The ADU Boundary input will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a zoning district, areas within 1/2-mile of transit stations, or a combination of factors. If the policy does not reference a specific boundary, the ADU Boundary layer should be defined using the boundary of the Study Municipality.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define the ADU boundary. Retrieve and/or create the data layer(s).&#x20;
2. If working with multiple data layers, merge them into a single layer. Produce a single-part polygon, where the enclosed area represents geography where ADUs _may be_ permitted.
3. Export the resulting file to ADUTool.gdb, titled "adu\_boundary," also adding the file back to ArcMap for further processing.

### **3b.  Assemble the Categorical Spatial Exclusions input ("adu\_exclusions")**

{% hint style="info" %}
The **Categorical Spatial Exclusions** input delineates areas _inside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted. In general, the areas comprising the Spatial Exclusions layer will be smaller than the areas comprising the ADU Boundary layer.

As with the ADU Boundary input, the Categorical Spatial Exclusions input will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a historic district or flood zones; it could also (or additionally) be defined by proximity to certain features, such as the area within 100 feet of a particular zoning district. If the policy does not reference specific spatial exclusions, the Categorical Spatial Exclusions input does not need to be created.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all Categorical Spatial Exclusions. Retrieve and/or create the data layer(s).&#x20;
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. Buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer the polygon geometries to expand them by the policy-mandated distance.
4. If working with multiple data layers, merge them into a single layer. Produce a single-part polygon, where the enclosed area represents geography where ADUs _are not_ permitted.
5. Export the resulting file to ADUTool.gdb, titled "adu\_exclusions," also adding the file back to ArcMap for further processing.

### **3c.  Combine the ADU Boundary and Spatial Exclusions Layer ("eff\_adu\_boundary")**

{% hint style="info" %}
The **Effective ADU Boundary** input is the ADU Boundary input (Step 4a), less the areas defined in the Categorical Spatial Exclusions input (Step 4b). Parcels with centroids in this boundary will continue to be evaluated for an ADU, while parcels with centroids outside of this boundary will be excluded from the analysis.
{% endhint %}

_If an Advanced ArcGIS License is available to you:_&#x20;

1. Use the Erase tool to eliminate areas in the Categorical Spatial Exclusions input (adu\_exclusions) from the ADU Boundary (adu\_boundary). Categorical Spatial Exclusions should be defined as the Erase Feature, while the ADU Boundary should be defined as the Input Feature.&#x20;
2. Export the resulting file to ADUTool.gdb, with the title, "eff\_adu\_boundary."

_If an Advanced ArcGIS License is not available to you:_&#x20;

1. Dissolve the ADU Boundary input (adu\_boundary) into a single feature class.
2. Dissolve the Categorical Spatial Exclusions input (adu\_exclusions) into a single feature class.
3. Use the Union tool to consolidate two dissolved layers into a multi-part polygon.&#x20;
4. Discard any geometry in the resulting multi-part polygon, using the FID\_ADUExc field created through the union. (Geometry, where the FID\_ADUExc field is not equal to -1, should be eliminated.)
5. Export the resulting file to ADUTool.gdb, titled "eff\_adu\_boundary."
