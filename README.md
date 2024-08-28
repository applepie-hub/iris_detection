IrisLocalization.py
===================

The function IrisLocalization(images) does the following:

It uses a Bilateral filter to remove the noise by blurring the image

We project the image coordinates in the horizontal and vertical directions, and find the minimum(as the minimum would be a dark region of the pupil) to find the approximate center of the pupil.

We next use this approximate center to binarize a 120 x 120 space around the pupil, as defined in the paper, to re-estimate the pupil center.

We perform Canny edge detection on a masked image to get only a few edges around the pupil. If the image was not masked we would get a lot of edges of the eyelashes,etc.

We then implement Hough transformation on the edged image to detect all possible circles in the image. We take the Hough circle that has center closest to the pupil center found as the pupil boundary.

The outer boundary is then drawn by adding 53 to the radius of the inner circle.

The list “boundary” stores all the images with boundaries drawn, while the list “centers” stores the center coordinates.

IrisNormalization.py
====================

We sequentially load each image from the list boundary returned by the previous function and initialize an empty list to store the normalized images.

In order to project the polar coordinates onto the cartesian plane, we only need to focus on the region between the boundaries.

We define an equally spaced interval over which the for loop iterates to convert polar coordinates to cartesian coordinates, using x=rcos(theta) and y=rsin(theta).

We resize the image to a rectangular 64x512 sized image.

ImageEnhancement.py
In this function, we enhance the image using Histogram Equalization to increase the contrast of the image for better feature extraction.

FeatureExtraction.py
====================

The functions ‘m’ and ‘gabor’ help in calculating the spatial filter defined in the paper
