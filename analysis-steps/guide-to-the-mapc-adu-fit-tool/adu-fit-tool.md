# ADU Fit Tool

{% hint style="danger" %}
From Caitlin's Transition Memo
{% endhint %}

ADU fit tool

This tool requires the .pkl file resulting from running the Parcel Side Classifier, building roofprint spatial data, excluded area spatial data, and zone-based dimensional requirements for a detached ADU. This tool makes a rough estimate at whether a minimum-size ADU will fit on empty space in each parcel depending on required setbacks from the front, back, and sides of the parcel and minimum space permitted between structures on the parcel and a detached ADU. The tool also makes a rough check for whether a minimum-sized ADU can fit as an extension of an existing structure on the parcel without infringing on setback or excluded area. The tool’s results will include false negatives for some parcels (that is, the results would indicate that a minimum-size detached or building-extension ADU could not fit on the parcel given zoning and ADU dimensional requirements when one actually could fit with some creativity or finesse). However, the tool’s results are very unlikely to include false positives (that is, indicating that a detached or building-extension ADU can fit on the parcel when one actually can not). Property owners interested in installing a detached or building-extension ADU should confirm the tool’s eligibility result with the help of a surveyor.&#x20;

\


An example zoning table compatible with the ADU fit tool can be found at the file path below. Fields highlighted in blue are required by the tool and were sourced from a Beverly, MA zoning requirements table. Fields highlighted in yellow were not included in the Beverly zoning table, and reflect the parameters of zone-dependent ADU dimensional requirements in a hypothetical proposed ADU ordinance.&#x20;

\


The tool is found at the following K drive location:

K:\DataServices\Projects\Current\_Projects\Housing\Beverly\_ADU\Scripts\setback\_fit.py
