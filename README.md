# Image-Processing
## Abstract
The task was to segment and track the trajectories of two bacteria in a petri dish from a video. Binary thresholding, background subtraction, and morphological filtering were used to process the individual frames in the video. This made it possible to extract each bacterium's center of mass and track this information over time in order to map the two bacterial trajectories. 

## Methods
Looking at a single frame, the mean pixel value of the bacteria is compared to the distribution of pixel values across the entire image. Then, the median pixel value of the entire image is subtracted from each pixel value in order to create a clear divide between background pixels and bacteria pixels. The median is used because compared to the mean, the median is not skewed by extreme values, such as brief moments of intense brightness that lights up an entire frame.This makes it possible to use binary thresholding to create an image that only consists of the two bacteria (any pixel that is part of a bacteria has the value 1 and all others are set to 0). The exact threshold of pixel value to subtract the background is chosen by looping through various potential threshold values and choosing the one that appeared to generate the best image. Morphological filtering, including erosion and dilation, are used to clean up these binary images. Finally, the centers of mass of the two bacteria are found for each frame in the movie. The locations of these centroids are tracked across frames in order to determine the trajectory of each bacterium. 

## Results and Discussion
From the histogram below, it's apparent that binary thresholding alone will not work to isolate the bacteria because the mean pixel value of the bacteria is within the boundaries of the range of common background pixel values. In other words, the bacteria gets "lost" in the background. 

<img src="https://github.com/shoshireich/Image-Processing/blob/master/Figures/PixelValues.png" width="60%">

Even though there are many objects in the image, the image has low resolution, and the bacteria are similar in pixel intensity to the background, somehow our brains are still able to find the bacteria in the video. This is possible because the bacteria move over time.
Background subtraction allows for the creation of a "background" image composed of pixels whose values remain fairly constant over time.
The information extracted from these processed images can be used effectively to plot the bacterial trajectories.

<img src="https://github.com/shoshireich/Image-Processing/blob/master/Figures/BacteriaTrajectories.png" width="50%">

