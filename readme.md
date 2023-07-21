# Gemstone identification AI

This project is an Imagenet/ Resnet18 based AI model that is designed to evaluate and classify raw gemstone or rock samples. It is meant to ease the difficulty that can be encountered when trying to identify a rock/gemstone sample yourself. The AI was trained on 33 classes of commonly found rock/gemstone specimens, with a dataset that was made and curated by hand (see labels.txt to view what each class is specifically, and see the train and val folders under the dataset to see examples of each of the classes).

## The Algorithm

Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

## Running this project
imagenet.py --model=models/Gemstones/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=data/Gemstones/labels.txt 0007.jpg output2.jpg
1. Add steps for running this project.
2. Make sure to include any required libraries that need to be installed for your project to run.

[View a video explanation here](video link)
