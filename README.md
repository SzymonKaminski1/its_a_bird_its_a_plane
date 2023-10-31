# It's a bird! It's a plane!
## This project is about creating and training my own convolutional neural network to classify whether it is a bird or a plane dataset.
### Process description:
- #### Dataset:
  In this project I used following datasets:

  Planes: \
  https://www.kaggle.com/datasets/nelyg8002000/commercial-aircraft-dataset \
  https://www.kaggle.com/datasets/eabdul/flying-vehicles

  Brids: \
  https://www.kaggle.com/datasets/gpiosenka/100-bird-species 

  Birds datasets consists of 525 subfolders with photos of particular species. My goal was to recognize birds images in general, so I decided to combine these images. Secondly, birds dataset is much bigger than my planes datasets. For merging species subfolders and choosing adequate number of photos from birds dataset to obtain balanced amount of images for binary classification I used prepare_bird_dataset.ipynb script.

- #### Data preparation
  Main point of data preperation in this project is data augmentation. My motivation to use this method were birds images. They are cropped in a way that a bird is more or less in the middle and takes majority of center part of the photo. Data augmentation helps to make images more diverse. I was also worried that 
same schedule among bird photos would lead to worse performance on test data. It turned out during experiments process that without data augmentation the performance was indeed worse. My hypotesis is that our CNN would "make a conclusion" that the "bird" is a big, colorful area in the middle of a photo.
