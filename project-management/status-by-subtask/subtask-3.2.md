---
description: 3.2 Decision Support Tool Development - Phase 1
---

# Subtask 3.2

<details>

<summary>For reference, subtask description (from Data Services Subtasks)</summary>

Using the software development roadmap, MAPC staff will conduct three development ‘sprints’ designed to create a draft product for City review. &#x20;

* The first sprint will focus on **assembling the data necessary for the high priority policy options** to be tested and high priority metrics to be created.&#x20;
* The second sprint will focus on creating a **beta version of the decision support tool to test out the highest priority options and create core metrics.** The beta version will be reviewed internally.&#x20;
* The third development sprint will focus on **additional feature development with the goal of producing a version of the tool ready for City staff review.**&#x20;

While the specific technology “stack” to be used is still TBD, it is likely that the development will use Esri ArcMap or ArcPro and Python.  <mark style="background-color:green;">**All development will be documented and version-controlled using GitHub so that the project will eventually be able to accept contributions from other users and software developers.**</mark> &#x20;

</details>

## Work Completed to Date

### Ongoing: Development Sprint 1&#x20;

> The first sprint will focus on assembling the data necessary for the high priority policy options to be tested and high priority metrics to be created.

In addition to the [Parameters table](../../policy/parameters/parameters-table.md) (which supports the flowchart described in the [Subtask 3.1](subtask-3.1.md) status update), the Beverly ADU Airtable base houses three tables that will aid in our development of the decision support tool. These tables have been embedded into the Parcel [Data](../../policy/parcel-characteristics/parcel-data.md), [Citywide Dimensional Requirements](../../policy/assumptions-and-policy/citywide-dimensional-requirements.md), and [Parking Requirements](../../policy/assumptions-and-policy/parking-requirements/) pages where, in some cases, the tabular data has been supplemented with written information.

Beyond the Airtable base and this GitBook, Data Services has assembled spatial data that might support analysis into a project [geodatabase](../../policy/parcel-characteristics/other-spatial-data.md). We have also developed a set of Python scripts that further describe the geometry of each parcel by identifying the parcel's front, side, and rear lot lines, separating those lot lines into individual segments, and measuring their length. (These dimensions are not available in the MAPC Land Parcel Database or the CAMA data the City provided.) Our next step will be to internally buffer these individual segments by their respective setbacks to determine the subarea of the parcel which could theoretically be used for further development.

### Next: Development Sprint 2&#x20;

> The second sprint will focus on creating a beta version of the decision support tool to test out the highest priority options and create core metrics. The beta version will be reviewed internally.

### After: Development Sprint 3

> The third development sprint will focus on additional feature development with the goal of producing a version of the tool ready for City staff review.
