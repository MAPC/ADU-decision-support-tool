# Proposed Next Steps

Data Services next step on Subtask 3.2 is to devise a method to internally buffer a parcel's front, side, and rear lot lines by their respective setbacks to determine the subarea of the parcel which could theoretically be used for further development.&#x20;

After this point, we will need input from the project team on the following higher-priority questions:&#x20;

### ASAP

<details>

<summary>Project Management</summary>

* [x] Confirmation that the roadmap can stay as-is (see notes under [Subtask 3.1](status-by-subtask/subtask-3.1.md))\
  \
  _The road map is staying as is, based both on conversations / concerns from Tim. The language has been softened to not hold our team to anything specific, with the overall goals remaining the same._\
  __
* [ ] Clarity on the "template engagement materials" task 3 deliverable (see [Data Services Subtasks](reference/data-services-subtasks.md))\
  \
  _This was intended on being support materials for public webinars. Those have been eliminated from the scope, as has the deliverable. The task 3 deliverables are now only the “Fully-documented decision support tool”_\

*   [ ] Collaborate to define the design of the decision-support tool (see notes under [Decision Support Tool](../analysis/decision-support-tool.md))\
    \
    _This has been eliminated from the scope. This essentially meant that the tool would be open source (ish, whatever license your team wanted to use) and that GitHub should be used to develop the tool and make the repo publicly available for others to contribute to if they want to. Ryan has indicated to me (John) that the DS team keeps github as part of their workflow and makes code open to the public when they can, and there’s no reason as to why that should change for this project._

    __\
    _The top priority at this time is that this tool can lead to a functional draft of an ordinance for Beverly. DS is welcome to make the project open source and if there are resources to support that outside of the scope of this project, the housing team is fine with that being pursued independently._\

*   [ ] Collaborate to define an organizational structure for communication on policy options\
    \
    _We will need to discuss how to discuss and collaborate on the policy options and how to narrow down the policy options. Let me know how your team prefers to handle communication for this and if we need to follow any intake, set up work sessions, or provide email / slack responses._

    __\
    _On the housing side, we will want to set up 3 meetings: Goals and equity framework, variables / parameters, client-facing materials._

    __\
    _We need to get the client’s thoughts on what they would be open to or what there is likely to be severe opposition to. I have been given the indication that there would be little community pushback, but the effort is not a “Slam dunk” per-say for getting this passed. That will be discussed with them on Wednesday._\




* [ ] Collaborate to define an organizational structure for numerical inputs\
  \
  _We will need to discuss this to see what exactly you’re looking for with this question. It sounds like you’re asking what / how we will input the variables into the tool – such as lot size, zoning district, cover of existing structures, etc. Let’s talk through it more._

</details>

<details>

<summary>Analysis</summary>

* [ ] We're planning to explore [the four ADU typologies described here](../analysis/part-a-feasibility/1.-available-space/). Are there typologies we're exploring that you don't see as being necessary? Conversely, are there ADU typologies not under consideration that you would like us to explore? \
  \
  _These are the four that we should be looking at. I would just change “convert the attic” to “convert existing floor” as we consider those options and annotate it as such (floor, attic, basement, etc.). The two options under “principal” are currently allowed under the zoning regulations, the accessory ones are not currently allowed. The biggest focus should be on the ”Build new” option._\

