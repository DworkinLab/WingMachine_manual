# A few notes on using images that have been cropped or resized for analyses of size and shape.

This may go without saying, but some changes to your image can alter the size information in it. This is important to consider when doing anything where you might be need this information.

## Make sure to know your scale for the raw image.
For most digitally captured images on a microscope it computes the scale factor (i.e. pixels/mm or px/mm) automatically. However, the software does need to know which objective you are using. Obviously the absolute image size will be the same even as you go to higher objectives. So make sure you have this set!

## **Never modify the raw image itself, but a copy of the raw image**
Enough said. Make sure you always keep the raw data and just modify copies of the images. This was you can always go back and check things!!

## cropping images
- Cropping an image by itself does not change the scale. i.e. if you had 200px/mm before, and you crop the image, the number of px/mm has not changed. What has changed is the overall image size.
- Always keep the ratios (width and length) the same when cropping. This is usually just a precaution, but it is important to keep this consistent. Most images have a ratio of 1.32815 or so (1360 x 1024, 4080 x 3072). Others are just slightly off this (632 x 480). So if you crop the image try to crop it with this ratio (or as close as you can get it).

# resizing images.
- resizing images (say from 4080 x 3072 to 632 x 480) will change the scale (i.e the number of px/mm). So make sure you measure the new scale after resizing (in px/mm or mm/px or whatever is the appropriate dimensions for your work).
- cropping an image and resizing it will result in a different scale than if you just resized the image. So make sure to first crop (see above for notes), then resize, and then measure the new scale (px/mm). 
