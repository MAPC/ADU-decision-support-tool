# Table of contents

## Analysis Preparation

* [Installations](README.md)
  * [Python](analysis-preparation/installations/python.md)
* [Tabular Inputs](analysis-preparation/tabular-inputs/README.md)
  * [1. Allowable Typologies](analysis-preparation/tabular-inputs/all-adus.md)
  * [2. Existing Zoning](analysis-preparation/tabular-inputs/general-zoning-dimensional-requirements.md)
  * [For Type 1 ADUs](analysis-preparation/tabular-inputs/type-1-adus-principal-existing.md)
  * [For Type 2 ADUs](analysis-preparation/tabular-inputs/type-2-adus-principal-new.md)
  * [For Type 3 ADUs](analysis-preparation/tabular-inputs/type-3-adus-accessory-existing.md)
  * [For Type 4 ADUs](analysis-preparation/tabular-inputs/type-4-adus-xxx.md)
* [Spatial Inputs](analysis-preparation/spatial-inputs/README.md)
  * [1. All Parcels](analysis-preparation/spatial-inputs/step-1.-all-parcels.md)
  * [2. Zoning Districts](analysis-preparation/spatial-inputs/step-2.-zoning.md)
  * [3. Effective ADU Boundary](data-preparation.md)
  * [4. Parcel-level Exclusions](analysis-preparation/spatial-inputs/step-4.-parcel-level-exclusions.md)
  * [For Type 2 and 4 ADUs and/or ADUs with On-site Parking](analysis-preparation/spatial-inputs/for-type-2-and-4-adus-and-or-adus-with-on-site-parking/README.md)
    * [A. Building Roofprints](analysis-preparation/spatial-inputs/for-type-2-and-4-adus-and-or-adus-with-on-site-parking/a.-building-roofprints.md)
    * [B. Right-of-Way Polygons](analysis-preparation/spatial-inputs/for-type-2-and-4-adus-and-or-adus-with-on-site-parking/b.-right-of-way-polygons.md)
    * [For On-site Parking](analysis-preparation/spatial-inputs/for-type-2-and-4-adus-and-or-adus-with-on-site-parking/for-on-site-parking.md)
  * [For Type 3 ADUs](analysis-preparation/spatial-inputs/for-type-3-adus.md)

## Analysis Steps

* [Analysis Steps](analysis-steps/analysis-steps.md)
* [Running the Python Tool](analysis-steps/running-the-python-tool/README.md)
  * [Parcel Side Classifier](analysis-steps/running-the-python-tool/parcel-side-classifier.md)
  * [ADU Fit Tool](analysis-steps/running-the-python-tool/adu-fit-tool.md)

## Documentation

* [Python Supporting Functions](documentation/python-supporting-functions.md)
* [Recommended Improvements](documentation/recommended-improvements.md)

## Project Management

* [Meeting Notes](<README (2).md>)
* [Status by Subtask](<README (1).md>)
  * [Subtask 3.1](project-management/status-by-subtask/subtask-3.1.md)
  * [Subtask 3.2](project-management/status-by-subtask/subtask-3.2.md)
* [Proposed Next Steps](project-management/proposed-next-steps.md)
* [Reference](project-management/reference/README.md)
  * [Data Services Subtasks](project-management/reference/data-services-subtasks.md)
  * [Data Services Budget](project-management/reference/data-services-budget.md)
  * [Tool Precedents](project-management/reference/tool-precedents.md)

## Analysis Roadmap <a href="#analysis" id="analysis"></a>

* [Part A | Feasibility](analysis/part-a-feasibility/README.md)
  * [1A. How much space exists on this parcel?](analysis/part-a-feasibility/1.-available-space/README.md)
    * [Principal-Existing](analysis/part-a-feasibility/1.-available-space/principal-existing.md)
    * [Accessory-Existing](analysis/part-a-feasibility/1.-available-space/accessory-existing.md)
    * [Principal-New](analysis/part-a-feasibility/1.-available-space/principal-new.md)
    * [Accessory-New](analysis/part-a-feasibility/1.-available-space/accessory-new.md)
  * [1Bi. How much space is undevelopable due to environmental factors?](analysis/part-a-feasibility/1bi.-how-much-space-is-undevelopable-due-to-environmental-factors.md)
  * [1Bii. How much of the allowable density is already consumed?](analysis/part-a-feasibility/1bii.-how-much-of-the-allowable-density-is-already-consumed.md)
  * [2Ai. How much space is required for the ADU structure?](analysis/part-a-feasibility/2ai.-how-much-space-is-required-for-the-adu-structure.md)
  * [2Aii. How much space is required around the ADU?](analysis/part-a-feasibility/2aii.-how-much-space-is-available-around-the-adu.md)
  * [2B. How much space is required for the parking associated with the ADU?](analysis/part-a-feasibility/2b.-how-much-space-is-required-for-the-parking-associated-with-the-adu.md)
  * [Part A. Output](analysis/part-a-feasibility/part-a.-output.md)
* [Part B | Eligibility](analysis/part-b-or-eligibility/README.md)
  * [3A. Is an ADU allowable given the individual characteristics of the parcel?](analysis/part-b-or-eligibility/3a.-is-an-adu-allowable-given-the-individual-characteristics-of-the-parcel.md)
  * [3B. Is an ADU allowable given the location of the parcel?](analysis/part-b-or-eligibility/3b.-is-an-adu-allowable-given-the-location-of-the-parcel.md)
* [Part C | Yield](analysis/part-c-or-yield/README.md)
  * [4. How many ADUs will be developed?](analysis/part-c-or-yield/4.-how-many-adus-will-be-developed.md)
  * [5. What are the impacts of that development?](analysis/part-c-or-yield/5.-what-are-the-impacts-of-that-development.md)

## Supporting Information <a href="#policy" id="policy"></a>

* [Parameters](policy/parameters/README.md)
  * [Parameters Table](policy/parameters/parameters-table.md)
  * [Additional Parameters](policy/parameters/additional-parameters.md)
* [Parcel Characteristics](policy/parcel-characteristics/README.md)
  * [Parcel Data](policy/parcel-characteristics/parcel-data.md)
  * [Other Spatial Data](policy/parcel-characteristics/other-spatial-data.md)
* [Assumptions and Policy](policy/assumptions-and-policy/README.md)
  * [ADU Policy Options](policy/assumptions-and-policy/adu-policy-options/README.md)
    * [Scenario 0: Existing ADU Ordinance](policy/assumptions-and-policy/adu-policy-options/scenario-0-existing-adu-ordinance.md)
  * [Citywide Dimensional Requirements](policy/assumptions-and-policy/citywide-dimensional-requirements.md)
  * [Parking Requirements](policy/assumptions-and-policy/parking-requirements/README.md)
    * [Citywide Parking Requirements](policy/assumptions-and-policy/parking-requirements/number-of-parking-spaces.md)
    * [Parking Assumptions](policy/assumptions-and-policy/parking-requirements/previous-parking-assumptions.md)

## Deliverables <a href="#technical-documentation" id="technical-documentation"></a>

* [Decision Support Tool](analysis/decision-support-tool.md)
  * [Deliverable 1: Code Base](technical-documentation/deliverable-1-code-base.md)
  * [Deliverable 2: User Guide](technical-documentation/deliverable-2-user-guide.md)
* [Technical Documentation](technical-documentation/technical-documentation/README.md)
  * [Fixed Assumptions](technical-documentation/technical-documentation/fixed-assumptions.md)
  * [Joining LPD and CAMA Data](technical-documentation/parcel-data.md)
