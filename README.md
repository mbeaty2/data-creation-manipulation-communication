# Data Creation, Manipulation, and Communication

This repository develops a deeper understanding of dataset creation, manipulation, and communication.

## Description

This repository contains all files for the Artificial Intelligence for the Media course assignments completed in part of my Masters of Data Science and AI degree. These assignments are as follows:

Assignment 1: Creating My Own Dataset

For this assignment, I wanted to create a dataset I could use for my mini-project for this course. I was interested in using a Pix2Pix model on drawings or sketches of architectural buildings and the real image of that building once built. To do this, I first started with my output or real images by conducting 7 searches in Pinterest and using PinDown to download the images into a folder. This resulted in about 7,000 images, videos, and text files. I then cleaned this folder to only include images related to the search. When referring to this assignment, you need to look at the Outputs_png, Inputs_png, Image_pairs folders, as well as the Assignment 1 code notebook. After I had all the images cleaned, I used the terminal and ImageMagick to change and resave all images as .png files, whereas before they were a mixture of .png and .jpg files. I then ran them through a code to resize them all to 512 x 512 to keep them all uniform. 

I then used this code to rename the files in numerical order: first = ls -v | cat -n | while read n f; do mv -n "$f" "$n.ext"; done

And then used this to rename them with starting zeroes so they could be read properly: ls -t *.png | cat -n |                                           \
while read n f; do mv "$f" "$(printf %04d.png $n)"; done

Both of the above commands were done in the Terminal. The output images were saved in the "Output_png" folder. Once I had the output images resized and renamed, I ran the images through a Canny edge detection model to get my input images. The edge detection model was adapted from code available on StackOverflow here: https://stackoverflow.com/questions/58314400/edge-detection-for-multiple-images. I did the same renaming process as before so all input images were named with the same number as their counterpart output image. These input images were saved in the "Input_png" folder. As the Pix2Pix model takes in only one image, I then had to merge these images side by side. To do this, I adapted code found from StackOverflow available here: https://stackoverflow.com/questions/65342361/photos-side-by-side.

Finally, I renamed those images with beginning zeros and split my dataset into a training set (70% of the data), a test set (20% of the data), and a validation set (10% of the data). The paired images are saved in the folder "Image_pairs." 

Due to the large scale of the data, you can view these datasets here: https://artslondon-my.sharepoint.com/:f:/g/personal/m_beaty0520221_arts_ac_uk/Ejh8ZI5HJS1IuJpcAPEokPgBOGyB-T4ALOJmcc9uh_JQqA?e=cOBFct

Assignment 2 - Datasheet

Within this Assignment, you'll find a datasheet describing the data above in more detail. This datasheet follows the template provided to us by our Course leaders, answering all relevant questions, and removing those that do not fit the dataset. Those that do not fit are primarily regarding people. This datasheet also provides additional ideas in which this dataset could be used, as well as complications or limitations within the dataset. 

Assignment 3 - Manipulating Images with Pytorch

Assignment 3 follows a notebook provided by my course leaders. Given my computer's difficulty using Tensorflow, I have selected the Pytorch version of this notebook. Section One of this notebook is running through the code given with the notebook. In Section Two, I map the same code with a color image and translate the model to map RGB color values rather than just Black and White. This required a few changes in the code allowing the model to output 3 values in the output layer, and reshaping the image to have three dimension (height, width, RGB). 

Section Three adds two additional layers to the model. For this section, I reverted back to the Black and White image and model in Section One, and added two additional layers before the final activation function. 

Section Four first covers experimenting with other activation functions, specifically with Softsign and Tanhshrink. The second part of Section Four experiments with two different optimizers, Adam and Adadelta.

Section Five responds to the following question: In a paragraph or so, describe how the image we have created differs from the original image.  

## Getting Started

### Dependencies

* This project relied heavily on numpy and matplotlib.
* Librosa to parse and manipulate audiofiles.

### Executing program

Working through this program is relatively easy and can be simply done by downloading any dataset of your choosing and uploading it within the Jupyter notebook. Within that you can utilize the cells available to reveal truths in the data.

## Authors

Marissa Beaty, https://github.com/mbeaty2

## Version History
* 0.1
    * Initial Release

## Acknowledgments

Inspiration, code snippets, etc.
* [awesome-readme](https://github.com/matiassingers/awesome-readme)
