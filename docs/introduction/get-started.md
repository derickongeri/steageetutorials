# Prerequisites

## Sign Up for Earth Engine Account

To sign up for an earth engine account, visit the [`Google earth engine homepage`](https://earthengine.google.com) and click on the sign up link at the top-right conner of the page. The earth engine homepage also contains a tonn of information about earth engine and is a good place to get familiar with google earth engine platform, data catalog, terms of use, and case studies. The sign up link can also be found at the bottom of the page.

````{sidebar} **My sidebar title**
```{figure} ../_static/code_editor.png
---
width: 60%
figclass: margin-caption
alt: My figure text
name: myfig5
---
```
````

:::{note}
Earth Engine is available for commercial use, and remains free for academic and research use. [the terms of use](https://earthengine.google.com/terms/)
:::

## Earth Engine JavaScript Playground

The Code Editor is an interactive environment for developing Earth Engine applications (Figure 1). The center panel provides a JavaScript code editor. Above the editor are buttons to save the current script, run it, and clear the map. The Get Link button generates a unique URL for the script in the address bar. The map in the bottom panel contains the layers added by the script. At the top is a search box for datasets and places. The left panel contains code examples, your saved scripts, a searchable API reference and an asset manager for private data. The right panel has an inspector for querying the map, an output console, and a manager for long-running tasks. The help button help in the upper right contains links to this Guide and other resources for getting help. Learn more from the Code Editor guide and the Get Help guide.

```{figure} ../_static/code_editor.png
---
width: 60%
figclass: margin-caption
alt: My figure text
name: myfig5
---
And here is my figure caption, if you look to the left, you can see that COOL is in big red letters. But you probably already noticed that, really I am just taking up space to see how the margin caption looks like when it is really long :-)
```

## Earth Engine data-types

The remainder of the guides are intended to illustrate important concepts about data types such as:

- Image, The fundamental raster data type in Earth Engine.
- ImageCollection, a stack or time-series of images.
- Geometry, the fundamental vector data type in Earth Engine.
- Feature, or a Geometry with attributes.
- FeatureCollection, or a set of features.
- Reducer, an object used to compute statistics or perform aggregations.
- Join, or how to combine datasets (Image or Feature collections) based on time, location, or an attribute property.
- Array, for multi-dimensional analyses.
