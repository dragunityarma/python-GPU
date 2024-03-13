# python-GPU
Help with running python function with GPU in pycharm or jupyter 
This is my code and i want to run this create_random_bg() function with GPU:

from PIL import Image
from pathlib import Path  # to create the folder to store the images
import numpy as np
import matplotlib.pyplot as plt
import time
import random
from random import randint

#creates backround images with random pixel values
#if i run it again the previous images remain because in their names i add current time


def create_random_bg(N):
    Path("bg_images").mkdir(parents=True, exist_ok=True)  # creates the folder
    folder = "bg_images/"  # keep folder name here and use it to save the image
    for i in range(N):
        pixel_data = np.random.randint(
            low=0,
            high=256,
            size=(1024, 1024, 3),
            dtype=np.uint8
        )

        img = Image.fromarray(pixel_data, "RGB")  # turn the array into an image
        img_name = str("bg_") + str(i) + str(time.time()) + str(".png")  # give a unique name using current time
        img = img.save(folder + img_name)

create_random_bg(100)


