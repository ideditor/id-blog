---
layout: post
title:  "How to use Mapillary point data in iD"
description: "Learn about mapping features detected in Mapillary photos"
image: /assets/content/2020-01-15/03.png
date:   2020-01-15 18:30:00 -0500
author: Chris Beddow
organization: Mapillary
categories: tutorials
---
Mapillary has long been integrated into OpenStreetMap editors, and we are evaluating how to increase the value of both the imagery contributed by our community as well as the data extracted from that imagery. As it stands, Mapillary’s world-renowned computer vision capabilities provide an excellent tool for fixing maps in an unusual way. Outside of Mapillary imagery, we are seeing machine learning applied toward satellite imagery and telemetry data to help map roads and buildings. The coupling of computer vision and street-level imagery, however, offers a better view of the detailed reality maps have often lacked.

<iframe width="640" height="350" class="full-width bordered" src="https://embed-v1.mapillary.com/embed?version=1&filter=%5B%22all%22,%5B%22all%22,%5B%22%3E=%22,%22capturedAt%22,1575158400000%5D%5D,%5B%22==%22,%22pano%22,true%5D%5D&map_filter=%5B%22all%22,%5B%22all%22,%5B%22%3E=%22,%22captured_at%22,1575158400000%5D%5D,%5B%22==%22,%22pano%22,1%5D%5D&map_style=Mapillary streets&image_key=mMEJIfx9LWrBjQgzvG_PCg&x=0.48764933183654685&y=0.595925728396846&client_id=UTZhSnNFdGpxSEFFREUwb01GYzlXZzoyNGFlY2QwMmIwZTU2ZDVk&style=photo" frameborder="0"></iframe>
<figcaption>Map features extracted from a 360-degree panorama in Brazil</figcaption>

