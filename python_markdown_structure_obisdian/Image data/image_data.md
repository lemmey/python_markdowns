___
[[Machine Learning]]
___
## Basics
An image has two dimensions, defined by the amount of pixels in direction X and Y. Every pixel is defined through an intensity value, determined through the amount of light (of a specific wavelength).

Grayscale: Pixel can have values between 0 (black) and 255 (white). Therefore the function describing the pixel => F(px. position X/px. Position Y) = 0 - 255

RGB: F(x/y) = (red(x/y), green(x/y), blue(x/y))

Some terminology:
___
* Image classification: Predicting the class of an object in an image, by input of an image with a single object. Output: A class label (integer that is mapped to a string (0 == Not a cat, 1 == Cat)

*  Performance indicator: Mean classification error across the predicted label(s).

* Object localization: Identifying the presence of an object in an image and drawing a bounding box around the area of likelihood. Input is an image with single or multiple objects. Output, one or more bounding boxes.

* Single-object localization is a simpler approach, limiting localization to a single class of object.

* Performance: The distance between predicted and expected bounding box for a single class.