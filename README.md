# The flower project

The aim of this project is to first create high resolution images. The dataset of flowers was taken from [here](http://www.robots.ox.ac.uk/~vgg/data/flowers/) by taking both the 17 category flowers and 102 category flowers and mixing them together in random order.

This project is based on tensorflow's github repository on gans which can be found [here](https://github.com/tensorflow/models/tree/master/research/gan/progressive_gan).

The specific gan used is [progressive gan](https://arxiv.org/pdf/1710.10196.pdf) which is said to be good with high resolution images. This is done by progressively increasing resolution of images while training.
 As I am still in the progress of training, the results are not good yet.

To train the model further, just type

    python train_main.py

The original code is modified so this will do the trick. This will resume training from where it left off.

The models and event files will be saved to model. If you want to see the progress you can type

    tensorboard --logdir=events:./model

However, since the event files were close to 270 GB they were removed.
There are quite a few parameters(such as batch_size for each resolution) but they can be read in the train_main.py and can be changed accordingly.

# Slight modifications

- Increased training time as the final images had poor quality
- Increased resolutions so it can work up to 512*512
- Increased batch size for lower resolutions

# Problems

- At higher resolutions, possibly due to the small batch size due to lack of memory, the results are quite bad. For this, I am thinking of using accumulated gradients but I am not yet confident on how it works. Also, since the tensorflow team did not leave that much documentation, I think it will take quite a bit of time so I'm waiting on training for now.

Not sure how to test the code yet but I'm quite sure train_test.py has something to do with it.

# The models and data

I did not manage to upload the models and the dataset so I will host them in my google drive [here](https://drive.google.com/open?id=19NIWW0tgPkYf1sMVwwOPl4GjntU_6_uo). Unzip the file and put both flowers and model in the root directory for it to work.
