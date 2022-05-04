# 3. Effective ADU Boundary

## Assemble Effective Zone Boundary ("EffADUBoudary")

### 3a.  Assemble the ADU Boundary input **("ADUBoundary")**

{% hint style="info" %}
The **ADU Boundary** layer delineates the area _outside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted.&#x20;

The ADU Boundary layer will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a zoning district, areas within 1/2-mile of transit stations, or a combination of factors. If the policy does not reference a specific boundary, the ADU Boundary layer should be defined using the boundary of the Study Municipality.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define the ADU boundary. Retrieve and/or create the data layer(s).&#x20;
2. If working with multiple data layers, merge them into a single layer. Produce a single-part polygon, where the enclosed area represents geography where ADUs _may be_ permitted.
3. Export the resulting file to ADUTool.gdb, titled "ADUBoundary," also adding the file back to ArcMap for further processing.

### **3b.  Assemble the Categorical Spatial Exclusions input ("ADUExclusions")**

{% hint style="info" %}
The **Categorical Spatial Exclusions** layer delineates areas _inside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted. In general, the areas comprising the Spatial Exclusions layer will be smaller than the areas comprising the ADU Boundary layer.

As with the ADU Boundary layer, the Spatial Exclusions layer will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a historic district or flood zones; it could also (or additionally) be defined by proximity to certain features, such as the area within 100 feet of a particular zoning district. If the policy does not reference specific spatial exclusions, the Spatial Exclusions layer does not need to be created.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all Spatial Exclusions. Retrieve and/or create the data layer(s).&#x20;
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. Buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer the polygon geometries to expand them by the policy-mandated distance.
4. If working with multiple data layers, merge them into a single layer. Produce a single-part polygon, where the enclosed area represents geography where ADUs _are not_ permitted.
5. Export the resulting file to ADUTool.gdb, titled "ADUExclusions," also adding the file back to ArcMap for further processing.

### **3c.  Combine the ADU Boundary and Spatial Exclusions Layer ("EffADUBoundary")**

{% hint style="info" %}
The **Effective ADU Boundary** layer is the ADU Boundary layer (Step 4a), less the areas defined in the Spatial Exclusions layer (Step 4b). Parcels with centroids in this boundary will continue to be evaluated for an ADU, while parcels with centroids outside of this boundary will be excluded from the analysis.
{% endhint %}

_If an Advanced ArcGIS License is available to you:_&#x20;

1. Use the Erase tool to eliminate areas in the Spatial Exclusions layer ("Erase Features") from the ADU Boundary ("Input Feature".)
2. Export the resulting file to ADUTool.gdb, with the title, "EffADUBoundary."

_If an Advanced ArcGIS License is not available to you:_&#x20;

1. Dissolve the ADU Boundary layer into a single feature class.
2. Dissolve the Spatial Exclusions layer into a single feature class.
3. Use the Union tool to consolidate two dissolved layers into a multi-part polygon.&#x20;
4. Discard any geometry in the resulting multi-part polygon, using the FID\_ADUExc field created through the union. (Geometry, where the FID\_ADUExc field is not equal to -1, should be eliminated.)
5. Export the resulting file to ADUTool.gdb, titled "EffADUBoundary."
