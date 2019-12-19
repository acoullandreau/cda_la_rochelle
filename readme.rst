=================================
Map rendering - CDA La Rochelle
=================================


---------------------
Purpose of the script
---------------------

This repository contains an example of the use of the geo_rendering package_.
.. _package: https://pypi.org/project/geo-rendering/

A step-by-step guide on how to use this package is also available on Medium_.
.. _Medium: https://medium.com/@mozart38/a-quick-introduction-on-the-geo-rendering-python-package-9c6e290f9c


The idea here is to render a map of the CDA of La Rochelle, using a color code to indicate which zone each city belongs to. Those zones are used to calculate the cost of a transportation service from La Rochelle.

This repository contains:
* A Jupyter notebook that can be executed to save the output map or simply render it
* The output maps (two similar files)
* This readme file

The source map can be found here_.
.. _here: https://www.data.gouv.fr/en/datasets/decoupage-administratif-communal-francais-issu-d-openstreetmap/


-------------------------
Environment requirements
-------------------------

The code is written in Python 3.7.
The following packages are necessary to run it:
- geo_rendering (v1.0 is sufficient as the updated code is included in the notebook)
- numpy 1.16.4
- pandas 0.25.0
- OpenCV 4.1.0


-------------------------
Comments on the approach
-------------------------

The source shapefile contains the outline of all cities of France. We are interested in a few of them, we therefore need to render the map using the zoom trick of the package:
1. we create a zoom base map from the shapefile, using specifically the reference of the cities we want to see in the final rendering
2. we calculate the projection accordinly and scale the coordinates of all the shapes
3. we apply formatting (color filling, text info)


Note that the projection of the initial file had to be corrected. It looks like the projection takes into account the curvature of the earth, and we were looking for a "flat" representation of the territory. 

This triggered the update of the package (v1.1), with a new parameter that can be set to "correct" the initial projection on either axis.


