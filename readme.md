# Gemstone identification AI

This project is an Imagenet/ Resnet18 based AI model that is designed to evaluate and classify raw gemstone or rock samples. It is meant to ease the difficulty that can be encountered when trying to identify a rock/gemstone sample yourself. The AI was trained on 33 classes of commonly found rock/gemstone specimens, with a dataset that was made and curated by hand (see labels.txt to view what each class is specifically, and see the train and val folders under the dataset to see examples of each of the classes). This model only can classify images through a terminal command, and cannot use a normal python program to view images or connect to a webcam due to an error loading Imagenet.

## The Algorithm

This is a Resnet18 based model, which means that I took the pre-trained model- Resnet18 -and I gave it a new dataset for it to train off of. Effectively re-training the model to understand the new data but also taking advantage of its prior training and conditioning to allow it to learn very quickly. The dataset itself is just a large collection of images that are seperated into their respective catagories, with most of the images being in the 'train' folder and a small amount of each class in the 'val' folder. The AI spends most of its time learning in the 'train' folder, hence it having the majority of images, and the 'val' images are for the AI to test itself when training. This model was trained for 35 epochs, meaning it went through the data in its entirety 35 times, which is a fairly signifcant amount in terms of time and processing power.

## Running this project
This project was designed off of the Nvidia Jetson Nano with Jetson-inference and many other files pre-loaded on to it, and the steps listed here are specifically for a Jetson Nano with these files installed. This project also uses VScode to connect and interact with the Nano, so make sure to download and install that.

To run the already trained GemstonesAI follow these steps:
1. Download the GemstonesAI files off of the Google Drive page
2. Unzip the files
3. Rename the unzipped folder to GemstonesAI
4. Open VScode and connect to your Nano
5. Navigate to Jetson-inference/python/training/classification
6. Copy the GemstonesAI files into BOTH the models folder and the data folder
7. Take a picture of the rock sample you wish to classify (or download an image off the internet just to test the AI)
8. Upload the picture into the classification folder
9. Run this command in the terminal: imagenet.py --model=models/GemstonesAI/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/GemstonesAI/labels.txt {YOURIMAGE} {CLASSIFIEDIMAGENAME}
        *Replace {YOURIMAGE} with the file name for the image you want to classify, make sure to include the file type, here's an example: Rose_quartz.png (Also remove the {} brackets when putting in your file name). Replace {CLASSIFIEDIMAGENAME} with the name you want your new classified image to be called, make sure the file type is the same too, for example: Rose_quartz_classified.png
10. Run the command
11. After a moment you should see your new classified file appear in the classifications folder

If you want to train the model yourself, follow these steps:
1. Download the GemstoneAI dataset off the Google Drive file (second link)
2. Open VScode and connect to your Nano
3. Navigate to Jetson-inference/python/training/classification
4. Open the docker container in the terminal
5. Type this into the terminal: python3 train.py --model-dir=models/Gemstones data/Gemstones
6. After a moment you should see the AI start to run through the epochs and data
7. wait for training to finish (I recommend running a fan over the heatsink of the Nano to keep it cool and boost efficiency)
8. Type python3 onnx_export.py --model-dir=models/Gemstones into the console to save and export the model
9. Follow the 9 steps above this except with your own files to use your model

Link to youtube tutorial on how to classify an image using this AI:
[https://youtu.be/aPZ2T3H3OOw]
