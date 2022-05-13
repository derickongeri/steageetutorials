# Image Enhancement

## Cloud Masking

### Using Landsat 8 QA band to mask clouds

```js
// This example demonstrates the use of the Landsat 8 QA band
// to mask clouds.

// Load Landsat 8 TOA data.
var l8 = ee.ImageCollection("LANDSAT/LC08/C01/T1_TOA");

// Function to cloud mask from the quality band of Landsat 8.
function maskL8(image) {
  var qa = image.select("BQA");
  // Make a mask of possible values for high cloud confidence.
  // See https://landsat.usgs.gov/collectionqualityband
  var mask = qa
    .eq([2800, 2804, 2808, 2812, 6896, 6900, 6904, 6908])
    // If any of these combinations occur, return 1 (logical or)
    .reduce("max")
    // Negate to get not high confidence of cloud.
    .not();

  return image.updateMask(mask);
}

// Map the function over one year of data and take the median.
var composite = l8.filterDate("2016-01-01", "2016-12-31").map(maskL8).median();

// Display the results in a cloudy place.
Map.setCenter(114.1689, 22.2986, 12);
Map.addLayer(composite, { bands: ["B4", "B3", "B2"], max: 0.3 });
```

### Using Landsat 8 Fmask band To mask Cloud

```js
// This example demonstrates the use of the Fmask band to mask
// clouds in surface reflectance (SR) data.  It is suitable
// for use with any of the Landsat SR datasets.

// Load Landsat 8 surface reflectance data
var l8sr = ee.ImageCollection("LANDSAT/LC8_SR");

// Function to cloud mask from the Fmask band of Landsat 8 SR data.
function maskL8sr(image) {
  var qa = image.select("cfmask");
  // Make a mask to exclude cloudy pixels.
  var mask = qa.neq(2).and(
    // shadow
    qa.neq(4)
  ); // cloud

  // Return the masked image, scaled to [0, 1].
  return image.updateMask(mask).divide(10000);
}

// Map the function over one year of data and take the median.
var composite = l8sr
  .filterDate("2016-01-01", "2016-12-31")
  .map(maskL8sr)
  .median();

// Display the results.
Map.setCenter(116.3809, 39.9297, 10);
Map.addLayer(composite, { bands: ["B4", "B3", "B2"], min: 0, max: 0.2 });
```

### MODIS Cloud Masking Example

```js
// This example uses the Sentinel-2 QA band to cloud mask
// the collection.  The Sentinel-2 cloud flags are less
// selective, so the collection is also pre-filtered by the
// CLOUDY_PIXEL_PERCENTAGE flag, to use only relatively
// cloud free granule.

// Load Sentinel-2 TOA reflectance data.
var s2 = ee.ImageCollection("COPERNICUS/S2");

// Function to mask clouds using the Sentinel-2 QA band.
function maskS2clouds(image) {
  var qa = image.select("QA60");

  // Bits 10 and 11 are clouds and cirrus, respectively.
  var cloudBitMask = Math.pow(2, 10);
  var cirrusBitMask = Math.pow(2, 11);

  // Both flags should be set to zero, indicating clear conditions.
  var mask = qa
    .bitwiseAnd(cloudBitMask)
    .eq(0)
    .and(qa.bitwiseAnd(cirrusBitMask).eq(0));

  // Return the masked and scaled data.
  return image.updateMask(mask).divide(10000);
}

// Map the function over one year of data and take the median.
var composite = s2
  .filterDate("2016-01-01", "2016-12-31")
  // Pre-filter to get less cloudy granules.
  .filter(ee.Filter.lt("CLOUDY_PIXEL_PERCENTAGE", 20))
  .map(maskS2clouds)
  .median();

// Display the results.
Map.setCenter(-2.04, 48.6411, 13);
Map.addLayer(composite, { bands: ["B3", "B2", "B1"], min: 0, max: 0.3 });
```

### Sentinel 2 QA band Cloud Masking

```js
// This example uses the Sentinel-2 QA band to cloud mask
// the collection.  The Sentinel-2 cloud flags are less
// selective, so the collection is also pre-filtered by the
// CLOUDY_PIXEL_PERCENTAGE flag, to use only relatively
// cloud free granule.

// Load Sentinel-2 TOA reflectance data.
var s2 = ee.ImageCollection("COPERNICUS/S2");

// Function to mask clouds using the Sentinel-2 QA band.
function maskS2clouds(image) {
  var qa = image.select("QA60");

  // Bits 10 and 11 are clouds and cirrus, respectively.
  var cloudBitMask = Math.pow(2, 10);
  var cirrusBitMask = Math.pow(2, 11);

  // Both flags should be set to zero, indicating clear conditions.
  var mask = qa
    .bitwiseAnd(cloudBitMask)
    .eq(0)
    .and(qa.bitwiseAnd(cirrusBitMask).eq(0));

  // Return the masked and scaled data.
  return image.updateMask(mask).divide(10000);
}

// Map the function over one year of data and take the median.
var composite = s2
  .filterDate("2016-01-01", "2016-12-31")
  // Pre-filter to get less cloudy granules.
  .filter(ee.Filter.lt("CLOUDY_PIXEL_PERCENTAGE", 20))
  .map(maskS2clouds)
  .median();

// Display the results.
Map.setCenter(-2.04, 48.6411, 13);
Map.addLayer(composite, { bands: ["B3", "B2", "B1"], min: 0, max: 0.3 });
```
