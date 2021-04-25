## How To Make A SlideShow Using OpenCV

We have been making slideshows for most of our college/office presentations to look great while presenting using Microsoft PowerPoint, let's take this as an image processing activity and see how we can achieve slide show utility using Python's OpenCV library in this article.

It could be a pass time activity or something new to learn or just to show off your friends or juniors, so without any further ado, let's get started!

> *Note: If you do not have OpenCV installed, I suggest you visit [here](https://blog.codekaro.info/lets-draw-opencv-logo-using-opencv) and check **Prerequisites** steps on the process of installation.*

---

### Necessary Imports

First, create a python file, name it whatever you like, for this article let's say `slideshow.py`. Now add the following imports to the file created:

```python
# ./slideshow.py

import cv2
import numpy as np
from math import ceil
import os
```

- We import `cv2` for all image processing tasks, `numpy` with alias `np` to create an initial window for display (all things in OpenCV works with numpy under the hood), `ceil` from `math` to satisfy a future condition (how do I know if need it or not?, well you don't, during the process of making an app there would be times when you will have to continuously improve your program and it's fine, but for this article, I want to keep everything at one place from starting, so don't worry just know that we will need this import) and lastly we import `os` to extract all image files that we need in a slideshow.

> *Note: You also need a set of images you would want to view as a slideshow. Collect them and keep them in the `./images` folder and don't worry about the size of images.*

### Variables, Image Window and Alpha-Beta

Add the following code to the same file:

```python

dst = "./images/"       # Images destination
images = os.listdir(dst)    # Get their names in a list
length = len(images)

result = np.zeros((360,360,3), np.uint8)        # Image window of size (360, 360)
i = 1

a = 1.0     # alpha
b = 0.0     # beta
img = cv2.imread(dst + images[i])
img = cv2.resize(img, (360, 360))
```

- First 3 lines find out the image name of all the images present in the `./images` folder. We use the `os.listdir` method to list all the contents of a directory and then keep them in the `images` variable and also we keep the length as a measure for total available images.
- Next, we create an image window of size `(360, 360, 3)`, which is a 3 channel image. Initially, it will all be black (filled with zeros).
- Then we define some more constants, `i` to be used to loop over images, `a` to keep initial alpha value and `b` for initial beta value, we will see how these are used for image transition that ultimately will give the slideshow effect.
- At last, we take the first image from the list of images, resize it to fit the window, this will be the first image to appear on the slideshow.

### SlideShow Loop

Let's create our slideshow, add the following code to the same file:

```python

# Slide Show Loop
while(True):

    if(ceil(a)==0):
        a = 1.0
        b = 0.0
        i = (i+1)%length    # Getting new image from directory
        img = cv2.imread(dst + images[i])
        img = cv2.resize(img, (360, 360))

    a -= 0.01
    b += 0.01

    # Image Transition from one to another
    result = cv2.addWeighted(result, a, img, b, 0)
    cv2.imshow("Slide Show", result)
    key = cv2.waitKey(1) & 0xff
    if key==ord('q'):
        break

cv2.destroyAllWindows()
```

- Now, we create a while infinite loop. Inside it, there is a conditional that checks for `ceil(a)` if it reaches `0` (zero) then we reset the `a` and `b` values, update `i` in a circular fashion using modulus operator `%` on the length of the list of images to get the index of next image, and update `img` variable to contain a new image and resize it.
- Outside of the conditional, we use `a` and `b` to decrease and increase alpha and beta values respectively. This variation will give us the transition effect that seems to be smooth. We will use these with the `cv2.addWeighted` method that just overlaps one image over another depending on the weight of the given images.
- `result` stores the new updated image that we will display using the `cv2.imshow` method of the OpenCV. At last, we wait for a key event and breaks out of the while loop if it happens and destroy all windows created during execution using the `cv2.destroyAllWindow` method.

`cv2.addWeighted` method is what helps us to achieve the slideshow effect that we wanted. Here, the alpha `a` value is the weight for the resulting image (that was initially a black window) and the beta `b` value is for a new image that will overlap the `result` window. Make sure that sum of `a` and `b` remains equal to` 1` (one). For more information on this, please visit [here](https://docs.opencv.org/3.4/d5/dc4/tutorial_adding_images.html).

### Demo - How It Looks

The images I took are logos of my favourite programming languages - Python, Scala and ReactJS (currently learning).

![demo.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1619347152591/cjuu6ZS_W.gif)

> *For complete script, visit [here](https://github.com/siddharth2016/Opencv-Python-Computer-Vision/blob/master/imageSlideShow.py).*

### What Next?

Well, that's it from me. If you followed this, you might be seeing a wonderful slideshow of your collection of images. As for the next steps, you can enhance this application by adding the following:

- Add buttons to change the type of slideshow. Currently, it is only doing a smooth transition, try to implement a different animated transition.
- Add a utility to select a number of images and not all, as we did, we just took every image. Also, you can try to handle exception like what if a non-image comes from the folder.

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Want to showcase your Python project or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