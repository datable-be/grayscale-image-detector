# grayscale-image-detector
Python function that takes an image file path as input and determines whether the image is quasi-monochrome with an RGB channel or a color image containing a black and white photo.

* It checks if the image has an RGB channel by examining its color bands. If the image doesn't have three color bands (R, G, B), it returns **False**.

* If the image has an RGB channel, it checks several conditions to determine if it's **quasi-monochrome** (i.e. very low saturation or grayscale):
  * If the image is in RGBA mode (with an alpha channel), it checks if the alpha channel is mostly white (i.e., transparent). If more than 99% of the alpha pixels are white, it returns **True**.
  * If the image is in L mode (grayscale), it returns **True** since grayscale images are considered monochrome.
  * If the image is in RGB mode (color), it checks if all three color channels (R, G, B) have the same extrema, which suggests the image has very low color saturation. If this condition is met, it returns **True**. Additionally, it checks if the image has very low color saturation by converting it to the HSV color space and examining the saturation channel (S). If more than 95% of the pixels have a saturation value less than 32, it returns **True**.

* If none of the above conditions are met, it returns **False**, indicating that the image is neither quasi-monochrome with an RGB channel nor a color image containing a black and white photo.
