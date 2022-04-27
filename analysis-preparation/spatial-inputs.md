# Spatial Inputs

### <mark style="background-color:blue;">Overview</mark>

<mark style="background-color:blue;">**The ADU Decision Support tool requires**</mark>&#x20;

### <mark style="background-color:blue;">1.  Create an Analysis Geodatabase</mark>

### 2.  Assemble Base Geography ("AllParcels")

1. Download parcel data for the municipality with the draft ADU Bylaw or Ordinance, the "study municipality." We recommend sourcing parcel data from the Massachusetts Land Parcel Database, available for download at [https://www.mapc.org/learn/data/#landparceldb](https://www.mapc.org/learn/data/#landparceldb)
2. Discard any parcels not located within the study municipality, using the Municipal ID (muni\_id) field.&#x20;
3. _Recommended for faster operation, but not required:_ Eliminate all fields but the following:
   * Municipal ID (muni\_id)
   * Municipality (muni)
   * MassGIS Parcel ID (parloc\_id)
   * <mark style="background-color:blue;">\[Insert list of fields that must be retained.]</mark>
4. Export the resulting file to the analysis geodatabase, with the title, "AllParcels."

### <mark style="background-color:blue;">3.  Assemble Zoning Data ("Zoning")</mark>

1\.&#x20;

#### Ensure the file has the following attributes:

* ZO\_CODE (Zone Code): Concatenation of MUNI\_ID and ZO\_ABBR. Formula: MUNI\_ID\&ZO\_ABBR
  * MUNI\_ID (Municipal ID): Municipality ID, as assigned by MassGIS.
  * ZO\_ABBR (Zone Abbreviation): Zoning district abbreviation, as it appears in the municipality's zoning by-law.

> Automated: The zoning data will be joined to the parcels using a spatial join, with a "One to One" join operation and a "Have their center in" match option.

#### **Ensure the file is named, "Zoning." Export to Geodatabase.**

### 4. Assemble &#x20;

#### 4a.  Assemble Spatial Extent **("ADUBoundary")**

{% hint style="info" %}
The Spatial Extent layer delineates the ADU Boundary, the area outside of which an ADU may not be located, regardless of whether it would otherwise be permitted.&#x20;

The Spatial Extent layer will be determined by the policy under consideration. It may consist of one or more areas within the municipality, such as the area defined by a zoning district, areas within 1/2-mile of transit stations, or a combination of factors. If the policy does not reference a specific boundary, the Spatial Extent layer should be defined using the boundary of the study municipality.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define the ADU boundary.&#x20;
2. If needed, merge the data layer(s) to produce a single-part polygon, where the enclosed area represents geography where ADUs may be permitted.
3. Export the resulting file to the Analysis Geodatabase, with the title, "ADUBoundary."

**4b.  Assemble Categorical Spatial Exclusions ("ADUExclusions")**

{% hint style="info" %}
The Spatial Exclusions layer delineates areas within which an ADU may not be located, regardless of whether it would otherwise be permitted. In general, the areas comprising the Spatial Exclusions layer will be smaller than the areas comprising the Spatial Extent layer.

As with the Spatial Extent layer, the Spatial Exclusions layer will be determined by the policy under consideration. It may also consist of one or more areas within the municipality, such as the area defined by a historic district or flood zones. It could also or additionally be defined by proximity to certain features, such as the area within 100 feet of a particular zoning district. If the policy does not reference specific spatial exclusions, the Categorical Spatial Exclusions layer does not need to be created.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define Spatial Exclusions.&#x20;
2. Buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer polygon geometries to expand them by the relevant distance.
3. If needed, merge the data layer(s) to produce a single-part polygon, where the enclosed area represents geography where ADUs are not permitted.
4. Export the resulting file to the Analysis Geodatabase, with the title, "ADUExclusions."

**4c.  Combine the Spatial Extent and Spatial Exclusions Layer ("EffADUBoundary")**

{% hint style="info" %}
The Effective ADU Boundary layer is the ADU Boundary, less the areas defined in the Spatial Exclusions layer. Parcels with centroids in this boundary will continue to be evaluated for an ADU, while parcels with centroids outside of this boundary will be excluded from the analysis.
{% endhint %}

1. If an Advanced GIS License is available to you: Use the [Erase](https://desktop.arcgis.com/en/arcmap/latest/tools/analysis-toolbox/erase.htm#L\_) tool to eliminate areas in the Spatial Exclusions layer ("Erase Features") from the ADU Boundary ("Input Feature".)
2. If an Advanced GIS License is not available to you:&#x20;
   1. Use the Dissolve tool to bring the Spatial Exclusions Layer and the ADU Boundary layer, respectively, into a single feature class.
   2. Use the Union tool to consolidate layers into a multi-part polygon.&#x20;
   3. In the resulting file, discard any geometry where FID\_ADUExc is not equal to -1.
3. Export the resulting file to the Analysis Geodatabase, with the title, "EffADUBoundary."

### 5. Assemble Parcel-level Exclusions

{% hint style="info" %}
Parcel-level Exclusions are characteristics of individual parcels that yield them ineligible for an ADU, regardless of their location in the municipality. May need to attach features. If you picked up the parcel and move it, it would still have this attribute. Parcel-level exclusions are attributes of the parcel itself.
{% endhint %}

****
