# A few notes on using images that have been cropped or resized for analyses of size and shape.

This may go without saying, but some changes to your image can alter the size information in it. This is important to consider when doing anything where you might be need this information.

## Make sure to know your scale for the raw image.
For most digitally captured images on a microscope it computes the scale factor (i.e. pixels/mm or px/mm) automatically. However, the software does need to know which objective you are using!! Obviously the absolute image size will be the same even as you go to higher objectives. So make sure you have this set! Depending on your system, it may not include this as meta-data though. 

## **Never modify the raw image itself, but a copy of the raw image**
Enough said. Make sure you always keep the raw data and just modify copies of the images. This was you can always go back and check things!!

## Cropping images
- Cropping an image by itself does not change the scale. i.e. if you had 200px/mm before, and you crop the image, the number of px/mm has not changed. What has changed is the overall image size. However, this does influence the scale if you then resize the image!
- Always keep the ratios (width and length) the same when cropping. This is usually just a precaution, but it is important to keep this consistent. Most images have a ratio of 1.32815 or so (1360 x 1024, 4080 x 3072). Others are just slightly off this (632 x 480). So if you crop the image try to crop it with this ratio (or as close as you can get it).
- Note that cropping image will change the scale you will want to use if you are resizing.

## Resizing images.
- resizing images (say from 4080 x 3072 to 632 x 480) will change the scale (i.e the number of px/mm). So make sure you measure the new scale after resizing (in px/mm or mm/px or whatever is the appropriate dimensions for your work). 
- cropping an image and resizing it will result in a different scale than if you just resized the image. So make sure to first crop (see above for notes), then resize, and then measure the new scale (px/mm). 
- You can do the recalculation fairly easily:

  d = (a x b) / c
  
  With
  a = width of full size original image in number of pixels.
  
  b = mm/px for the full size image.
  
  c = width of resized image in number of pixels.
  
  So the numerator gives the width of the original full size image in mm, scaled by the width of the resized image in pixels.
  
  d = mm/px for the resized image.
  
- For our current microscope system at McMaster (the Olympus BX 43 with the DP10 camera), we capture most wing images using either the 2X or 4X at full (4080 x 3072) resolution. For rescaling during the spline (i.e. resizing image to 632 x 480).

 **With the 4X objective:**
 
 For the original image
 a = 4080 px, b = 0.0005375 mm/px,
 
 a x b = 2.193 mm (width)

After resizing image to 632 x 480 px (c = 632)

d =  0.00347 (mm/px)

**With the 2X objective:**

 For the original image
 
 a = 4080 px, b = 0.00108 mm/px,
 
 a x b = 4.4064 mm (width)

After resizing image to 632 x 480 px (c = 632)

d =  0.00697 mm/px


## **Important notes for cropped (and resized) images for scale**

- If you are cropping images for splining (typically for an image taken at 2X), and you crop prior to resizing images (which is easier I gather), then you need to adjust the scale that you will use in the Python script to generate the `.asc` file. 
    - Example you crop a 2X image (4080px X 3072px which is 4.4mm X 3.3mm, or a scale of 0.00108mm/px) to 3580px X 2696px. The new width of the image is 3580 px * 0.00108 mm/px = 3.8664 mm. Now you resize this image to 632px X 480px. The scale for the resized image is now 3.8664 mm/632px = 0.006118 mm/px.
    
## Greyscale VS colour
- If you are using your images only for splining wings (or measuring wing size). They you can use greyscale.
- If you are using the images only for trichome (cell) counts, then use colour (and maximum camera resolution). 
- if you are using the images for both, produce them in colour (and maximum resolution), but change to greyscale at the same time as you resize them.
- Changing to greyscale does not influence the resolution by itself (but the resizing does).

## Notes on bit depth
- most images we need are 8 bit. Either 8 bit greyscale or 3x8bit (24 bit) colour.
- We don't need to use the 14 bit greyscale for wing size, splining. 
- We don't need to use the 12 bit colour for trichome counts.
- The bit depth influences how many colours at each pixel, but not resolution.
