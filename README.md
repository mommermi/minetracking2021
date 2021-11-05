# Mine Tracking Sample Dataset

This repository contains sample image data for our Mine Tracking Workshop. Feel free to
download and inspect the data. To participate in the workshop, please have the data available on your computer and [label-studio](https://labelstud.io/) installed. 


## Data 

The image data were obtained by the [Sentinel-2 satellites](https://sentinel.esa.int/web/sentinel/missions/sentinel-2) that are operated by the European [Copernicus Programme](https://www.copernicus.eu/en). Observations are available for three different mining sites:

* Calendaria Copper Mine (0854, Chile), [Google Maps](https://www.google.com/maps/place/27%C2%B031'05.5%22S+70%C2%B017'24.4%22W/@-27.5231827,-70.3091445,13.8z/data=!4m5!3m4!1s0x0:0x0!8m2!3d-27.5182!4d-70.2901), 8 observations
* Kokpatas Gold Mine (3548, Uzbekistan), [Google Maps](https://www.google.com/maps/place/42%C2%B015'42.8%22N+63%C2%B053'30.1%22E/@42.2613275,63.8711426,9110m/data=!3m1!1e3!4m5!3m4!1s0x0:0x0!8m2!3d42.2619!4d63.8917), 10 observations
* Himmetdede Gold Mine (55350, Turkey), [Google Maps](https://www.google.com/maps/place/38%C2%B057'01.8%22N+35%C2%B003'31.0%22E/@38.948383,35.0539053,4265m/data=!3m1!1e3!4m5!3m4!1s0x0:0x0!8m2!3d38.9505!4d35.0586), 3 observations

Typically, there is a time difference of about 3 months between two successive observations of each site. Images are available as `png` image files of size 1000x1000 pixels covering 10x10 km on the ground. For each site, a `gif` animation at lower image resolution is available, too, to highlight changes between the individual observations caused by mining operations, weather conditions, and seasonal variations.  

## Labeling

Our goal is to label images like those present in this repository (and many more in the future) and thereby produce training data for Deep Learning Computer Vision models to automatically detect changes in mining sites that will be indicative of ongoing mining operations. 

### Label-Studio Setup

In order to label our satellite images, we will utilize the open-source software [label-studio](https://labelstud.io/). Once installed, you have to sign up and generate a user account (your email address and password will only be stored on your computer). To label data, you have to create a new project (`create` button, top right corner). After providing a meaningful name to the project, you can click on the `data import` tab and upload the `png` image files from this repository, and finally, click the `labeling setup` tab and select *semantic segmentation with polygons*. 

In the following window you can choose a `code` view; click this button and replace the displayed code with the following code snippet:

```
<View>
  <Header value="$image"/>
  <Image name="image" value="$image" zoom="true"/>
  <PolygonLabels name="label" toName="image" strokeWidth="3" pointSize="small" opacity="0.9">
    <Label value="Pit" background="red"/>
    <Label value="Infrastructure" background="blue"/>
    <Label value="Outline" background="yellow"/>    
  </PolygonLabels>
</View>
```

This will make sure that you are able to label the three different categories that we are interested in for this study: `Pit`, `Infrastructure` and `Outline` (see below). Once everything is setup properly, you should be able to get started with labeling the data. 

### Labeling 

We use the following labels in this workshop:

* `Pit`: use this to draw the outlines of mining pits
* `Infrastructures`: use this to draw the outlines of accumulations of mining infrastructure like buildings and vehicles (not necesserily individual instances thereof)
* `Outline`: use this to draw the outlines of the overall mine grounds

### Submitting your labels

If you would like to submit your generated labels to us, please use the `export` button in label-studio (top right corner), save your labels in the `json` format and send your results to [miningworkshop21@gmail.com](mailto:miningworkshop21@gmail.com).



