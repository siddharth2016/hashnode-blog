## Brocading Naruto - A Computer Vision Activity

While learning how to do image processing, there are always two terms that we come across from time to time, that is, Convolution and Correlation. This article focusses on Correlation aspect of image processing, that is widely used in image enhancement computer vision applications. Here I have taken one of my favorite anime character Naruto, to help him look awesome among his friends !

---

## Convolution vs Correlation

Convolution involves 2 matrices (in Linear algebra context) when combined in a particular fashion will result in a 3rd matrix that can be termed as convoluted matrix. Here, one matrix is our image and another one is what we call a kernel (a weight matrix), our kernel's center position is placed on input image's pixel (source) and its surrounding pixels will determine the nature of pixel in output image (destination). If the resultant of surrounding pixels is less than the source pixel, then destination pixel will be blurred and if the resultant is greater than source pixel then destination pixel will be sharpened.

Image Correlation is a full-field image analysis method, based on gray value digital images, that can determine the contour and the displacements of an object under load in three dimensions. Correlation and Convolution are very much similar, both involves dot product of pixels from kernel weights in order to find the destination pixel either to be enhanced or blurred. Here I will be using a kernel with both negative and positive weights, so that the image can be blurred and sharpened at the same time, giving rise to an embossed effect on image.

I think it's pretty much clear what is Convolution and how Correlation can be used interchangeably with it. If you want to look further into this, do visit [Convolution vs Correlation](https://stackoverflow.com/questions/20321296/convolution-vs-correlation).

Now let us move to the most crucial part, that is, writing our python script !

## Steps Involved

1. Import the required libraries.
2. Define class Brocade, that will contain our kernel and function definition.
3. Then run the script.

## Code

```python
# Import necessary libraries

import cv2
import numpy as np
import imutils
```

`cv2` will be used for filtering our image whose concept involves correlation, `numpy` will be helpful to merge original and resulting image during the display and `imutils` will be used to resize the image (imutils, is what i prefer for small image processing tasks because of clean and clear function declarations, that are easy to remember).

```python
# Define your Brocade class
class Brocade:

    def __init__(self, imageName):
        self._img = cv2.imread(imageName, cv2.IMREAD_COLOR)
        self._img = imutils.resize(self._img, 600)
        self._grayimg = cv2.cvtColor(self._img, cv2.COLOR_BGR2GRAY)

        # Kernel to Brocade the image
        self._kernel3 = np.array([[-2, -1, 0],
                                  [-1, 1, 1],
                                  [0, 1, 2]], dtype = np.float64)

    def getOrigImg(self):
        return self._img
    def getGrayImg(self):
        return self._grayimg
    
    # Member function to apply kernel on Filter of CV
    def applyFilter(self):
        img = self._img.copy()
        filtered = cv2.filter2D(img, -1, self._kernel3)

        return filtered
```

Define the constructor, by reading image (BGR and Gray) and defining required kernel. Here your creativity comes into play, go and change the kernel to whatever value you want and examine the results. Also define `getOrigImg` and `getGrayImg` methods. 

`applyFilter` method takes our BGR image and pass it to `cv2.filter2D` function of OpenCV3 that does correlation behind the scene and the filtered image is returned for display.

```python
# Now some real work :D !
if __name__ == "__main__":
    
    B = Brocade("naruto.jpg") # Image path
    img = B.getOrigImg()
    grayimg = B.getGrayImg()
    filtered = B.applyFilter()  # filter2D applies Correlation

    # Join horizontally, original and filtered image for display
    res = np.hstack((img, filtered))
    
    cv2.imshow("Result", res)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
```

Now if you are running the same script, call the main function. Here, Brocade class takes our `naruto.jpg` image and applies the filter. Both original and filtered images are joined using numpy function `hstack`, that joins arrays horizontally.

## Output

Left is input image and Right is the output image.

![brocaded naruto](https://cdn.hashnode.com/res/hashnode/image/upload/v1607150026469/Pgw8I-BvY.png)

---

That's it from me today ! I hope you enjoyed and learned something new from this article. If you faced any errors or any other problem, please feel free to comment or mail me, I will try my best to edit or solve it as soon as possible. If you liked it, please share and more than that, apply this script to other images and see how awesome they look !

Github [link](https://github.com/Siddharth2016/Opencv-Python-Computer-Vision/blob/master/brocadeNaruto.py) to the whole python script.

Stack Overflow [link](https://stackoverflow.com/questions/26857829/does-filter2d-in-opencv-really-do-its-job) for filter2D working.

---

Just starting you Open Source Journey ? Don't forget to check out [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

Want to `++` your GitHub Profile README ? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time !

Namaste 🙏