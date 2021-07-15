# Parcel Data

## Data

* Massachusetts Land Parcel Database: Parcel geometry and select attributes. Accessed: April 2021. Updated: April 2019.
* 
## **Join Details**

1. Using the Spatial Data Browser, added the MA Land Parcel Database to ArcGIS and used Select by Attribute \(muni\_id = 30\) to select parcels \(11,656\) in Beverly. Exported to BeverlyADU.gdb, named `LPD_Bev`.
2. Joined `ParcelLinkAll` \(parcel data provided by Beverly in April 2021\) to `LPD_Bev` using the `MassGISParcelID` \(for `LPD_Bev`\) and the `LOC_ID` fields \(in `ParcelLinkAll`\), keeping all records.
   1. 11,534 of 11,656 matched. There were no validation errors.
3. Exported to BeverlyADU.gdb, named `LPD_Bev_wCAMA`

**Parcel Data Inventory**: [https://airtable.com/shrVu8TeJHxgFsNHB](https://airtable.com/shrVu8TeJHxgFsNHB)

