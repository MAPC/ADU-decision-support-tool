# ADU Type 2

<details>

<summary>Compile Inputs and Add to ArcMap</summary>

#### Tabular Data

* Base Zoning Parameters table with:
  * Zone Code
  * ADU Permitted
  * Front Setback
  * Side Setback
  * Rear Setback
  * Max Setback (Greatest of Front, Side, and Rear)
  * Min Setback (Least of Front, Side, and Rear)

#### Spatial Data

* Parcel Data
* Zoning Data
* Unbuildable Area(s)
  * Building Roofprints
  * Existing Impervious Surfaces

</details>

<details>

<summary>Join Parcel Data with Zoning Data to Produce [FILE NAME]</summary>

* Execute a Spatial Join with the following selections:
  *

</details>

<details>

<summary>Join [FILE NAME] with Base Zoning Parameters</summary>



</details>

<details>

<summary>Internally Buffer Parcel Data to Produce [FILE NAME]</summary>

* Add the ArcMap Buffer Wizard to ArcMap ([Instructions here](https://support.esri.com/en/technical-article/000011497))
* Use the Buffer Wizard with the following selections:
  *   Page 1:

      * The features of a layer: Parcel Data
      * \[X] Use only the selected features

      &#x20;



</details>

####



