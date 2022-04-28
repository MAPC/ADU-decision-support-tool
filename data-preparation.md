---
description: The ADU Decision Support tool requires ...
---

# Spatial Inputs

### 1.  Create a Geodatabase for the Analysis

1. Create a file geodatabase for the analysis, with the title "ADUTool.gdb."

### 2.  Assemble Base Geography ("AllParcels")

1. Retrieve spatial data for the parcels in the municipality with the draft ADU Bylaw or Ordinance, the "study municipality." We recommend sourcing parcel data from the Massachusetts Land Parcel Database, available for download at [https://www.mapc.org/learn/data/#landparceldb](https://www.mapc.org/learn/data/#landparceldb)
2. Discard any parcels not located within the study municipality, using the Municipal ID (muni\_id) field.&#x20;
3. _Recommended for faster operation, but not required:_ Eliminate all fields from the associated attribute table but the following:
   * Municipal ID (muni\_id)
   * Municipality (muni)
   * MassGIS Parcel ID (parloc\_id)
   * <mark style="color:orange;background-color:blue;">\[Insert list of fields that must be retained.]</mark>
4. Export the resulting file to ADUTool.gdb, with the title, "AllParcels."

### 3.  Assemble Zoning Data ("Zoning")

{% hint style="info" %}
In the scripted analysis, zoning districts are associated with parcels through a spatial join. This association allows users to vary the parameters of the ADU Bylaw or Ordinance by zoning district.
{% endhint %}

1. Retrieve spatial data for the zoning districts in the study municipality.&#x20;
2. Review the associated attribute table for the following fields, creating them if they do not exist:
   * Zone Code (zo\_code): Concatenation of muni\_id and zo\_abbr. Formula: muni\_id\&zo\_abbr
     * Municipal ID (muni\_id): Municipality ID, as assigned by MassGIS.
     * Zone Abbreviation (zo\_abbr): Zoning district abbreviation, as it appears in the municipality's zoning by-law.
3. Export the resulting file to ADUTool.gdb, with the title, "Zoning."

### 4. Assemble the Effective Zone Boundary

#### 4a.  Assemble the ADU Boundary input **("ADUBoundary")**

{% hint style="info" %}
The **ADU Boundary** layer delineates the area _outside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted.&#x20;

The ADU Boundary layer will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a zoning district, areas within 1/2-mile of transit stations, or a combination of factors. If the policy does not reference a specific boundary, the ADU Boundary layer should be defined using the boundary of the study municipality.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define the ADU boundary.&#x20;
2. If needed, merge the data layer(s). Produce a single-part polygon, where the enclosed area represents geography where ADUs may be permitted.
3. Export the resulting file to ADUTool.gdb, with the title, "ADUBoundary."

**4b.  Assemble the Categorical Spatial Exclusions input ("ADUExclusions")**

{% hint style="info" %}
The **Categorical Spatial Exclusions** layer delineates areas _inside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted. In general, the areas comprising the Spatial Exclusions layer will be smaller than the areas comprising the ADU Boundary layer.

As with the ADU Boundary layer, the Spatial Exclusions layer will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a historic district or flood zones; it could also (or additionally) be defined by proximity to certain features, such as the area within 100 feet of a particular zoning district. If the policy does not reference specific spatial exclusions, the Spatial Exclusions layer does not need to be created.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all Spatial Exclusions.&#x20;
2. Buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer polygon geometries to expand them by the policy-mandated distance.
3. If needed, merge the data layer(s). Produce a single-part polygon, where the enclosed area represents geography where ADUs are not permitted.
4. Export the resulting file to ADUTool.gdb, with the title, "ADUExclusions."

**4c.  Combine the ADU Boundary and Spatial Exclusions Layer ("EffADUBoundary")**

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
4. Discard any geometry in the resulting multi-part polygon, using the FID\_ADUExc field created through the union. (Geometry where the FID\_ADUExc field not equal to -1 should be eliminated.)
5. Export the resulting file to ADUTool.gdb, with the title, "EffADUBoundary."

### 5. Assemble Parcel-level Exclusions

{% hint style="info" %}
The **Parcel-level Exclusions** layer describes parcels where an ADU may not be located, regardless of their location within the Effective ADU Boundary (Step 4c). In contrast with  May need to attach features. If you picked up the parcel and move it, it would still have this attribute. Parcel-level exclusions are attributes of the parcel itself.

As with the ADU Boundary and Spatial Exclusions layers, Parcel-level Exclusions will be determined by the policy under consideration. Parcel-level exclusions may involve spatial features (for example, parcels with a historical building point) but could also involve tabula



It may also consist of one or more areas within the municipality, such as the area defined by a historic district or flood zones. It could also or additionally be defined by proximity to certain features, such as the area within 100 feet of a particular zoning district. If the policy does not reference specific spatial exclusions, the Categorical Spatial Exclusions layer does not need to be created.
{% endhint %}



****
