# Working with Images


## Hallo Image
Let's take a look at how images appear in the editor. Below is an example of a Sentinel 2 image in the visible bands. 
.. image:: "C:\Users\Rejoice\Documents\bands\imageee.png"
   :width: 600
Images in the Earth Engine are made up of bands. This image is a combiantion of 3 bands blue red and green, combined together.
 To display an image, you will have to specify the bands. 
 ```js
'''var image = ee.ImageCollection('COPERNICUS/S2_SR')  //
                .filterBounds(ee.Geometry.Point(34.83, -19.3631))
                .filterDate('2019-01-01', '2019-12-31');
Map.centerObject(image, 11);
Map.addLayer(image, {bands: ['B4', 'B3', 'B2'], min: 0, max: 2000});// specify the bands to display
```
Since bands appear grey in the Earth Engine by default, to vizualise a single band or a collection of bands, a palette can be added to the bands to give it colour.

Without colour
```js
// elevation image
var image = ee.Image('CGIAR/SRTM90_V4');

// Zoom to a location.
Map.setCenter(34.83, -19.3631, 9); // Beira Port Mozambique

// Display the image on the map with default colour
Map.addLayer(image, {min: 0, max: 3000}, 'custom visualization');
```
..image:: "C:\Users\Rejoice\Documents\bands\greyscale.png"
  :width: 600
  
With colour
```js
var image = ee.Image('CGIAR/SRTM90_V4');
Map.setCenter(34.83, -19.3631, 9);
Map.addLayer(image, {min: 0, max: 3000, palette: ['blue', 'green', 'red']},
    'custom palette');
```
..image:: "C:\Users\Rejoice\Documents\bands\colour.png"


## Apply a Computation to an Image

## Apply a Spatial Reduction to an Image

## Exporting an Image
