___
[[image_data]]
[[Machine Learning]]
___
Within a RGB image this means determining distinctive image features such as color and or texture. Underwater imagery prone to different levels of light absorption, lens distortion, suspended matter and artifacts such as chromatic aberration can influence decision-making and classification of benthic features by users and algorithms.

Since reef benthos can show high variability, within the same category or even species adequate representation of each class in the training data is necessary for accurate predictions.

Features can be variables used for **classification** (colour, texture, shape of ear). Can be manually extracted, but in deep learning the algorithm learns features by itself and applies importance (Weight) to more frequent (?) features. Basically, the whole image has to much information anyway, so with features  the extraction of a ‘simplified’ view non-essential information is omitted. A vector of different features composes the classifier algorithm.

Pooling:
**Max pooling** is done to in part to help over-fitting by providing an abstracted form of the representation. As well, it reduces the computational cost by reducing the number of parameters to learn and provides basic translation invariance to the internal representation. **Max pooling** is done by applying a max filter to (usually) non-overlapping subregions of the initial representation. The other forms of pooling are: **average**, **general**.
___
## Image augmentation

Image augmentation

·       Size

·       Flips (horizontal reflection) of crops

·       Random changes in the brightness of images (training)

·       Changes in contrast and color (training)

·       (VGG) subtracting the mean RGB value per channel from each pixel (training)

·       Blurs (‘smoothing’ to reduce noise)