*   [ ] <mark style="background-color:orange;">Draft list of parameters to explore so that we can assemble all needed data layers. (We don't need specific thresholds at this time, just an indication that they will be important.)</mark>\ <mark style="background-color:orange;"></mark>\ <mark style="background-color:orange;"></mark>a.     ADU Type (one of the four above)

    &#x20;              i.     This is the first step in Seattle’s tool, determining if the ADU is attached or detached. That logic determines what parameters and variables are needed. So the following may change based on what people select, but overall this is what we should be prepared for:\


    b.     Lot size sq ft (int)\


    c.      Zoning District (varchar, to get other variables)\


    &#x20;            i.     Total Impervious cover allowed by pct (float)

    &#x20;            ii.     Setbacks required (int)

    &#x20;                         1\.     Front

    &#x20;                         2\.     Rear

    &#x20;                         3\.     Side

    &#x20;             iii.     Parking Requirements per unit (float)

    &#x20;             iv.     Maximum FAR (float)\


    d.     Current lot coverage in sq ft (float)\


    e.     Flood Plain (binary)\
    &#x20;         i.     The city has a floodplain ordinance designed to have additional protections in flood districts. We don’t need to get the flood zone level or anything that specific, but we’ll want to flag anything that is likely in a flood plain and discourage basement ADUs in those areas [https://www.beverlyma.gov/DocumentCenter/View/130/Zoning-Amendment-Floodplain-Overlay-District-Ordinance-PDF](https://www.beverlyma.gov/DocumentCenter/View/130/Zoning-Amendment-Floodplain-Overlay-District-Ordinance-PDF)\


We’ll likely want to add some more nuanced things here based on some input from the city. Let me know if you’re looking for something different.

</details>

### Soon

<details>

<summary>Part A | 1A. How much space exists on this parcel?</summary>

* [ ] **For Principal-Existing and Principal-New:** _The State of Zoning for Accessory Dwelling Units_ (Dain, 2018) suggests ADU Ordinances and Bylaws commonly control ADUs by **percent of primary unit floor area** and/or **percent expansion of primary dwelling.** Do you imagine wanting to regulate ADUs using either or both of these parameters? ****&#x20;
* [ ] **For Principal-New and Accessory-New:** Please confirm that the setbacks recorded in the Minimum Yards - Front, Minimum Yards - Side, and Minimum Yards - Rear [columns in the Airtable](../policy/assumptions-and-policy/citywide-dimensional-requirements.md) are correct. Will these setbacks be fixed or flexible parameters? For reference, policy options from Ella on minimum setbacks:
  * No change: Same as underlying lot size&#x20;
  * Potential changes:&#x20;
    * Rear, side, and/or front setbacks are decreased to x, x, and x feet
    * No additional setback for ADUs within or attached to non-conforming existing structures&#x20;
* [ ] **For Accessory-New:** Will detached ADUs be allowed to be constructed in parcel setbacks?
* [ ] **For Accessory-New:** Is there a front yard setback that will only apply to ADUs? (Put differently, will there be an area of the parcel where ADUs may only be constructed?) This might relate to these options from Ella on yard requirements:
  * No change: None&#x20;
  * Potential changes:
    * If detached is allowed, minimum of x square feet of yard is required

</details>

<details>

<summary>Part A | 1Bii. How much of the allowable density is already consumed?</summary>

* [ ] We assume ADUs will count towards at least a few parcel-wide density controls. For example, if an ADU would push the parcel beyond a maximum FAR, the ADU could not be built. Is this assumption correct? If so, what of the existing (or non-existing) dimensional regulations should we take into account? A partial list is provided in [1Bii](../analysis/part-a-feasibility/1bii.-how-much-of-the-allowable-density-is-already-consumed.md)., under Factors We Could Explore.
* [ ] Is it safe to assume we can ignore the potential for subdivision of lots greater than twice the lot area minimum?

</details>

<details>

<summary>Part A | 2Ai. How much space is required for the ADU structure?</summary>

* [ ] Will the ordinance define ADU size? If so, what dimensional regulations will be used? A partial list is provided under [2Ai.](../analysis/part-a-feasibility/2ai.-how-much-space-is-required-for-the-adu-structure.md), under Factors We Could Explore.
* [ ] What should we use as a minimum dimension for an ADU? (This is needed as an assumption in our analysis regardless of whether it is translated to policy.)

</details>

<details>

<summary>Part A | 2Aii. How much space is available around the ADU? </summary>

* [ ] Will the ordinance define minimum space around the ADU? If so, what dimensional regulations will be used? A partial list is provided in [2Aii.](../analysis/part-a-feasibility/2aii.-how-much-space-is-available-around-the-adu.md), under Factors We Could Explore.

</details>

<details>

<summary>Part A | 2B. How much space is required for the parking associated with the ADU?</summary>

* [ ] Will the ordinance define parking requirements for the ADU? If so, how many spaces? A partial list is provided in [2B.](../analysis/part-a-feasibility/2b.-how-much-space-is-required-for-the-parking-associated-with-the-adu.md), under Factors We Could Explore.
* [ ] Are there any Beverly-specified parking requirements (minimum size, acceptable layout, etc.) that we should take into account?
* [ ] Are parking spaces allowable in parcel setbacks?



</details>

<details>

<summary>Part B | 3A. Is an ADU allowable given the individual characteristics of the parcel?</summary>

* [ ] How will the ordinance define parcel eligibility by parcel characteristics? A partial list is provided in [3A.](../analysis/part-b-or-eligibility/3a.-is-an-adu-allowable-given-the-individual-characteristics-of-the-parcel.md), under Factors We Could Explore.

</details>

### Later

<details>

<summary>Part B | 3B. Is an ADU allowable given the location of the parcel?</summary>

* [ ] How will the ordinance define parcel eligibility by parcel location? A partial list is provided in [3B.](../analysis/part-b-or-eligibility/3b.-is-an-adu-allowable-given-the-location-of-the-parcel.md), under Factors We Could Explore.

</details>

<details>

<summary>Part A | 1Bi. How much space is undevelopable due to environmental factors?</summary>

No questions for Land Use at this time.

</details>

<details>

<summary>Part C | Yield</summary>

No questions for Land Use at this time.

</details>

## Next Steps for Data Services

<details>

<summary>General</summary>

* [ ] What types of analysis will we deprioritize?
* [ ] Where can we bring in additional support? (Potentially, from Research on tabular-fit analysis?)

</details>

<details>

<summary>Part A | 1A. How much space exists on this parcel?</summary>

* [ ] **Principal-Existing and Accessory-Existing:** Data Services needs to identify which of the analysis options under [Principal-Existing](../analysis/part-a-feasibility/1.-available-space/principal-existing.md) and [Accessory-Existing](../analysis/part-a-feasibility/1.-available-space/accessory-existing.md) we want to propose to the project team.
* [ ] **Accessory-New:** Data Services needs to devise a method to internally buffer a parcel's front, side, and rear lot lines by their respective setbacks to determine the subarea of the parcel which could theoretically be used for further development. .&#x20;

</details>

<details>

<summary>Part A | 1Bi. How much space is undevelopable due to environmental factors?</summary>

* [ ] Review possible environmental factors, particularly if we want to ignore this part of the analysis&#x20;

</details>

<details>

<summary>Part A | Output</summary>

* [ ] Data Services needs to devise a method to fit a rectangle (or rectangles) representing the space required for the ADU (and/or space around the ADU and/or ADU parking) in the area of the parcel we've determined to be developable.

</details>



