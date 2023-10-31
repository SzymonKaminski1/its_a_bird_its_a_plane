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

- #### Architecture and learning process.
  Current architecture and values of features of CNN model in this project is a result of a long experimental process. At the begining of work I noticed that a key is a size, a number of parameters of the network. Small CNNs performed bad, some of them seemed not to learn anything.
When I started trying bigger networks I realized that my personal equipmemt doesn't provide me with enough od computational power. After some research I decided to use Google Colab with TP4 environment. It enabled me to find suitable CNN in a resonable time.

 I tried changing number of convolutional leyers and way of stacking them. Stacked leyers where demanding when it comes to computations but they didn't give satisfying results.
 It also turned out that MaxPooling gave better accuracy than AveragePooling.
 Next aspect of convolutional leyers was a size of a kernel. The smaller kernel compared to image resolution whe better result was obtained.
 When it comes to depth of the leyers it tourned out that 64 was a good trade-off. The 128 lead to bad performance, in my opinion it starded to detect random aspects of a image.
 I also tried to figure out best resolution of a photo. At first I was trying 224x224 and I obtained good results but by cost of long learning process. After that I had an idea that maybe the problem is much more simple because a bird is far different from a plane and I tried i.e. 32x32 and 64x64 but unfortunately it got worse.

 I also experimented with number of dense leyers. The result surprised me because best performance was obtained by only one dense layer after Flatten leyer. My intuision was that at least two of them are necessery.

 



