# Parcel Side Classifier

{% hint style="danger" %}
From Caitlin's Transition Memo. Not yet edited.
{% endhint %}

Parcel side classifier

This tool requires only the parcel geometry and the streets or “Right of Way” geometry as inputs. The tool breaks the linestrings which define the parcel boundaries into individual line segments, then classifies each segment as belonging to the “front”, “back”, or “sides” of the parcel depending on its distance to the nearest street or ROW feature, angle relative to the nearest street/ROW, and relationship to other line segments which make up the parcel boundary. The tool stores a GeoPandas GeoDataFrame which is the product of the tool in “pickled” (.pkl) form when complete. The product GeoDataFrame contains several geometry columns, including the original parcel geometry, the minimum rotated rectangle which contains the original parcel geometry, and three fields containing linestrings which represent the parts of the parcel boundaries which have been classified as the front, back, and sides of the parcel. This tool may take multiple days and up to over a week to run depending on municipality size. Since the tool requires only the most basic and publicly available input data and no information on ADU requirements OR zoning, we recommend running this tool as soon as a decision is made to create or revise an ADU ordinance.

\


The tool is found at the following K drive location:

K:\DataServices\Projects\Current\_Projects\Housing\Beverly\_ADU\Scripts\parcelside\_categorize.py
