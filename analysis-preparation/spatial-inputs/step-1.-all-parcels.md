# 1. All Parcels

## Assemble Base Geography ("AllParcels")

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



****
