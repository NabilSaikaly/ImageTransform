# ImageTransform
Solution to the UIUC Image Transform Problem/Programming Project.
Implementation of the functions:
- `illinify` to transform each Pixel to Illini Orange or Illini Blue after evaluating its proximity to these colors using Euclidean Distance and Trigonometric Logical Approach.
- `createSpotlight` To create a spotlight pattern on a given point in the picture.
- `watermark` to insert a watermark to a specific picture.

*The given and requirements by/from UIUC are summarized in this readme file*

# HSLAPixel Class
HSL Color space is used (Hue, Saturation and Luminance of the color).

Source: UIUC from Adobe Technical Guides page on "The HSB/HLS Color Model"

## Hue
Hue (denoted as h) defines the color itself, for example, red in distinction to blue or yellow.

The values for the hue axis run from 0–360° beginning and ending with red and running through green, blue and all intermediary colors like greenish-blue, orange, purple, etc.
There are two main hues that we'll use later in this assignment:
- "Illini Orange" has a hue of 11.
- "Illini Blue" has a hue of 216.

<img width="250" alt="image" src="https://user-images.githubusercontent.com/98900886/230672332-e17bf4d8-427e-427b-af6e-20d4fd0d0319.png">


## Saturation
Saturation (denoted as s) indicates the degree to which the hue differs from a neutral gray. The values run from 0%, which is no color saturation, to 100%, which is the fullest saturation of a given hue at a given percentage of illumination.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/98900886/230672566-33bde629-87ff-413e-963c-d9c31cd41b8d.png">

## Luminance
Luminance (denoted as l) indicates the level of illumination. The values run as percentages; 0% appears black (no light) while 100% is full illumination, which washes out the color (it appears white).

<img width="400" alt="image" src="https://user-images.githubusercontent.com/98900886/230672650-40091f89-e120-4110-a594-1533239782ff.png">

## HSL Color Space
<img width="400" alt="image" src="https://user-images.githubusercontent.com/98900886/230672726-dc8709cb-13cc-4e5d-b132-004f43d743ab.png">
The full HSL color space is a three-dimensional space, but it is not a cube (nor exactly cylindrical). The area truncates towards the two ends of the luminance axis and is widest in the middle range. The ellipsoid reveals several properties of the HSL color space:

- At l=0 or l=1 (the top and bottom points of the ellipsoid), the 3D space is a single point (the color black and the color white). Hue and saturation values don’t change the color.
- At s=0 (the vertical core of the ellipsoid), the 3D space is a line (the grayscale colors, defined only by the luminance). The values of the hue do not change the color.
- At s=1 (the outer shell of the ellipsoid), colors are vivid and dramatic!


# PNG Class
PNG stands for Portable Network Graphics

## For loading and saving PNG files:
- `bool PNG::readFromFile(const std::string & fileName)` loads an image based on the provided file name, a text string. The return value shows success or failure. Takes a direct reference to the memory is being passed, similar to a pointer.
- `bool PNG::writeToFile(const std::string & fileName)` writes the current image to the provided file name (overwriting existing files).
## For Retrieving pixel and image information:
- `unsigned int PNG::width()` const returns the width of the image.
- `unsigned int PNG::height()` const returns the height of the image.
- `HSLAPixel & getPixel(unsigned int x, unsigned int y)` returns a direct reference to a pixel at the specified location.


# Objective
Implementation required for the three functions:
- illinify
- spotlight
- watermark

## illinify
To illinify an image is to transform the hue of every pixel to Illini Orange (11) or Illini Blue (216). The hue of every pixel should be set to one or the other of these two hue values, based on whether the pixel's original hue value is closer to Illini Orange or Illini Blue. 
Note: The values are arranged in a logical circle.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/98900886/230673480-c9d7b4ba-30f5-4607-b074-04792b28bdc2.png">

## spotlight
To spotlight an image is to create a spotlight pattern centered at a given point (centerX, centerY).
A spotlight adjusts the luminance of a pixel based on the distance between the the pixel and the designated center by decreasing the luminance by 0.5% per 1 pixel unit of Euclidean distance, up to an 80% decrease in luminance at most.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/98900886/230673529-c0647aae-bc29-4895-9a86-a9eaea81fc8f.png">

## watermark
To watermark an image is to lighten a region of it based on the contents of another image that acts as a stencil.
You should not assume anything about the size of the images. However, you need only consider the range of pixel coordinates that exist in both images; for simplicity, assume that the images are positioned with their upper-left corners overlapping at the same coordinates.
For every pixel that exists within the bounds
of both base image and stencil, the luminance of the base image should be increased by +0.2 (absolute, but not to exceed 1.0) if and only if the luminance of the stencil at the same pixel position is at maximum (1.0).

# Testing and Evaluation
To run the code and test the implemented functions run the following commands:
1. Navigate to the directory in which `makefile` is available.
2. `make` to compile the files
3. `./ImageTransform` to compile the ImageTransform.cpp file
4. `make test` to compile the test files
5. `./test` to run the tests
- Note: `make clean` after cloning this repo and before implementing.
