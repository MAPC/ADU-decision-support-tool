# 4. Parcel-level Exclusions

## Assemble Parcel-level Exclusions

{% hint style="info" %}
**Parcel-level Exclusions** collectively describe characteristics of parcels that yield a parcel ineligible for an ADU, regardless of whether that parcel is located within the Effective ADU Boundary (Step 4c). In contrast with Categorical Spatial Exclusions, Parcel-level Exclusions are not a function of where a given parcel is located; in theory, the parcel could be moved to a different area within the Study Municipality and would remain ineligible due to the characteristics inherent to that parcel and its associated structures.

As with the ADU Boundary and Spatial Exclusions layers, Parcel-level Exclusions will be determined by the policy under consideration. Parcel-level exclusions may involve spatial features present on the parcel, such as the exclusion of all parcels with a historical building point, but could also involve text or numerical attributes, such as the exclusion of all parcels with non-residential land use. If the policy does not reference specific exclusions, the Parcel Exclusions layer does not need to be created.
{% endhint %}

Review the draft ADU Bylaw or Ordinance and identify the data required to define the Parcel Exclusions. We anticipate five categories of data:

### 4a. Point geometry, the presence of which renders the parcel ineligible for an ADU.&#x20;

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all excluding point geometry. Retrieve and/or create the data layer(s).
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. If working with multiple data layers, merge them into a single layer. Produce a single feature class, where all points represent features that, if present on a parcel, would yield the parcel ineligible for an ADU.
4. Export the resulting file to ADUTool.gdb, titled "ExcludingPoints."

### 4b. Line geometry, the presence of which renders the parcel ineligible for an ADU.&#x20;

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all excluding line geometry. Retrieve and/or create the data layer(s).
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. If working with multiple data layers, merge them into a single layer. Produce a single feature class, where all lines represent features that, if present on a parcel, would yield the parcel ineligible for an ADU.
4. Export the resulting file to ADUTool.gdb, titled "ExcludingLines."

### **4c. Polygon geometry (buffered points or lines and/or polygons), that, if present above a certain percentage threshold, renders the parcel ineligible for an ADU.**&#x20;

{% hint style="info" %}
In contrast with the point geometry (Step 5a) and line geometry (Step 5b), which are <mark style="color:orange;background-color:blue;">\[</mark><mark style="color:orange;background-color:blue;"><mark style="color:orange;">Boolean exclusions]<mark style="color:orange;"></mark> in the tool (the presence of any point and any line on the parcel results in a parcel exclusion, no matter the feature count or type), the exclusions resulting from polygon geometry may vary depending on the feature coverage and/or type. For example, the tool can differentiate between an exclusion based on >25% coverage by steep slopes and an exclusion based on >50% coverage by wetlands.
{% endhint %}

1. Review the draft ADU Bylaw or Ordinance and identify the data layer(s) required to define all excluding coverage geometry. Retrieve and/or create the data layer(s).
2. If applicable, eliminate any features in the data layer(s) that should not result in a parcel exclusion.
3. If applicable, buffer all point and line geometries by the relevant distance to produce polygon geometries. As relevant, buffer the polygon geometries to expand them by the policy-mandated distance.
4. Export the resulting file(s) to ADUTool.gdb, with the naming structure "CG\_\[FeatureType]\_und\[CoverageLimit]pct." For example, if the policy under consideration excluded parcels with 25% of more coverage by steep slopes, the input file might be titled "CG\_Slopes\_und25pct."&#x20;

### 4d. Parcel attributes, such as Land Use Code, that are already present in "all\_parcels"&#x20;

\[TO WRITE]

### 4e. Parcel attributes, such as an existing ADU, that are not present within "all\_parcels" and must be joined to it

\[TO WRITE]



****
