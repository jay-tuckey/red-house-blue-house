# Red House, Blue House...
Australian towns have a system of street names and numbers to allow us to navigate them. Remote Aboriginal communities typically do not. Street signs are usually non existent and house numbers are typically missing or obscured. The Aboriginal residents of East Arnhem Land do not use street names or numbers to identify a house, instead they use descriptive methods. The houses are painted in a variety of colours, and so they are often identified by colour and nearby prominent landmarks.
For example, “I live in the blue house at the end of the road”.

This presents a great difficulty to those who are not familiar with the community. Emergency services may be delayed while trying to find a house. Visiting services may spend a significant portion of their day just trying to find the correct house, which can result in people missing out on services because of time limitations.

Currently, NT Government employees use Bushtel, which provides downloadable PDF slap maps, as well as online overlays for Google Maps showing street names and numbers. There are no colour coded maps, which makes it difficult to navigate based on the directions given by the local residents.

[Example Slap Map](http://www.ntlis.nt.gov.au/hpa-services/slapmaps?community_id=500)

Our project will address this by providing maps that have the colour and lot number of each house as well as identifying key landmarks. We will be using the existing geospatial data from Bushtel, and utilising an open source mobile app (GeoODK). This app will allow users to view colour coded maps on their mobile devices for easy navigation, and will allow them to upload corrections when required. For example, if a house is repainted a different colour, the user can fill in a quick form in the app, which is uploaded to the server and the map can be corrected. These maps will also be viewable in a web based format.

[Web-Map for Gapuwiyak](https://jay-tuckey.github.io/red-house-blue-house/gapuwiyak_town_map.html)

Our web map provides an interactive map with handy tools for zooming into the map, and also provides mouse-over tooltips to view extra data about each house or building. This is useful for marking shops, clinics and other landmarks.

We have nearly everything we need for this project using open-source software and publicly available data, however field work is required to collect the house colour data for all communities.

This product will be extremely useful for a range of services. It will decrease response times for Emergency Services and increase work efficiency for visiting service providers. Having accurate and relevant maps will aid in closing the gap for remote communities.

Our data flow goes like this:
1. From the Bushtel website we fetch shape imagery.
2. We pipe that data into a program called TileMill, along with sattelite imagery from Google. This generates an offline usable map, which is great for communities with limited internet access.
3. We put the offline map into an app called GeoODK which allows a person in the community to collect data points with the colours of the building and any points of interest or other data. This data is fed back to an ODK Aggregation server in the cloud, to store and clean up the data. [Data Aggregate Server](https://red-house-blue-house.appspot.com/Aggregate.html)

![aggregate server screenshot](https://github.com/jay-tuckey/red-house-blue-house/raw/master/gapuwiyak_data.png "Aggregate Server Screenshot")

4. From the ODK Aggregation server we pull the data and merge it with the shape imagery from Bushtel, creating a shapefile with the coloured shapes. We do this using a Python Jupyter Notebook.
5. We can save the exported map to a HTML page for viewing on a computer: [Web-Map for Gapuwiyak](https://jay-tuckey.github.io/red-house-blue-house/gapuwiyak_town_map.html)
6. We can also save the exported map as an offline layer, so that it can be viewed in the communities without internet connection.

# Open Source Programs Used

![python](https://www.python.org/static/img/python-logo@2x.png)

[Python](https://www.python.org)

![anaconda](https://www.continuum.io/sites/all/themes/continuum/assets/images/logos/logo-horizontal-large.svg)

[Anaconda Python with Jupyter Notebook](https://www.continuum.io/downloads)

[TileMill](https://tilemill-project.github.io/tilemill/)

![qgis](http://www.qgis.org/en/_static/logo.png)

[QGis](http://www.qgis.org/en/site/#)

[GeoODK] (http://geoodk.com/)

[ODK] (https://opendatakit.org/)
