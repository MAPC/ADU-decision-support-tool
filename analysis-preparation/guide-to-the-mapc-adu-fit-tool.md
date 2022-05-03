---
description: From Caitlin
---

# Guide to the MAPC ADU fit tool

Data Inputs: Prepare these in advance

The tool requires the following inputs:

* • Parcel spatial dataset with, at a minimum, parcel polygon geometry and one field identifying the zoning at each parcel through a standardized code. Standard Level 3 attributes required for other parts of the analysis, but not the fit test. The analyst may need to manipulate the parcel dataset to identify parcels located in areas relevant to the proposed ADU ordinance(s) which are not reflected by zoning alone. For example, the analyst may wish to add a binary column to the parcel dataset which has a value of “1” if the parcel is within a half mile of a transit area or “0” if the parcel is further than half a mile from a transit station of ADU dimensional requirements differ depending on whether the ADU is within a transit area.&#x20;
*
  * o Option 1 (preferred/supported): From Massachusetts Land Parcel Database, select parcels WHERE (‘muni’ = ‘Muni Name’). Export the selected cells, save as ESRI shapefile, and record file path. This method is preferred because the script tool is currently designed to support the schema of the MA Land Parcel Database.
  * o Option 2 (risky but possible reward): Use parcel geometry and attributes from local CAMA database. One reason to use this option would be that the ADU ordinance may involve parcel attributes which are included in detailed CAMA records, but would not be included in the standardized MA Land Parcel Database attributes. However, this option would require the analyst to edit the script and ADU ordinance excel sheet to work properly with the local CAMA parcel data schema.&#x20;
  * • Streets or “right of way” lines or parcels dataset. At a minimum, their geometry. The tool currently supports spatial data inputs in ESRI shapefile format, but could be easily tweaked by a knowledgeable analyst to read in the data in&#x20;
  * o Option 1: Get vector file from municipality.
  * o Option 2: From Massachusetts Land Parcel Database, select parcels WHERE (‘muni’ = ‘Muni Name’) AND (‘type’ IN (‘ROW’, ‘PRIV\_ROW’, ‘RAIL\_ROW’)). Check for variant right-of-way file types. Export the selected cells, save as ESRI shapefile, and record file path for future reference.
  * • Table (excel sheet form) documenting the dimensional requirements in each type of municipal zoning. This table should also include the proposed dimensional requirements for an attached or detached ADU in each type of zoning and/or area which can be identified through parcel attributes within the municipality.&#x20;
  * o Required zoning dimensional information:
  *
    * ♣ Minimum front setback length, feet
    * ♣ Minimum side setback length, feet
    * ♣ Minimum rear setback length, feet
  * o Required ADU dimensional information:
  *
    * ♣ Minimum width in any dimension, feet
    * ♣ Minimum internal dwelling unit area in any dimension, square feet
    * ♣ Minimum distance between a structure on the parcel and detached ADU, feet
    * • Building roofprint spatial data
  * o Web resource listed in spatial data browser: [http://www.mass.gov/anf/research-and-tech/it-serv-and-support/application-serv/office-of-geographic-information-massgis/datalayers/structures.html](http://www.mass.gov/anf/research-and-tech/it-serv-and-support/application-serv/office-of-geographic-information-massgis/datalayers/structures.html)
  * o K drive local copy listed in spatial data browser: K:\DataServices\Datasets\MassGIS\Facilities\_Structures
  * o Because only building roofprint geometry is needed, there is no reason not to use any comparable alternative. Currently, the script supports ESRI shapefile format.&#x20;
  * • Excluded area polygon dataset. Must contain the geometry of any areas which would not be eligible for building new ADUs for example within 100 ft of a wetland, in flood zone, on steep slope, etc. as determined by analysts and planners. The script currently supports ESRI shapefile format.&#x20;

Running the Tool

Python setup

The ADU analysis tool is a set of Python scripts which ingest spatial and tabular data on municipal features and regulations and produce spatial and tabular data files on municipal parcels. The products constitute municipal parcel data with added attributes which reflect constraints on adding ADUs to the parcel and which kind of ADU, if any, can fit on the parcel given the parameters of a proposed zoning ordinance.

The ADU analysis tool relies on several Python libraries and packages.&#x20;

*
  * • Geopandas
  * • Pandas
  * • Shapely
  * • Numpy
  * • Scipy
  * • Datetime

In addition, the tool set relies on a number of custom functions designed specifically for this application. At present, the file containing those functions is found at the path below (3/8/2022):

K:\DataServices\Projects\Current\_Projects\Housing\Beverly\_ADU\Scripts\mapcadu\mapcadu.py

The tools were developed using Python 3.8 in an Anaconda Spyder development environment. An environment (.yml) file which contains all the dependencies used in that development environment is stored here:

K:\DataServices\Projects\Current\_Projects\Housing\Beverly\_ADU\Scripts\mapcadu.yml

A user should be able to create a conda environment from the .yml file through:

conda env create -f mapcadu.yml

With some path manipulation.

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

Parcel side classifier

This tool requires only the parcel geometry and the streets or “Right of Way” geometry as inputs. The tool breaks the linestrings which define the parcel boundaries into individual line segments, then classifies each segment as belonging to the “front”, “back”, or “sides” of the parcel depending on its distance to the nearest street or ROW feature, angle relative to the nearest street/ROW, and relationship to other line segments which make up the parcel boundary. The tool stores a GeoPandas GeoDataFrame which is the product of the tool in “pickled” (.pkl) form when complete. The product GeoDataFrame contains several geometry columns, including the original parcel geometry, the minimum rotated rectangle which contains the original parcel geometry, and three fields containing linestrings which represent the parts of the parcel boundaries which have been classified as the front, back, and sides of the parcel. This tool may take multiple days and up to over a week to run depending on municipality size. Since the tool requires only the most basic and publicly available input data and no information on ADU requirements OR zoning, we recommend running this tool as soon as a decision is made to create or revise an ADU ordinance.

\


The tool is found at the following K drive location:

K:\DataServices\Projects\Current\_Projects\Housing\Beverly\_ADU\Scripts\parcelside\_categorize.py

ADU fit tool

This tool requires the .pkl file resulting from running the Parcel Side Classifier, building roofprint spatial data, excluded area spatial data, and zone-based dimensional requirements for a detached ADU. This tool makes a rough estimate at whether a minimum-size ADU will fit on empty space in each parcel depending on required setbacks from the front, back, and sides of the parcel and minimum space permitted between structures on the parcel and a detached ADU. The tool also makes a rough check for whether a minimum-sized ADU can fit as an extension of an existing structure on the parcel without infringing on setback or excluded area. The tool’s results will include false negatives for some parcels (that is, the results would indicate that a minimum-size detached or building-extension ADU could not fit on the parcel given zoning and ADU dimensional requirements when one actually could fit with some creativity or finesse). However, the tool’s results are very unlikely to include false positives (that is, indicating that a detached or building-extension ADU can fit on the parcel when one actually can not). Property owners interested in installing a detached or building-extension ADU should confirm the tool’s eligibility result with the help of a surveyor.&#x20;

\


An example zoning table compatible with the ADU fit tool can be found at the file path below. Fields highlighted in blue are required by the tool and were sourced from a Beverly, MA zoning requirements table. Fields highlighted in yellow were not included in the Beverly zoning table, and reflect the parameters of zone-dependent ADU dimensional requirements in a hypothetical proposed ADU ordinance.&#x20;

\


The tool is found at the following K drive location:

K:\DataServices\Projects\Current\_Projects\Housing\Beverly\_ADU\Scripts\setback\_fit.py

Internal ADU tool

Using only standard Level 3 tax parcel information, zoning dimensional requirements, and proposed ADU ordinance parameters, the tool estimates whether an ADU could be installed (a) within the existing primary structure, or (b) as a vertical or footprint extension of the existing structure.&#x20;

ADU Yield Tool

TBD 3/8/2022

Understanding the tool

Supporting Functions

*
  * • Segments: Accepts a curve (LineString), returns the individual line segments which make up the curve.
  * • Azimuth: Returns the Azimuth between two shapely points. Accepts point1 and point2 (Shapely points), returns azimuth between them in degrees.
  * • Anglediff: Accepts two Shapely line segments, returns difference in degrees between their angles relative to a single line.
  * • Dir\_hausdorff: Accepts two Shapely line segments, returns maximum distance between them.
  * • Touches: Accepts two Shapely line segments, returns “True” if they share an endpoint and “False” otherwise. Does not detect whether they cross in the middle. The idea is that we start with a collection of line segments which make up a Polygon boundary and can use this function to determine which of them are adjacent.
  * • Lengthshape: Accepts a polygon and a flag. The function returns either the higher or lower side length of the minimum rotated rectangle which contains the polygon. Returns the higher side length if the flag is set to “length”, the lower side length otherwise. Returns length in units of feet, assuming CRS is in meters.&#x20;
  * • Areainterior: Given a rectangular detached ADU’s outer width and length in feet, the minimum required interior area in square feet, and the thickness of a wall, this function returns “True” if the proposed ADU would contain adequate interior square footage and “False” otherwise.
  * • Areatest: Given the square footage available for building on the parcel, the minimum interior area required for an ADU in square feet, and wall thickness of an ADU in square feet, this function returns “True” if there is enough area available on the parcel to contain a detached ADU and “False” otherwise. Does not check for shape issues, so this is a basic check to rule out doing a shape fit check in the case that there is not enough space on the parcel for a detached ADU in any arrangement.
  * • Makerect: Given two lengths which define the size and shape of a rectangle, a Shapely line segment which is on the boundary of the Polygon available for building within the parcel after excluded areas have been removed, the slope and intercept of the line segment in its native coordinate system, and a user-defined number of rectangles to generate (“nrects”), this function returns a list of nrects Shapely Polygon rectangles with side lengths length1 and length2 which share a side of length1 with the line segment. The rectangles are evenly spaced along the line segment such that the first rectangle is placed to share a corner with the first endpoint of the line segment and the last rectangle is placed to share the far corner with the second endpoint of the line segment.&#x20;
  * o Makepoint: This function creates a point which matches specific geometric criteria given two Shapely points on a reference line, the slope and intercept of the line the new point should be on, the ideal distance between the new point and the first reference point, and a flag which indicates whether the new point should be on the reference line or perpendicular to it. Used to find the points which define the rectangle in “makerect.”
  * • Fitrects: Given a list of Shapely Polygons (ideally a list of rectangles created through “makerects” and another single Shapely Polygon (ideally a Polygon representing the buildable area on a parcel), returns “True” if any of the polygons in the list are contained by the single polygon.&#x20;
  * • Fittest: Given a Shapely polygon representing the buildable area on a parcel, the length and width of that shape calculated through “lengthshape”, the minimum area of an ADU in square feet, the minimum width of an ADU in feet, and the wall thickness of a detached ADU in feet, returns “True” if a minimum-size rectangular ADU is found to fit within the buildable area on the parcel.&#x20;

Recommended Improvements

1.
   1. 1\. Develop internal ADU tool (3/8/2022)
   2. 2\. Develop ADU yield tool (3/8/2022)
   3. 3\. Formally produce mapcadu toolset as a Python module/library (3/8/2022)
   4. 4\. Produce a data dictionary on the attributes added to parcel data through this tool (3/8/2022)
   5. 5\. Produce a standard set of map templates (ArcMap? ArcPro? Other?) which can be used to display the spatial data produced by each tool for QC and/or visualization purposes (3/8/2022)
   6. 6\. Clean and streamline code in parcelside\_categorize.py (3/8/2022)
   7. 7\. Update detached or attached ADU tool to more generously define parcel segments for fit test. For example, the tool in its current state checks whether several aspect ratios of a minimum-area ADU fit when one side is aligned perfectly with each individual line segment which makes up the boundaries of the buildable area on the parcel. This is a working start, but the tool would be improved if the tool better accommodated line segments which share a terminus and form a nearly 180 degree angle (3/8/2022).
   8. 8\. Add finalized code to github (3/8/2022)
   9. 9\. Reformat scripts as one or more executable applications with a GUI. (3/8/2022)
   10. 10\. Build in more unit flexibility. Current script requires coordinate reference system in metres and user inputs in feet (outputs, e.g. area and length fields added to data, also in feet). (3/8/2022)
   11. 11\. Build in data format flexibility. Current script requires spatial data as ESRI shapefiles and tabular data inputs as Excel files, but the modules which handle reading and writing data support other formats so this would be an easy fix. (3/8/2022)

\


\


\


\
