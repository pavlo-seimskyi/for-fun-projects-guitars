# Guitars
This is a just-for-fun-project. Is your guitar Stratocaster or Telecaster? Find out here.

## Step 1: Scrape the Bing Image Search engine to get data
This is done in the notebook `data_and_training`. The data looks like this:

![image](/images/test1.jpg)

## Step 2: Prepare the data
150 images were  downloadeded. To prepare images for feeding into the model, we need to resize them first. After trying several approaches, `RandomResizedCrop` turned out to work best. After resizing the images to 128x128 px format, I also used data augmentation that performs random changes in contrast of the pictures, flipping them horizontally and vertically, and expanding/squishing them. All that is fairly easy to perform with fastai. This is how one of the data samples looks after augmentation and just before feeding into the model:

![image](/images/augmentation.jpg)

## Step 3: Train a model
I went for the ResNet34 model that was pretrained on ImageNet. Accuracy of 92% was achieved just after 9 epochs and roughly 1 minute of training!

![image](/images/confusion.jpg)

The model was saved for future inference as `export.pkl` file.

## Step 4: Deployment
In the `deployment.ipynb` notebook, it is shown how to perform inference with the saved file. You can upload your own new images and classify them. Lastly, in the `web_app.ipynb` notebook, using **voila**, I created some basic design for the potential web app application. This code can be uploaded to services like [Binder](https://mybinder.org/) to put in production.
