---
description: From Caitlin
---

# Guide to the MAPC ADU fit tool

## Running the Tool

The target user is an analyst working in municipal or regional planning who has some familiarity with scripted data analysis. The scripts are designed to require minimal edits by such an analyst to produce summaries of parcel-level ADU eligibility and municipal-level ADU yield for any municipality in Massachusetts. To set up and run the tools, the analyst should perform the following steps:

1.
   1. 1\. Obtain and format the spatial and tabular input data described below under “Tool Components.”&#x20;
   2. 2\. Install software which can be used to run Python scripts (recommended: Anaconda3 and Spyder).
   3. 3\. Within the software for running Python scripts, set up an environment with the packages and dependences in the environment file (.yml) above.
   4. 4\. Open the .py file which makes up each script (descriptions below) in the software and appropriate environment. Each script opens with a set of package imports followed by a number of lines which are input file path definitions. This section is bordered above and below by commented/non-evaluated text labeled “Edit this part” and “End edit section.” The user should update each evaluated line so that the right hand side of the equals sign is the appropriate file path to the data they prepared.
   5. a. Run the parcel side classifier.” Open the script “parcelside\_categorize.py” in your preferred environment. Save a copy of the script for your project and update the file paths in the opening section to point to the input files you prepared and the destination file. The results will bear the following names in that destination file:
   6.
      1. i. parcels\_sides.pkl: This .pkl file is a stored GeoPandas GeoDataframe; essentially a Dataframe (table) with all original attributes of the parcel and three geometry attributes. The geometry attributes correspond to the parts of the parcels’ boundary which were categorized as the front (“”), back (“”), and sides (“”). This file will be a key input to the next step, running the ADU fit tool.
      2. ii. Parcel\_front.shp: This shapefile will contain all original attributes of the parcel. Its geometry will be the line segments on the boundary which the script categorized as the parcels’ frontage. We export this file as a shapefile so that users may view the categorized parcel frontages in context with other layers if desired.&#x20;
      3. iii. Parcel\_backs.shp: This shapefile will contain all original attributes of the parcel. Its geometry will be the line segments on the boundary which the script categorized as the parcels’ back. We export this file as a shapefile so that users may view the categorized parcel backs in context with other layers if desired.
      4. iv. Parcel\_sides.shp: This shapefile will contain all original attributes of the parcel. Its geometry will be the line segments on the boundary which the script categorized as the parcels’ sides. We export this file as a shapefile so that users may view the categorized parcel sides in context with other layers if desired.
   7. b. Run the ADU fit tool&#x20;
   8. 5\. When the file paths in the “edit” section are updated and the resulting file is saved, run the script.
   9. 6\. The products of the script will be saved as new products in the folder the user provided as “basefp = \_\_\_” in each script.&#x20;

Tool Components







\


\


\


\
