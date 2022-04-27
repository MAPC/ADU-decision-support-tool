# Data Preparation

## Spatial Data

#### <mark style="background-color:blue;">1.  Create an Analysis Geodatabase</mark>

#### 2.  Assemble Base Geography ("AllParcels")

1. Download parcel data for the study municipality. Our recommendation is to source this data from the Massachusetts Land Parcel Database, available for download here: [https://www.mapc.org/learn/data/#landparceldb](https://www.mapc.org/learn/data/#landparceldb)
2. Eliminate any parcels not located within the study municipality. Our recommendation is to do so using the Municipal ID ("muni\_id") field.&#x20;
3. _Recommended for faster operation, but not required:_ Eliminate all fields but the following:
   1. Municipal ID ("muni\_id")
   2. Municipality ("muni")
   3. MassGIS Parcel ID ("parloc\_id")
   4. <mark style="background-color:blue;">\[Insert list of fields that must be retained.]</mark>
4. Export the resulting file to the analysis geodatabase, with the title, "AllParcels."

#### 3.  Assemble Spatial Extent&#x20;

{% hint style="info" %}
The Spatial Extent layer delineates the boundary outside of which an ADU may not be located, regardless of whether it would otherwise be allowable to construct. The Spatial Extent layer could be comprised of one or more sub-areas in the municipality, such as a zoning district or districts, the area within 1/2-mile of transit stations, or a combination of factors. If the policy under consideration does not reference a specific boundary, the Spatial Extent layer will be the municipal boundary.
{% endhint %}

1. Review the ADU Bylaw and identify the data layers required to delineate the ADU boundary. Merge these layers as needed to produce a single-part polygon, where the enclosed area represents geography where ADUs may be allowable.
2. Export the resulting file to the Analysis Geodatabase, with the title, "ADUBoundary."

**4.  Assemble Categorical Spatial Exclusions**

{% hint style="info" %}
The Spatial Exclusions layer delineates areas where&#x20;
{% endhint %}

**Configure Parameter Geography**

### Zoning Districts (.shp)

#### Ensure the file has the following attributes:

* ZO\_CODE (Zone Code): Concatenation of MUNI\_ID and ZO\_ABBR. Formula: MUNI\_ID\&ZO\_ABBR
  * MUNI\_ID (Municipal ID): Municipality ID, as assigned by MassGIS.
  * ZO\_ABBR (Zone Abbreviation): Zoning district abbreviation, as it appears in the municipality's zoning by-law.

> Automated: The zoning data will be joined to the parcels using a spatial join, with a "One to One" join operation and a "Have their center in" match option.

#### **Ensure the file is named, "Zoning." Export to Geodatabase.**

### **Parameters Table**
