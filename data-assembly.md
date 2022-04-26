# Data Assembly

## Spatial Data

### Zoning Districts (.shp)

#### Ensure the file has the following attributes:

* ZO\_CODE (Zone Code): Concatenation of MUNI\_ID and ZO\_ABBR. Formula: MUNI\_ID\&ZO\_ABBR
* Supported by:
  * MUNI\_ID (Municipal ID): Municipality ID, as assigned by MassGIS.
  * ZO\_ABBR (Zone Abbreviation): Zoning district abbreviation, as it appears in the municipality's zoning by-law.

> The zoning data will be joined to the parcels using a spatial join, with a "One to One" join operation and a "Have their center in" match option.

### Ordinance **Parameters**