The OpenStreetMap iD editor has been evolving at a fast pace in recent years, thanks to a strong user base, dedicated developers, and integrations from multiple partners. At State of the Map US 2019 in Minneapolis, the iD developers [gave a preview](https://www.youtube.com/watch?v=cnML0w0qFCw&list=PLqjPa29lMiE3IqlKQlEwGlodMfJJHz-YV) of version 3 which is due to release sometime in 2020.

In the meantime, the user interface has already started changing, and late in 2019 this included the addition of a new Mapillary data layer called Map Features. This layer includes multiple classes of point data extracted from imagery uploaded to Mapillary. While a complete taxonomy of available point data is [listed in our API documentation](https://www.mapillary.com/developer/api-documentation/#points),  we have only included such features as benches, street lights, and cross walks, which have a clear one to one match in the OSM tagging schema.

![Mapillary map features and corresponding icons](/assets/content/2020-01-15/01.png){: .bordered}
{: .full-width}

The result is a collection of useful new data to enrich OpenStreetMap. The most powerful aspect of this for mapping communities is that data collection becomes extremely efficient: simply walk, cycle, or drive down a street, and use the Mapillary mobile application to capture imagery. Upload the imagery, then when it is finished uploading, new map features will be extracted in the form of point data that can be overlaid on the map.

![The Mapillary Map Features layer can be found in the Map Data menu on OSM iD](/assets/content/2020-01-15/02.png){: .bordered}
{: .full-width}

The map features layer can be activated in the Map Data menu. If you aren’t sure what an icon represents, simply hover over it for a hint. You can also click on the point and a Mapillary image looking at it will appear. This will help you verify that the map feature actually exists and see where it is positioned.

For example, we can check out a bench we detected from imagery near a city park. Clicking the bench, an image nearby loads up. Turning on the Mapillary image overlay, we can also see the location of this image.

![The bench is visible on the east side of the road](/assets/content/2020-01-15/03.png){: .bordered}
{: .full-width}

In the corner of the image, we can zoom in on the bench to see it next to the basketball court. We can then add a point to the map where the bench is, which looks pretty correct, next to one of the basketball hoops. Notice that a box appears around the bench as well as a detected pole—the boxes indicate what features on the map are visible in the current image.

Also notice on the opposite side of the street there are some trash bins—these are temporary and dynamic features which the residents put on the street for trash collection, so we probably should not map those.

![](/assets/content/2020-01-15/04.png){: .bordered}
{: .full-width}

Once the bench has been added to the map, we can take advantage of the detail provided by the street-level imagery to confirm that the bench is made of wood and has a backrest. Once that’s saved, then we can move on and map more features.

You may notice with an initial test that map features are not displayed in your area. To fix this, simply click the `Request Data` button to the right of the layer toggle.

![](/assets/content/2020-01-15/05.png){: .bordered}
{: .full-width}

While Mapillary traffic signs are automatically available everywhere globally by default, the other map features are available upon request. In the data request form, you can draw the area where you want to request data, or otherwise make a note to us that it’s a particular area name that you’re looking for, such as “Recoleta neighborhood of Buenos Aires”. This helps make sure you get specific data for your own project, and we also hope to learn more about what you’re accomplishing with the data, and what feedback you have as a result. It’s suggested that you keep the data request to a limited geographic size, such as at the neighborhood level of a big city or the entire boundary of a small town.

![An example data request](/assets/content/2020-01-15/06.png){: .bordered}
{: .full-width}

Using Mapillary map features in OpenStreetMap comes with some caveats. The data quality depends entirely on the device used to capture it, and the methodology of the Mapillary contributor. If the person is capturing during a rainstorm or low light conditions, this can complicate the quality, while tall buildings in city centers such as Chicago might obscure GPS signal and place the images offset from the road, affecting the spatial position of extracted data.

<iframe width="640" height="300" class="full-width bordered" src="https://embed-v1.mapillary.com/embed?version=1&filter=%5B%22all%22%5D&map_filter=%5B%22all%22%5D&map_style=OpenStreetMap&map_style=OpenStreetMap&image_key=eQ1IpS2JyqT0k6yJQT5okA&x=0.5000000000015811&y=0.5000000000671525&client_id=UTZhSnNFdGpxSEFFREUwb01GYzlXZzoyNGFlY2QwMmIwZTU2ZDVk&style=split" frameborder="0"></iframe>
<figcaption>Watch out for skyscrapers—they can complicate the GPS reading</figcaption>

If the GPS and camera lens are performing at their best, then the point data can be quite accurate. Remember that accuracy has multiple aspects: the positional accuracy and the classification accuracy.

We may correctly recognize a fire hydrant, but due to GPS issues it could be offset from the satellite image or reality by a few meters. OSM iD allows a great opportunity for the mapper to take a note of the detected data, and then reposition it more accurately according to local knowledge or other reference sources. Meanwhile, we may detect a utility pole, but it really might be the pole supporting a basketball hoop (notice in the example we used).

![Mapillary verifier tool](/assets/content/2020-01-15/07.png){: .bordered}
{: .full-width}

The classification accuracy is greatly improved if you verify the data beforehand using the [Mapillary verifier tool](https://help.mapillary.com/hc/en-us/articles/115001964171-Verifier-tool). The tool allows you and your collaborators to verify the classifications in the images quickly and efficiently, then updates the map data to remove false positives. This can save you a great amount of time once you actually start adding the data to OpenStreetMap. Make sure to ask about this when you request data, and we can include links to verification projects for you. You can also [set up a verification project on your own](https://help.mapillary.com/hc/en-us/articles/360025532692-Verification-projects), prior to a data request.

Try to give good details in the data request, as you’ll be sending this to me so I can better understand what impact the data has and how to make it more valuable in the future. Once you’ve submitted the request, you’ll get a message saying it’s approved and you’re ready to start mapping!

Questions? Feedback? Ideas? [Drop us a message](mailto:osm@mapillary.com)!

/ Chris
