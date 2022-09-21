# 4-3 | Type 3 ADU Test

This model, 4-3 | Type 3 ADU Fit Test, uses the policy parameters recorded in the [zoningedits](../../analysis-preparation/tabular-inputs/#tabular-inputs) Excel spreadsheet to evaluate what parcels meet the eligibility requirements for a Type 3 ADU, that is, an ADU developed within an existing accessory structure, without any expansion of that building's foundation.

### Model Inputs

* Already present in the [zoningedits](../../analysis-preparation/tabular-inputs/) Excel spreadsheet:
  * Minimum Size for a Type 3 ADU (aduSFmn3)
  * Parcel Attribute Requirements:&#x20;
    * Type 3 ADU Permitted (adu3perm)
    * Minimum Size for a Type 3 Principal Building, in GSF (pGSFmn3)
    * Minimum Size for a Type 3 Principal Building, in FSF (pFSFmn3)
* [allstructures\_estsf](../../analysis-preparation/tabular-inputs/type-3-adus-accessory-existing.md)
* possparcels\_sjo\_zones (Generated from [3 | Prepare Spatial Data for Fit Tests](../3-or-prepare-spatial-data-for-fit-tests.md))

### Model Outputs

* parcels\_passforadu3 (Geometry and attributes of parcels that have passed through the Type 3 ADU Fit tests and are likely eligible.)&#x20;

### Key Assumptions

* Level 3 Parcel Data does not contain square footage figures for accessory structures, so the tool uses estimates of square footage created by analyzing building footprints. This means parcels with two-story accessory structures may be unnecessarily eliminated. The prescribed process can deliver strong estimates for the footprint of the first three structures on a parcel; parcels with more than three structures will have less precise estimates.
* The tool does not test accessory structures for a minimum dimension.

### Analysis

This model uses the policy parameters recorded in the zoningedits Excel spreadsheet (attached to the parcel data and structure data in the previous step) to evaluate what parcels and accessory structures meet the eligibility requirements for a Type 3 ADU. It does this by restricting the Possible Parcels data to only those parcels meeting the parcel attribute requirements, then checking the accessory structures to make sure at least one accessory structure is large enough to accommodate an ADU.&#x20;

_Model Design_

{% tabs %}
{% tab title="Parcels Input" %}
<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Parcel Attribute Tests" %}
<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Prepare Structure Input" %}
<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}

{% tab title="Join Parcels to Structures" %}
<figure><img src="../../.gitbook/assets/image (3) (3).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Export Results" %}
<figure><img src="../../.gitbook/assets/image (5) (2).png" alt=""><figcaption><p>Click to expand</p></figcaption></figure>
{% endtab %}
{% endtabs %}
