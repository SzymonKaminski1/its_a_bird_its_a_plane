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

  Birds datasets consist of 525 subfolders with photos of particular species. My goal was to recognize birds images in general, so I decided to combine these images. Secondly, birds dataset is much bigger than my planes datasets. For merging species subfolders and choosing adequate number of photos from birds dataset to obtain a balanced amount of images for binary classification I used prepare_bird_dataset.ipynb script.

- #### Data preparation
  The main point of data preparation in this project is data augmentation. My motivation to use this method was birds images. They are cropped in a way that a bird is more or less in the middle and takes the majority of the center part of the photo. Data augmentation helps to make images more diverse. I was also worried that 
same schedule among bird photos would lead to worse performance on test data. It turned out during experiment process that without data augmentation the performance was indeed worse. My hypothesis is that our CNN would "make a conclusion" that the "bird" is a big, colorful area in the middle of a photo. In addition, photos show only one bird, not a pair or a group. 

- #### Architecture and learning process.
  Current architecture and values of features of CNN model in this project is a result of a long experimental process. At the beginning of work, I noticed that a key is a size, a number of parameters of the network. Small CNNs performed worse, some of them seemed not to learn anything.
When I started trying bigger networks, I realized that my personal equipment doesn't provide me with enough computational power. After some research I decided to use the Google Colab with TPU environment. It enabled me to find suitable CNN in a reasonable time.
  - I tried changing number of convolutional layers and way of stacking them. Stacked layers where demanding when it comes to computations, but they didn't give satisfying results.
   - It also turned out that MaxPooling gave better accuracy than AveragePooling.
  - Next aspect of convolutional layers was a size of a kernel. The smaller kernel compared to image resolution the better result was obtained.
  - When it comes to depth of the layers it turned out that 64 was a good trade-off. The 128 lead to bad performance, in my opinion it starded to detect random aspects of an image.
  - I tried to use some types of regularization but the learning process became very long and I wasn't able to properly test this method because of my limited computational power.
  - I also tried to figure out best resolution of a photo. At first I was trying 224x224 and I obtained good results but by cost of a long learning process. After that I had an idea that maybe the problem is much simpler because a bird is far different from a plane and I tried i.e. 32x32 and 64x64 but unfortunately it got worse.
  - I experimented with number of dense layers. The result surprised me because best performance was obtained by only one dense layer after Flatten layer. My intuition was that at least two of them are necessary.
  - After trying different batch sizes I made a conclusion that best is 128.
  - Same goes to using (or not) droputs, their number, "place" where there are used and dropout rate. It turned out that best are after flatten and dense layer with 0.1 rate each.
  - Last but not least, one of key factors - number of epochs. 10 epochs gave best results. I also want to note that I didn't try very big numbers of epochs because of time required to train my network.
 
  To conclude, experiments did not exhaust the topic for sure. Google Colab enables user to make computation for up to 12 hours. My models required about 8-9 hours of training. It prevented me from trying more complex and/or more possibilities of network features combinations.

- #### Evaluation
  - Plots for training/validation loss and accuracy.
  - On a test set my network got 94% accuracy for birds class and 96% for planes class - 95% on average.
  - Currently, I am preparning separate program for checking test cases. I am very curious how my CNN "thinks".

- #### Thoughts on the result
  95% accuracy is pretty good, but in my opinion it shows that my dataset makes this task easier for my algorithm. Especially bird dataset is constructed in a way that (in my opinion) helps CNN to perform on test set. Photos in training and test set are very similar to each other. Very similar background, bird are big, in the center of the photo - photos made in a "manufactural" way. My intuition is that CNN can become "lazy" - not trying to recognize birds' features like their shape, colors, their wings, beaks, claws etc. That's a room for improvement!
