---
description: The ADU Decision Support tool requires ...
---

# Spatial Inputs

### 1.  Create a Geodatabase for the Analysis

1. Create a file geodatabase for the analysis with the title "ADUTool.gdb."

### 2.  Assemble Base Geography ("AllParcels")

1. Retrieve spatial data for the parcels in the municipality with the draft ADU Bylaw or Ordinance, the "Study Municipality." We recommend sourcing parcel data from the Massachusetts Land Parcel Database, available for download at [https://www.mapc.org/learn/data/#landparceldb](https://www.mapc.org/learn/data/#landparceldb)
2. Discard any parcels not located within the Study Municipality, using the Municipal ID (muni\_id) field.&#x20;
3. _Recommended for faster operation, but not required:_ Eliminate all fields from the parcel data attribute table but the following:
   * Municipal ID (muni\_id)
   * Municipality (muni)
   * MassGIS Parcel ID (parloc\_id)
   * Gross Building Area (bldg\_area)
   * Finished Building Area (res\_area)
   * Lot Area (square feet) (lot\_areaft)
   * Percent Building Coverage (pct\_building)
   * <mark style="color:orange;background-color:blue;">\[Insert list of fields that must be retained.]</mark>
4. Export the resulting file to ADUTool.gdb, titled "AllParcels."

### 3.  Assemble Zoning Data ("Zoning")

{% hint style="info" %}
In the scripted analysis, zoning districts are associated with parcels through a spatial join. This association allows users to vary the parameters of the ADU Bylaw or Ordinance by zoning district.
{% endhint %}

1. Retrieve spatial data for the zoning districts in the Study Municipality.&#x20;
2. Review the zoning data attribute table for the following fields, creating them if they do not exist:
   * Zone Code (zo\_code): Concatenation of muni\_id and zo\_abbr. Formula: muni\_id\&zo\_abbr
     * Municipal ID (muni\_id): Municipality ID, as assigned by MassGIS.
     * Zone Abbreviation (zo\_abbr): Zoning district abbreviation, as it appears in the municipality's zoning by-law.
3. Export the resulting file to ADUTool.gdb, titled "Zoning."

### 4. Assemble Effective Zone Boundary ("EffADUBoudary")

#### 4a.  Assemble the ADU Boundary input **("ADUBoundary")**

{% hint style="info" %}
The **ADU Boundary** layer delineates the area _outside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted.&#x20;

The ADU Boundary layer will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a zoning district, areas within 1/2-mile of transit stations, or a combination of factors. If the policy does not reference a specific boundary, the ADU Boundary layer should be defined using the boundary of the Study Municipality.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define the ADU boundary. Retrieve and/or create the data layer(s).&#x20;
2. IIf working with multiple data layers, merge them into a single layer. Produce a single-part polygon, where the enclosed area represents geography where ADUs _may be_ permitted.
3. Export the resulting file to ADUTool.gdb, titled "ADUBoundary," also adding the file back to ArcMap for further processing.

**4b.  Assemble the Categorical Spatial Exclusions input ("ADUExclusions")**

{% hint style="info" %}
The **Categorical Spatial Exclusions** layer delineates areas _inside of which_ an ADU may not be located, regardless of whether one would otherwise be permitted. In general, the areas comprising the Spatial Exclusions layer will be smaller than the areas comprising the ADU Boundary layer.

As with the ADU Boundary layer, the Spatial Exclusions layer will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a historic district or flood zones; it could also (or additionally) be defined by proximity to certain features, such as the area within 100 feet of a particular zoning district. If the policy does not reference specific spatial exclusions, the Spatial Exclusions layer does not need to be created.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all Spatial Exclusions. Retrieve and/or create the data layer(s).&#x20;
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. Buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer the polygon geometries to expand them by the policy-mandated distance.
4. If working with multiple data layers, merge them into a single layer. Produce a single-part polygon, where the enclosed area represents geography where ADUs _are not_ permitted.
5. Export the resulting file to ADUTool.gdb, titled "ADUExclusions," also adding the file back to ArcMap for further processing.

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
4. Discard any geometry in the resulting multi-part polygon, using the FID\_ADUExc field created through the union. (Geometry, where the FID\_ADUExc field is not equal to -1, should be eliminated.)
5. Export the resulting file to ADUTool.gdb, titled "EffADUBoundary."

### 5. Assemble Parcel-level Exclusions

{% hint style="info" %}
**Parcel-level Exclusions** collectively describe characteristics of parcels that yield a parcel ineligible for an ADU, regardless of whether that parcel is located within the Effective ADU Boundary (Step 4c). In contrast with Categorical Spatial Exclusions, Parcel-level Exclusions are not a function of where a given parcel is located; in theory, the parcel could be moved to a different area within the Study Municipality and would remain ineligible due to the characteristics inherent to that parcel and its associated structures.

As with the ADU Boundary and Spatial Exclusions layers, Parcel-level Exclusions will be determined by the policy under consideration. Parcel-level exclusions may involve spatial features present on the parcel, such as the exclusion of all parcels with a historical building point, but could also involve text or numerical attributes, such as the exclusion of all parcels with non-residential land use. If the policy does not reference specific exclusions, the Parcel Exclusions layer does not need to be created.
{% endhint %}

Review the draft ADU Bylaw or Ordinance and identify the data required to define the Parcel Exclusions. We anticipate five categories of data:

#### 5A. Point geometry, the presence of which renders the parcel ineligible for an ADU.&#x20;

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all excluding point geometry. Retrieve and/or create the data layer(s).
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. If working with multiple data layers, merge them into a single layer. Produce a single feature class, where all points represent features that, if present on a parcel, would yield the parcel ineligible for an ADU.
4. Export the resulting file to ADUTool.gdb, titled "ExcludingPoints."

#### 5B. Line geometry, the presence of which renders the parcel ineligible for an ADU.&#x20;

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all excluding line geometry. Retrieve and/or create the data layer(s).
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. If working with multiple data layers, merge them into a single layer. Produce a single feature class, where all lines represent features that, if present on a parcel, would yield the parcel ineligible for an ADU.
4. Export the resulting file to ADUTool.gdb, titled "ExcludingLines."

**5C. Polygon geometry (buffered points or lines and/or polygons), that, if present above a certain percentage threshold, renders the parcel ineligible for an ADU.**&#x20;

{% hint style="info" %}
In contrast with the point geometry (Step 5a) and line geometry (Step 5b), which are boolean exclusions in the tool (the presence of any point and any line on the parcel results in a parcel exclusion, no matter the feature count or type), the exclusions resulting from polygon geometry may vary depending on the feature coverage and/or type. For example, the tool can differentiate between an exclusion based on >25% coverage by steep slopes and an exclusion based on >50% coverage by wetlands.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all excluding coverage geometry. Retrieve and/or create the data layer(s).
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. If applicable, buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer the polygon geometries to expand them by the policy-mandated distance.
4. Export the resulting file(s) to ADUTool.gdb, with the naming structure "CG\_\[FeatureType]\_notover\[CoverageLimit]pct." For example, if the policy under consideration excluded parcels with 25% of more coverage by steep slopes, the input file might be titled "CG\_Slopes\_notover25pct."&#x20;

#### 5D. Parcel attributes, such as Land Use Code, Lot Size, Principal Building Age, already contained within the existing parcel data.&#x20;

\[TO WRITE]

#### 5E. Parcel attributes, such as the presence of an existing ADU, not contained within the existing parcel data that must be joined to it.

\[TO WRITE]



****
