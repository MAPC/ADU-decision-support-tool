# Recommended Improvements

{% hint style="danger" %}
From Caitlin's Transition Memo. Not yet edited.
{% endhint %}

1. Develop internal ADU tool (3/8/2022)
2. Develop ADU yield tool (3/8/2022)
3. Formally produce mapcadu toolset as a Python module/library (3/8/2022)
4. Produce a data dictionary on the attributes added to parcel data through this tool (3/8/2022)
5. Produce a standard set of map templates (ArcMap? ArcPro? Other?) which can be used to display the spatial data produced by each tool for QC and/or visualization purposes (3/8/2022)
6. Clean and streamline code in parcelside\_categorize.py (3/8/2022)
7. Update detached or attached ADU tool to more generously define parcel segments for fit test. For example, the tool in its current state checks whether several aspect ratios of a minimum-area ADU fit when one side is aligned perfectly with each individual line segment which makes up the boundaries of the buildable area on the parcel. This is a working start, but the tool would be improved if the tool better accommodated line segments which share a terminus and form a nearly 180 degree angle (3/8/2022).
8. &#x20;Add finalized code to github (3/8/2022)
9. Reformat scripts as one or more executable applications with a GUI. (3/8/2022)
10. Build in more unit flexibility. Current script requires coordinate reference system in metres and user inputs in feet (outputs, e.g. area and length fields added to data, also in feet). (3/8/2022)
11. Build in data format flexibility. Current script requires spatial data as ESRI shapefiles and tabular data inputs as Excel files, but the modules which handle reading and writing data support other formats so this would be an easy fix. (3/8/2022)
