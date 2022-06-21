# ADU Type 2

<details>

<summary>Compile Inputs and Add to ArcMap</summary>

#### Tabular Data

* Base Zoning Parameters (zoning\_base\_parameters) table with:
  * Zone Code (zo\_code)
  * ADU Permitted (adu\_perm)
  * Front Setback (frStbk)
  * Side Setback (siStbk)
  * Rear Setback (reStbk)
  * Maximum Setback - Greatest of Front, Side, and Rear (mxStbk)
  * Minimum Setback - Least of Front, Side, and Rear (mnStbk)

#### Spatial Data

* Parcel Data (all\_parcels)
* Zoning Data (zoning\_base)
* Unbuildable Area(s)
  * Building Roofprints (all\_structures)
  * Existing Impervious Surfaces

</details>

<details>

<summary>Join Parcel Data with Zoning Data to Produce all_parcels_sjoin_zoning_base</summary>

* Execute a **Spatial Join** with the following selections:
  * Target Features: all\_parcels
  * Join Features: zoning\_base
  * Output Feature Class: all\_parcels\_sjoin\_zoning\_base
  * Join Operation: Join One to One
  * Match Option: Have Their Center In
* Use **Select by Attributes** on Type of Parcel (poly\_typ) to select parcels where the Type of Parcel is not "FEE."
* Use the **Field Calculator** to change the Zone Code for the selected parcels to "NOZONE."

</details>

<details>

<summary>Join all_parcels_sjoin_zoning_base with Base Zoning Parameters (zoning_base_parameters)</summary>

* Execute a **Join** using the zo\_code field, keeping all records
* Export the file to the geodatabase, with the title **all\_parcels\_all\_zoning**

</details>

<details>

<summary>Add Possible Parcels Field to <strong>all_parcels_all_zoning</strong></summary>

* Field Name: possparcel, Integer
* Use **Select by Attributes** to select parcels where: `luc_adj_1='101' AND adu_perm =1`
* Use the Field Calculator to change possparcel for the selected parcels to 1 and the unselected parcels to 0.

</details>

<details>

<summary>Internally Buffer Parcel Data to Produce all_parcels_all_zoning_mnStbk</summary>

* Add the ArcMap Buffer Wizard to ArcMap ([Instructions here](https://support.esri.com/en/technical-article/000011497))
* Use the Buffer Wizard with the following selections:
  * Page 1:
    * The features of a layer: all\_parcels\_all\_zoning
    * \[X] Use only the selected features
  * Page 2:
    * Based on a distance from an attribute: mnStbk
  * Page 3:
    * Dissolve barriers between: No
    * Create buffers to they are: Only inside the polygon(s)
    * In a new layer: all\_parcels\_all\_zoning\_mnStbk

</details>

<details>

<summary>Execute a Union with the Buffered Setback and Structures</summary>

* Input Features:
  * all\_structures
  * all\_parcels\_all\_zoning\_mnStbk
* Output Feature Class: mnStbk\_structures\_union

</details>

<details>

<summary>Execute a Union with </summary>

* Input Features:
  * all\_structures
  * all\_parcels\_all\_zoning\_mnStbk

<!---->

* Output Feature Class: mnStbk\_structures\_parcels\_union

</details>

<details>

<summary>Split Multipart to Singlepart Polygons</summary>

singlepart\_union

</details>

<details>

<summary>Discard Building, Setback Parcels</summary>

Add Field: ShapeTy (Type: Text)

Identify Structures: FID\_all\_structures >0, label them 'ROOF'

</details>

<details>

<summary>Add Area and Perimeter Fields to singlepart_union</summary>

* area\_sf (Double), populate with Calculate Geometry
* perim\_f (Double), populate with Calculate Geometry
* ppscore (Double), populate with (12.56637 \* \[area\_sf])/( \[perim\_f] \* \[perim\_f] )

</details>

#### ## NEED TO MAKE SURE ADUS ARE PLACED NEXT TO OR AWAY FROM BUILDINGS



