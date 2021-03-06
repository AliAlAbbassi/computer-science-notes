# Intensity Transformations and Spatial Filtering
The term spatial domain refers to the image plane itself, and image processing methods in this category are based on direct manipulation of pixels in an image. This is in contrast to image processing in a transform domain which, as we will discuss in Chapters 4 and 6, involves first transforming an image into the transform domain, doing the processing there, and obtaining the inverse transform to bring the results back into the spatial domain. Two principal categories of spatial processing are intensity transformations and spatial filtering. Intensity transformations operate on single pixels of an image for tasks such as contrast manipulation and image thresholding. Spatial filtering performs operations on the neighborhood of every pixel in an image. Examples of spatial filtering include image smoothing and sharpening. In the sections that follow, we discuss a number of “classical” techniques for intensity transformations and spatial filtering.

#### THE BASICS OF INTENSITY TRANSFORMATIONS AND SPATIAL FILTERING

```
g(x, y) = T[f(x, y)]
```

where f(x , y) is an input image, g(x , y) is the output image, and T is an operator on f defined over a neighborhood of point (x, y).
