# 4-4 | Type 4 ADU Test

This model, 4-4 | Type 4 ADU Fit Test, uses the policy parameters recorded in the [zoningedits](../../analysis-preparation/tabular-inputs/#tabular-inputs) Excel spreadsheet to evaluate what parcels meet the eligibility requirements for a Type 4 ADU, that is, an ADU built as a new, detached structure. The model also evaluates which of those parcels are large enough to fit a Type 4 ADU.

### Model Inputs

* Already present in the [zoningedits](../../analysis-preparation/tabular-inputs/) Excel spreadsheet:
  * Minimum Size for a Type 4 ADU (aduSFmn4)
  * Existing Building and ADU Setback Requirement (paduStbk4)
  * Parcel Attribute Requirements:&#x20;
    * Type 4 ADU Permitted (adu4perm)
    * Minimum Size for a Type 4 Principal Building, in GSF (pGSFmn4)
    * Minimum Size for a Type 4 Principal Building, in FSF (pFSFmn4)
  * Parcel Setback Requirements:&#x20;
    * Front (pafrStbk4)
    * Side (pasiStbk4)
    * Rear (pareStbk4)
* Desired Setback Selection (see [Key Assumptions](4-4-or-type-4-adu-test.md#key-assumptions)): Front Setback, Side Setback, or Rear Setback (This selection is made in the model tool parameters dialogue box.)
* possparcels\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../3-or-prepare-spatial-data-for-fit-tests.md))
* relstructures\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../3-or-prepare-spatial-data-for-fit-tests.md))

### Model Outputs

* parcels\_passforadu2 (Geometry and attributes of parcels that have passed through the three Type 4 ADU Fit tests and are likely eligible.)&#x20;

### Key Assumptions

* While the tool is able to apply a different parcel setback for each zoning district and each ADU typology, the tool is not capable of applying different setbacks to each parcel at this time. This means that it cannot correctly render a zoning policy where the parcel front setback differs from the parcel side setback and/or the parcel rear setback. To provide as much flexibility as possible within this limitation, the model tool parameters dialogue box allows a user to define their preferred setback.
* The tool assumes ADUs are one-story tall. This means parcels that might accommodate a two-story ADU may be unnecessarily eliminated.

### Analysis

This model uses the policy parameters recorded in the zoningedits Excel spreadsheet (attached to the parcel data and structure data in the previous step) to evaluate what parcels meet the eligibility requirements for a Type 4 ADU. It does this through a sequence of two tests: one that checks the parcels against required attributes and one that determines buildable areas on the remaining parcels and checks these buildable areas are sufficiently large and compact.

#### Parcel Attribute Test

The first part of the model restricts the Possible Parcels data to only those parcels meeting the parcel attribute requirements.&#x20;

_Model Design_

<figure><img src="../../.gitbook/assets/image (6) (2).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>

#### Buildable Area Test

The second part of the model removes setbacks and existing structures, which have been expanded by the Existing Building and ADU Setback Requirement, from the geometry of the parcels passing through the first test. This removal generates area(s) within the parcel for possible ADU construction:

_Model Design_

{% tabs %}
{% tab title="Generate Parcel Setbacks" %}
<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Generate Structure Buffers" %}
<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Combine Buildable and Unbuildable Area" %}
<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}
{% endtabs %}

These areas are then restricted to those exceeding the minimum size for a Type 4 ADU and to those with shapes that are sufficiently compact. This compactness test uses a [Polsby Popper ](https://en.wikipedia.org/wiki/Polsby%E2%80%93Popper\_test)score; areas that are closer to the minimum size for a Type 4 ADU must have Posby Popper score closer to 1 to pass, while areas that are larger need lower scores. The test used in the analysis is below.

```sql
(area_sf4 <= (aduSFmn4*1.25) And ppscore4 <= '0.95') Or (area_sf4 <= (aduSFmn4*1.5) And ppscore4 <= '0.85') Or (area_sf4 <= (aduSFmn4*1.75) And ppscore4 <= '0.75') Or (area_sf4 <= (aduSFmn4*2.0) And ppscore4 <= '0.5') Or (area_sf4 <= (aduSFmn4*2.25) And ppscore4 <= '0.25') Or (area_sf4 <= (aduSFmn4*2.5) And ppscore4 <= '0.15') Or (area_sf4 <= (aduSFmn4* 3) And ppscore4 <= '0.10')
```

_Model Design_

{% tabs %}
{% tab title="Buildable Area Test, Part 1" %}
<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Buildable Area Test, Part 2" %}
<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}
{% endtabs %}
