---
description: Is there room inside the principal dwelling for an ADU?
---

# Principal-Existing

<mark style="background-color:orange;">The State of Zoning for Accessory Dwelling Units suggests ADU Ordinances and Bylaws commonly control ADUs by percent of primary unit floor area and/or percent expansion of primary dwelling. We might want to account for these in our analysis.</mark>

### Possible Options for Analysis

<details>

<summary>Large Building by Building Mass</summary>

#### Large Building Square Footage

* Attributes:
  * `Gross Building Area` (LPD)
  * `Finished Building Area` (LPD)&#x20;

#### Large Building Height

* Possible attributes:
  * `STORY_HEIGHT` (CAMA)
  * Number of Stairways: Not available

</details>

<details>

<summary>Large Building by Rooms</summary>

#### More Rooms

* Possible attributes:
  * `Reported Rooms` (LPD)

#### More Bedrooms

* Possible attributes:
  * `NUM_BEDROOM` (CAMA)
    * Challenge: How to address blank values?

<!---->

* Challenge: How to address building-wide counts in multifamily buildings?
  * Average by unit, GSF, or lot area

#### More Bathrooms

* Possible attributes:
  * `NUM_BATH_`  (CAMA)
    * Challenge: How to address blank values?
  * `NUM_HALF_BATH`(CAMA)
    * Challenge: How to address blank values?

</details>

<details>

<summary>Known "Bonus" Space</summary>

#### Unfinished Building Area

* Calculate by subtracting Finished Building Area `res_area from` Gross Building Area `bldg_area`

#### Presence of a Basement

* Calculate by assigning a value of 1 to all properties where `BASEMENT_AREA` exceeds a certain amount.
* Other attributes:
  * `BASEMENT_AREA` (SF)
  * `FIN_BASEMENT` (Units not yet evaluated)
  * `BSMT_GARAGE` (Unknown units)
    * 502 parcels have a value of 1
    * 641 parcels have a value of 2
    * 46 parcels have a value of 3
    * Other values are 4, 5, 42

#### Presence of an Attic

* Not available, but this could be approximated through the `ROOF` field (Null, Flat, versus other types: Bow, Gable, etc.)

#### Presence of an Attached Garage

* Calculate by assigning a value of 1 to all properties where `ATT_GARAGE` exceeds a certain amount.
* Other attributes:
  * `ATT_GARAGE` (SF)
    * More in line with actual SF values, but there are at least 20 parcels with garages less than 100SF.
  * BSMT\_GARAGE (Unknown units)
    * 502 parcels have a value of 1
    * 641 parcels have a value of 2
    * 46 parcels have a value of 3
    * Other values are 4, 5, 42

</details>
