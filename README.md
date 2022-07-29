[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8127859&assignment_repo_type=AssignmentRepo)
<!--
Name of your teams' final project
-->
# final-project
## [National Action Council for Minorities in Engineering(NACME)](https://www.nacme.org) Google Applied Machine Learning Intensive (AMLI) at the University of Kentucky

<!--
List all of the members who developed the project and
link to each members respective GitHub profile
-->
>Developed by: 
>- [LaQuawne DePriest](https://github.com/LDePriest) - `Virginia State University`
>- [Ronaldo Lopez-Tucux](https://github.com/RonaldoLopezTucux) - `Universtiy of California - Berkeley` 
>- [Priss Harbuck](https://github.com/harbuckp) - `Berea College` 


# Description
<!--
Give a short description on what your project accomplishes and what tools is uses. In addition, you can drop screenshots directly into your README file to add them to your README. Take these from your presentations.
-->
 The VIPER Library takes an image that is given and protects the user's privacy by blurring, blocking out, or adding noise to the image. When given a image it will blur, block, or add noise to the image depending on the user's preference. Then after the user has made a choice the user can make a percentage of the level of blur, or noise if they choose those. It will then return the new edited image to the user. It also blocks out any faces with emojis of the emotion the person is displaying.

There are two classes: the Model Class and the Image Class. The Image takes the parameters of detections and the image you want to use. The model class is only used for initizializing an instance of the Image Class currently in the code. The Image Class is the only part that continously works with the images. It is the way that privatize your images in your way. Some of the thing in the class only work with other things in the class. The Model class was only made to make the model to tell the detections of the objects that we want privatized in the images. 


# Usage instructions
<!--
Give details on how to install fork and install your project. You can get all of the python dependencies for your project by typing `pip3 freeze requirements.txt` on the system that runs your project. Add the generated `requirements.txt` to this repo.
-->

## Necessary Libraries
* !pip install -q fer
* !pip install -q cvzone
* import cv2 as cv( used for handling the image aspect)
* import tarfile(used to untar the model downloaded)
* import shutil
* import urllib.request(used to download)
* import os(file handling)
* import tensorflow as tf(used for detections model)
* import numpy as np(V1.2, added to fix adv noise saving.)
* import urllib
* import logging
* from imgaug import augmenters
* import matplotlib.pyplot as plt
* from fer import FER

## How to Open
1. Open the colab in the Github called 'Final.ipynb'
1. Run all of the code blocks in the colab until you get to the code block that creates a instance of the Image object named desk
1. Once you get to the code line that makes 'desk' put in a image with the name 'image.jpg'(Or you can import as many images as you want and just change the title of the image being used as a parameter for desk)
1. After the image/images have been added you can modify them as you'd like by using blur(),block(),noise(),or emoji().

**Image Class Methods**

* .get_image(image_path) - gets the image with the image path, which is a string
* .object_blur(cv2_image,x1,x2,y1,y2,blurAmount) - takes the image, and the coordinates of the detection boxes of the images
* .image_saver() - saves the modified image to 'image.jpg'
* .box_to_pixels(box_bounds, cv2_image) - takes the image, and the detections of the objects and borders our what we want to pixelize
* .blur(blur_amount) - takes the parameter of a float from .01 to 1.0, .01 = 1% and 1.0 = 100%,blurs image
* .object_block(image,x1,x2,y1,y2,color) - blocks out one of the items
* .block() - puts a black box over private images
* .noise(noise_amount) - takes a parameter that affects the amount of noise,.01 to 1.0, .01 = 1% and 1.0 = 100%
* .import_emoji() - downloads all of the emojis
* .coordinates(box) - coordinates of the bounding box
* .face2emoji(cropped_image, emotion) - puts the emoji on the face of the picture
* .emoji() - puts the emoji on the faces
* .priv_or_not(box_class) - checks to see if any of the items in the image are something we want private
* .priv_and_not(list[]) -seperates what is private and what isn't in the photo
* .modified(image) - saves the image that's been modified
* \__init__(model, image_path) - self.image= self.get_image(image_path),self.tensor,self.model,self.detections,self.blur_amount, self.noise_amount, self.priv_class, self.color, self.num_of_detections, self.modified, self.result, self.emoji_keys, self.emoji_dict

**Model Class Methods**

* \__init__ - imports and sets Facial Recognition Model, self.emotion_detector,self.emotion_model(),self.download_model(), self.model
* Download(base_url, file_name) -  checks if the file exists in the directory
* download_model() - downloads the model, and label.txt for the models
* initialize_model() - preprocesses te information to help with the frozen graph
