# Gemstone identification AI

This project is an Imagenet/ Resnet18 based AI model that is designed to evaluate and classify raw gemstone or rock samples. It is meant to ease the difficulty that can be encountered when trying to identify a rock/gemstone sample yourself. The AI was trained on 33 classes of commonly found rock/gemstone specimens, with a dataset that was made and curated by hand (see labels.txt to view what each class is specifically, and see the train and val folders under the dataset to see examples of each of the classes).

## The Algorithm

This is a Resnet18 based model, which means that I took the pre-trained model- Resnet18 -and I gave it a new dataset for it to train off of. Effectively re-training the model to understand the new data but also taking advantage of its prior training and conditioning to allow it to learn very quickly. The dataset itself is just a large collection of images that are seperated into their respective catagories, with most of the images being in the 'train' folder and a small amount of each class in the 'val' folder. The AI spends most of its time learning in the 'train' folder, hence it having the majority of images, and the 'val' images are for the AI to test itself when training. This model was trained for 35 epochs, meaning it went through the data in its entirety 35 times, which is a fairly signifcant amount in terms of time and processing power.

## Running this project
imagenet.py --model=models/Gemstones/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/Gemstones/labels.txt 0007.jpg output2.jpg
This project was designed off of the Nvidia Jetson Nano with Jetson-inference and many other files pre-loaded on to it, and the steps listed here are specifically for a Jetson Nano with these files installed. This project also uses VScode to connect and interact with the Nano, so make sure to download and install that.

To run the already trained GemstonesAI follow these steps:
1. Download the GemstonesAI files off of the Google Drive page
2. Open VScode and connect to your Nano
3. Navigate to Jetson-inference/python/training/classification
4. Copy the GemstonesAI files into BOTH the models folder and the data folder
5. Take a picture of the rock sample you wish to classify (or download an image off the internet just to test the AI)
6. Upload the picture into the classification folder
7. Run this command in the terminal: imagenet.py --model=models/Gemstones/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/Gemstones/labels.txt <YOURIMAGE> <CLASSIFIEDIMAGENAME>
        *Replace <YOURIMAGE> with the file name for the image you want to classify, make sure to include the file type, here's an example: Rose_quartz.png (Also remove the <> brackets when putting in your file name). Replace <CLASSIFIEDIMAGE> with the name you want your new classified image to be called, make sure the file type is the same too, for example: CLASSIFIEDEXAMPLE.png
8. Run the command
9. After a moment you should see your new classified file appear in the classifications folder

If you want to train the model yourself, follow these steps:
1. 


[View a video explanation here](video link)
