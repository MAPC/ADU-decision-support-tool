# 4-1 | Type 1 ADU Test

This model, 4-1 | Type 1 ADU Fit Test, uses the policy parameters recorded in the [zoningedits](../../analysis-preparation/tabular-inputs/#tabular-inputs) Excel spreadsheet to evaluate what parcels meet the eligibility requirements for a Type 1 ADU, that is, an ADU developed within the principal building, without any expansion of that building's foundation.

### Model Inputs

* Already present in the [zoningedits](../../analysis-preparation/tabular-inputs/) Excel spreadsheet:
  * Minimum Size for a Type 1 ADU (aduSFmn1)
  * Parcel Attribute Requirements:&#x20;
    * Type 1 ADU Permitted (adu1perm)
    * Minimum Size for a Type 1 Principal Building, in GSF (pGSFmn1)
    * Minimum Size for a Type 1 Principal Building, in FSF (pFSFmn1)
    * Maximum Share of the Principal Building GSF a Type 1 ADU May Occupy (pGSFmxs1)
    * Maximum Share of the Principal Building FSF a Type 1 ADU May Occupy (pFSFmxs1)
* possparcels\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../3-or-prepare-spatial-data-for-fit-tests.md))

### Model Outputs

* parcels\_passforadu1 (Geometry and attributes of parcels that have passed through the Type 1 ADU Fit tests and are likely eligible.)&#x20;

### Key Assumptions

* None at this time

### Analysis

This model uses the policy parameters recorded in the zoningedits Excel spreadsheet (attached to the parcel data and structure data in the previous step) to evaluate what parcels meet the eligibility requirements for a Type 1 ADU. It does this by restricting the Possible Parcels data to only those parcels meeting the parcel attribute requirements.&#x20;

_Model Design_

{% tabs %}
{% tab title="Prepare Inputs" %}
<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Parcel Attribute Tests" %}
<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Export Results" %}
<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}
{% endtabs %}
