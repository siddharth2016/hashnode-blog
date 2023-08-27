---
title: "Let's Draw OpenCV Logo Using OpenCV"
seoDescription: "OpenCV is a powerful computer vision and deep learning library. In this article, we are going to look at the image drawing capabilities of OpenCV."
datePublished: Sat Apr 17 2021 10:19:29 GMT+0000 (Coordinated Universal Time)
cuid: cknll99y603c5kos19sgdbws0
slug: lets-draw-opencv-logo-using-opencv
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1618653737809/eKmzvd2xj.png
tags: image-processing, tutorial, python, opensource, computer-vision

---

OpenCV is an awesome, powerful image-processing, computer vision and deep learning library. It would not be a joke to say that it is the god of all computer vision libraries.

In this article, we are going to look at the image drawing capabilities of OpenCV and how we can draw its very own logo with that.

---

### Prerequisites - All You Need

To be able to successfully work with this tutorial all we need is Python and OpenCV installed.

Here, we are going to use `pip` to install OpenCV, which directly installs the wheel file without us worrying about the manual build process. We can surely do a manual build, but that itself would need a separate write-up (check [this](https://www.pyimagesearch.com/opencv-tutorials-resources-guides/) already available awesome guide).

We are going to work in a virtual environment for this activity (considering we have python already installed, if not please check [this](https://realpython.com/installing-python/)). To create this environment follow the below steps in the terminal:

```shell
~ % mkdir opencv_logo_proj
~ % cd opencv_logo_proj
opencv_logo_proj ~ % python3 -m venv venv
```

This creates a virtual environment in our working directory `opencv_logo_proj` if we notice there is a folder created named `venv` in the directory.

To activate this `venv`, we can do the following:

```shell
opencv_logo_proj ~ % source venv/bin/activate
(venv) opencv_logo_proj ~ %
```

`(venv)` prefix in terminal means that this environment is active for us to do the work. Now nothing outside of it will be affected and libraries will only be installed in this environment.

So moving on, first we upgrade the pip, setuptools and wheel packages in python's virtual environment (to avoid any unwanted errors).

```shell
(venv) ~ % pip install --upgrade pip setuptools wheel
```

When you run the above command, it upgrades pip, setuptools and wheel in one go. Let's install OpenCV now.

```shell
(venv) ~ % pip install opencv-contrib-python
```

We are going to install OpenCV with all its main modules and contrib modules (this contains ongoing work, but mostly a stable version).

After you hit enter on that, you should see something like this:

```shell
Collecting opencv-contrib-python
  Downloading opencv_contrib_python-4.5.1.48-cp38-cp38-macosx_10_13_x86_64.whl (51.3 MB)
     |████████████████████████████████| 51.3 MB 7.5 MB/s 
Collecting numpy>=1.17.3
  Downloading numpy-1.20.2-cp38-cp38-macosx_10_9_x86_64.whl (16.0 MB)
     |████████████████████████████████| 16.0 MB 3.9 MB/s 
Installing collected packages: numpy, opencv-contrib-python
```

OpenCV is dependent on NumPy, hence it installs that as well. If you faced any issue during the OpenCV installation, please reach out to me in the comments.

Let's move on to the fun part.

---

### OpenCV Logo Using OpenCV

Our objective is to draw this:

![opencvlogoorig.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1618654038257/tM_8qo9Gt.jpeg)

Let's create a file, name it `openCvSymbolDrawing.py` (or whatever you like). Add the following lines of code in it:

```python
# ./opencv_logo_proj/openCvSynmbolDrawing.py

import cv2
import numpy as np

#output image
img = np.full((360, 512, 3), 255, dtype="uint8")
```

- First, we import required libraries, `import cv2` imports OpenCV computer vision library and `import numpy as np` imports numpy with an alias `np`.
- Then we create the output image where we will draw the OpenCV logo. OpenCV works with NumPy under the hood and treats images as NumPy arrays.

The important thing to note here is that the dimensions `(360, 512, 3)` are measured from the top-left corner of the image. So, it took `360` points downwards (y-axis) from that corner and took `512` points towards the right (x-axis) from that corner and `3` represents it is a 3-dimensional array (also represents its a 3 channel image, namely - Blue, Green, Red), which by the way all `BGR` images are in OpenCV (`GRAY` images are 2-dimensional). 

![xyaxis.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618654060529/soDMBbC66.png)

Now, there are several drawing utilities present in `cv2` that can help us to achieve the desired results. Here, we are going to look at the `ellipse` form to draw the logo. Add the following code in the file:

```python
# ./opencv_logo_proj/openCvSynmbolDrawing.py

img = cv2.ellipse(img, (256, 80), (60,60), 120,0,300,(0,0,255),-1)
img = cv2.ellipse(img, (256, 80), (20,20), 120,0,300,(255,255,255),-1)
img = cv2.ellipse(img, (176, 200), (60,60), 0,0,300,(0,255,0),-1)
img = cv2.ellipse(img, (176, 200), (20,20), 0,0,300,(255,255,255),-1)
img = cv2.ellipse(img, (336, 200), (60,60), 300,0,300,(255,0,0),-1)
img = cv2.ellipse(img, (336, 200), (20,20), 300,0,300,(255,255,255),-1)

font = cv2.FONT_HERSHEY_SIMPLEX
img = cv2.putText(img, "OpenCV", (196,296), font, 1, (0,0,0), 4, cv2.LINE_AA)
```

- We use `cv2.ellipse` to draw an ellipse on the image `img`. It takes image name on which it needs to draw `img`, centre coordinates that represent the centre of the ellipse `(256, 80)`, axes length that represents major and minor axes of ellipse `(60, 60)`, rotation angle at which ellipse needs to be rotated `120` degrees, start angle `0` degrees, end angle `300` degrees, colour ellipse uses `(0, 0, 255)` for red ellipse and the last parameter is thickness when set to `-1` that fills the drawing with the given colour. This would make an ellipse like below:

![img1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618654081997/eIvDEt6VP.png)

- `img = cv2.ellipse(img, (256, 80), (20,20), 120,0,300,(255,255,255),-1)` this statement creates a concentric ellipse to fill white color to get a desired shape.

![img2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618654095759/t65ELz9TH.png)

- Similarly, the next couple of statements creates green and blue ellipse with desired shapes.

```python
img = cv2.ellipse(img, (176, 200), (60,60), 0,0,300,(0,255,0),-1)
img = cv2.ellipse(img, (176, 200), (20,20), 0,0,300,(255,255,255),-1)
```

We get a green ellipse of the logo.

![img3.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618654129100/oAnxcrzE4.png)

```python
img = cv2.ellipse(img, (336, 200), (60,60), 300,0,300,(255,0,0),-1)
img = cv2.ellipse(img, (336, 200), (20,20), 300,0,300,(255,255,255),-1)
```

At last, we draw a blue ellipse of the logo.

![img4.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618654142324/ChVxxNc1A.png)

- Next, we can add some more information if we want, like text. Here, we set a font with `font = cv2.FONT_HERSHEY_SIMPLEX` takes hershey simplex font, which we can use to style the text.
- `img = cv2.putText(img, "OpenCV", (196,296), font, 1, (0,0,0), 4, cv2.LINE_AA)` this puts text on the image and takes following parameters, image where it needs to put text on `img`, text `OpenCV`, position of the text bottom-left coordinates `(196,296)`, font style `font` which we defined earlier, font scale `1`, color of text `(0,0,0)`, thickness of `4` and lastly type of line `cv2.LINE_AA` (it is optional, we can also skip this).

Now, we display our final result and save the output, add the following code to the file:

```python
# ./opencv_logo_proj/openCvSynmbolDrawing.py

cv2.imshow("OpenCV Logo", img)
cv2.waitKey(0)
cv2.destroyAllWindows()
cv2.imwrite('opencvlogo.png', img)
```

- We use the `cv2.imshow` method to output the image for display but simply saying `imshow` means that it will show that image for a couple of milliseconds and complete the program and exits the terminal. We don't want that, we need to be able to see the image for as long as we want, right?
- Here comes the use of `cv2.waitKey` that takes a parameter, say, `0` to let the system know to wait for a certain keypress until it exits the process. By giving `0` as the value, it means any keypress would continue the program and exit the process. To clear the display output we need to use `cv2.destroyAllWindows()` explicitly after using `cv2.waitKey(0)` to let system know to clear the output.
- Lastly, we save the result using `cv2.imwrite('opencvlogo.png', img)` that takes the image file name and image to be saved.

The final output would look something like this:

![opencvlogo.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618654175386/6KpX54oVc.png)

---

### Conclusion, Already?

Yeah, that's about it. We were able to draw a symbol almost (I would say 99%) similar to the actual logo. I hope you enjoyed the process of using a powerful yet simple to use library like OpenCV.

It was a fun activity I did, back during my college days. Hoping this would inspire you to pursue and look further at the capabilities of computer vision and image processing.

If you need more fun activities like this on computer vision, don't forget to check out [OpenCV-Python-Computer-Vision](https://github.com/siddharth2016/Opencv-Python-Computer-Vision).

---

- Just starting your Open Source Journey? Don't forget to check [Hello Open Source](https://github.com/siddharth2016/hello-open-source)

- Need inspiration or a different perspective on the Python projects or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch? Check out [PongPong](https://github.com/siddharth2016/PongPong)

- Want to `++` your GitHub Profile README? Check out [Quote - README](https://github.com/marketplace/actions/quote-readme)

Till next time!

Namaste 🙏