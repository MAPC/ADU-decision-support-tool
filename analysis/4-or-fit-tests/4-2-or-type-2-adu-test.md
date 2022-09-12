# 4-2 | Type 2 ADU Test

This model, 4-2 | Type 2 ADU Fit Test, uses the policy parameters recorded in the [zoningedits](../../analysis-preparation/tabular-inputs/#tabular-inputs) Excel spreadsheet to evaluate what parcels meet the eligibility requirements for a Type 2 ADU, that is, an ADU built as an addition to an existing structure. The model also evaluates which of those parcels are large enough to fit a Type 2 ADU.

### Model Inputs

* Already present in the [zoningedits](../../analysis-preparation/tabular-inputs/) Excel spreadsheet:
  * ADU Size Requirements:&#x20;
    * Minimum Size for a Type 2 ADU (aduSFmn2)
    * Minimum Dimension for a Type 2 ADU (aduDimn2)
  * Parcel Attribute Requirements:&#x20;
    * Type 2 ADU Permitted (adu2perm)
    * Minimum Size for a Type 2 Principal Building, in GSF (pGSFmn2)
    * Minimum Size for a Type 2 Principal Building, in FSF (pFSFmn2)
    * Maximum Expansion of the GSF of a Type 2 Principal Building (pGSFmxe2)
    * Maximum Expansion of the FSF of a Type 2 Principal Building (pFSFmxe2)
  * Parcel Setback Requirements:&#x20;
    * Front (pafrStbk2)
    * Side (pasiStbk2)
    * Rear (pareStbk2)
* Desired Setback Selection (see [Key Assumptions](4-2-or-type-2-adu-test.md#key-assumptions)): Front Setback, Side Setback, or Rear Setback (This selection is made in the model tool parameters dialogue box.)
* possparcels\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../3-or-prepare-spatial-data-for-fit-tests.md))
* relstructures\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../3-or-prepare-spatial-data-for-fit-tests.md))

### Model Outputs

* parcels\_passforadu2 (Geometry and attributes of parcels that have passed through the three Type 2 ADU Fit tests and are likely eligible.)&#x20;

### Key Assumptions

* While the tool is able to apply a different parcel setback for each zoning district and each ADU typology, the tool is not capable of applying different setbacks to each parcel at this time. This means that it cannot correctly render a zoning policy where the parcel front setback differs from the parcel side setback and/or the parcel rear setback. To provide as much flexibility as possible within this limitation, the model tool parameters dialogue box allows a user to define their preferred setback.
* The tool assumes ADUs are one-story tall. This means parcels that might accommodate a two-story ADU may be unnecessarily eliminated.

### Analysis

This model uses the policy parameters recorded in the zoningedits Excel spreadsheet (attached to the parcel data and structure data in the previous step) to evaluate what parcels meet the eligibility requirements for a Type 2 ADU and which of those parcels are large enough to fit a Type 2 ADU. It does this through a sequence of three tests: one that checks the parcels against required attributes, one that determines buildable areas on the remaining parcels and checks these buildable areas are sufficiently large and compact, and one that ensures there is enough depth between the structures and the buildable areas to meet the minimum dimension of a Type 2 ADU.

#### Parcel Attribute Test

The first part of the model restricts the Possible Parcels data to only those parcels meeting the parcel attribute requirements.&#x20;

_Model Design_

![Screenshot of Model 4, Group 1: Type 2 ADU Parcel Attribute Tests. Click to expand.](../../.gitbook/assets/4-1a.png)

#### Buildable Area Test

The second part of the model removes setbacks and existing structures (in other words, unbuildable areas) from the geometry of the parcels passing through the first test. This removal generates area(s) within the parcel for possible ADU construction:

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Sample Output. Dashed lines indicate parcel boundaries; green fill indicates area(s) within the parcel for possible ADU construction.</p></figcaption></figure>

These areas are then restricted to those exceeding the minimum size for a Type 2 ADU and to those with shapes that are sufficiently compact.&#x20;

<figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption><p>Sample Output. Green fill indicates area(s) within the parcel that have been discarded because they are too small.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Sample Output. Yellow fill indicates area(s) within the parcel that have been discarded because they were not sufficiently compact.</p></figcaption></figure>

The compactness test uses a [Polsby Popper ](https://en.wikipedia.org/wiki/Polsby%E2%80%93Popper\_test)score; areas that are closer to the minimum size for a Type 2 ADU must have Posby Popper score closer to 1 to pass, while areas that are larger need lower scores. The test used in the analysis is below.

```sql
(area_sf2 <= (aduSFmn2*1.25) And ppscore2 <= '0.95') Or (area_sf2 <= (aduSFmn2*1.5) And ppscore2 <= '0.85') Or (area_sf2 <= (aduSFmn2*1.75) And ppscore2 <= '0.75') Or (area_sf2 <= (aduSFmn2*2.0) And ppscore2 <= '0.5') Or (area_sf2 <= (aduSFmn2*2.25) And ppscore2 <= '0.25') Or (area_sf2 <= (aduSFmn2*2.5) And ppscore2 <= '0.15') Or (area_sf2 <= (aduSFmn2* 3) And ppscore2 <= '0.10')
```

_Model Design_

{% tabs %}
{% tab title="Generate Parcel Setbacks" %}
![Click to expand](../../.gitbook/assets/4b.png)


{% endtab %}

{% tab title="Combine Buildable Area and Unbuildable Area" %}


![Click to expand](<../../.gitbook/assets/4c (1).png>)
{% endtab %}

{% tab title="Buildable Area Test" %}


![Click to expand](../../.gitbook/assets/4d.png)
{% endtab %}
{% endtabs %}

#### Minimum Dimension Test

The third part of the model evaluates the buildable area(s) surrounding existing structures to make sure they are wide enough to accommodate an ADU. To do so, the model buffers reapplies the All Structures input, this time buffering existing structures by the minimum dimension for a Type 2 ADU, as defined by the aduDimn2 field.

_Model Design_

{% tabs %}
{% tab title="Buffer Structures by Minimum ADU Dimension" %}
<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Part 1. Click to expand.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>Part 2. Click to expand. The earlier model output, buildarea2_passadu2t2_dxpid, is rejoined in two steps.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (3) (1) (2).png" alt=""><figcaption><p>Part 3. Click to expand.</p></figcaption></figure>
{% endtab %}

{% tab title="Minimum Dimension Test" %}
<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}
