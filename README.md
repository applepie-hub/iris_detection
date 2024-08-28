IrisExtraction.py
===================

The function IrisLocalization(images) does the following:

It uses a Bilateral filter to remove the noise by blurring the image

We project the image coordinates in the horizontal and vertical directions, and find the minimum(as the minimum would be a dark region of the pupil) to find the approximate center of the pupil.

We next use this approximate center to binarize a 120 x 120 space around the pupil, as defined in the paper, to re-estimate the pupil center.

We perform Canny edge detection on a masked image to get only a few edges around the pupil. If the image was not masked we would get a lot of edges of the eyelashes,etc.

We then implement Hough transformation on the edged image to detect all possible circles in the image. We take the Hough circle that has center closest to the pupil center found as the pupil boundary.

The outer boundary is then drawn by adding 53 to the radius of the inner circle.

The list “boundary” stores all the images with boundaries drawn, while the list “centers” stores the center coordinates.

The functions ‘m’ and ‘gabor’ help in calculating the spatial filter defined in the paper

Iris_classification_3.ipynb
============================

This notebook building an ai model to detect users by given augmented iris dataset. 
We used pretrained models like DenseNet210, InceptionV3, InceptionResNetV2 and compared their accuracy.

Second.ipynb
=============

This notebook peform a user identify process and give us result with False Acceptance Rate, False Rejection Rate, Equal Error Rate, and F1score.



