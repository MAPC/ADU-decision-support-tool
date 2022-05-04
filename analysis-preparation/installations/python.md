# Python

{% hint style="danger" %}
From Caitlin's Transition Memo. Not yet edited.
{% endhint %}

#### Python Setup

The ADU analysis tool is a set of Python scripts that ingest spatial and tabular data on municipal features and regulations and produce spatial and tabular data files on municipal parcels. The products constitute municipal parcel data with added attributes that reflect constraints on adding ADUs to the parcel and which kind of ADU, if any, can fit on the parcel given the parameters of a proposed zoning ordinance.

The ADU analysis tool relies on several Python libraries and packages.&#x20;

* Geopandas
* Pandas
* Shapely
* Numpy
* Scipy
* Datetime

In addition, the toolset relies on a number of custom functions designed specifically for this application. At present, the file containing those functions is found at the path below (3/8/2022):

`K:\DataServices\Projects\Current_Projects\Housing\Beverly_ADU\Scripts\mapcadu\mapcadu.py`

The tools were developed using Python 3.8 in an Anaconda Spyder development environment. An environment (.yml) file which contains all the dependencies used in that development environment is stored here:

`K:\DataServices\Projects\Current_Projects\Housing\Beverly_ADU\Scripts\mapcadu.yml`

A user should be able to create a conda environment from the .yml file through:

`conda env create -f mapcadu.yml`

With some path manipulation.
