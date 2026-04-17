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

**Filters**
The OpenCV library also supports filtering, which consists in applying some features (such as blurring or sharpening) to an input image by *convolution*.

**Convolution**
In a more general way, convolution is a mathematical operation that uses an input image and a kernel, which is a small (typically odd-dimensioned) matrix containing the weights to apply to the image, in order to produce a new output image

---

**Change detection**
It is the process of finding and mapping what has changed in a scene by comparing a reference frame with a current frame of the same area. The goal is to produce a change map, often binary o multi-class, that highlights where relevant differences occurred between the two acquisition.

>[!info] Change Map
>A change map is an output image where each pixel indicates whether a change occurred at that location
>$$
>CM(x,y) = 0 \text { (black) } \to \text { unchanged }
>$$
>$$
>CM(x,y) = 1 \text { (white) } \to \text { changed }
>$$

**What does "change" mean?**
In Computer Vision, a change can be interpreted as any modification of pixel values observed in the current frame with respect to a fixed reference frame. Such pixel-level modifications may be caused by:
- Appearance of new objects or regions
- Modification of object of regions properties
- Disappearance of existing object or region
- Movement or displacement of objects or region

In other words, relative to the reference frame, any event that causes a relevant change in a pixel region in the current frame, e.g. by the appearance, disappearance, modification, or movement/displacement of scene elements, can be considered a change

---

