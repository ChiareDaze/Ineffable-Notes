### Overview

**What is computer vision?**
That branch of cs that tries to emulate the human visual system and understand a scene context.


recupera dagli appunti

**Binary images**
A pixel can take either value 0 for black pixel or value 1 for the white one. So it's possible to encode each pixel just one bit.
Binary images are very efficient in terms of space, although their application as limited to very specific tasks such as fingerprints

**Grayscale**
A pixel takes a value on the grayscale encoded in eight bites. It allows pixels to take values between 0 and 255.

>[!warning]
>When a pixel value is below 0, it is treated as a black pixel and a pixel above 255 is treated as a white pixel

**Indexed images**
Used for gif images which have a low framerate.
This model uses colors within a palette. It means that a pixel's values is encoded using the corresponding index within the palette.

**Colour**
It is the most popular pixel representation method. It encodes each pixel using three channels: the first byte encodes the red component, the second one encodes the green component and the third one encodes the blue component.

With that, it's possible to view $RGB$ as 3D matrices, where the width denotes the number of columns, the height denotes the number of rows and the depth denotes the number of channels for the image.
Sometimes, it's possibile (mostly for the png images) to consider a fourth channel encoding the $\alpha$ channel, which denotes a pixel's transparency, although this is rarely used in computer vision.

