# Cell Organelle Identifier Using Fluorescent Proteins

For the final project for Flatiron School's Data Immersive Course, I wanted to focus again on image classification. From my personal blog presentation on SSIM to identify picture pixel similarity and module 4's animal image classification, I found that analysing unstructure data to be very satisfying. In addition, I studied biology as an undergrad and have interned at a breast cancer research lab for a year before joining this bootcamp so I wanted to combine these two passions of mine into one. Unfortunately, getting pictures of cancer cells that are labeled is extremely difficult as it is propiretory data of each medical institute. So I focused on building a model that can perhaps identify cell organelle based on their structures. The cell organelles have each been tagged with specific fluorescent proteins. Specific protein only binds to specific organelle and once bound, they give off a color (most commonly green, but other colors such as DAPI staining for the nucleus exist).

## Data

I worked with two different data set. Nether data set is on github repo, but I will link them below:

### Dataset 1

The first dataset is labeled cell pictures of [Yeast](https://kodu.ut.ee/~leopoldp/2016_DeepYeast/) from Chong et all. Yeast was used instead of human cells as they have a 90% similarity in terms of cell organelle structures. They had 11 organelles labeled, but I decided to work on only 6. 

### Issues with Dataset 1

The dataset from source stated that pictures were of high resolution. So using what I know about VGG16 model transfer learning, I made a few models and trained the images on them. Since there were many pictures from each labels, this took a while. After ward, I decided to look at basic evaluation metrics and saw that my machine was not performing above baseline. Then I actually took a look at the pictures and saw that the resolution was actually terrible instead. I still went ahead and started to modify my model until I finally made one that can predict at double the base line. That can be found in my [Dataset 1 Final Notebook](https://github.com/imamun93/cell_organelle_classifer/blob/master/DataSet1FinalNotebook.ipynb). 

### Results

Here are the model accuracy, training and validation graph:

<img width="273" alt="screen shot 2019-02-11 at 5 53 49 pm" src="https://user-images.githubusercontent.com/41834786/52599221-063ff300-2e26-11e9-902b-e33eabaf2999.png">

<img width="433" alt="screen shot 2019-02-11 at 5 53 35 pm" src="https://user-images.githubusercontent.com/41834786/52599222-063ff300-2e26-11e9-9e86-d125fdc8391f.png">

Here are the classification metric and confusion matrix for dataset 1:

<img width="517" alt="screen shot 2019-02-11 at 5 38 33 pm" src="https://user-images.githubusercontent.com/41834786/52598560-1ce54a80-2e24-11e9-9b3f-94c558e62ac4.png">

<img width="372" alt="screen shot 2019-02-11 at 5 38 44 pm" src="https://user-images.githubusercontent.com/41834786/52598559-1ce54a80-2e24-11e9-823e-19666da7b527.png">

Without higher image resolution, I was not able to make accurate prediction.

### Dataset 2

The second dataset is from the Human Protein Atlas. They had a dataset on kaggle. The dataset can be found in [HPA-Kaggle](https://www.kaggle.com/c/human-protein-atlas-image-classification/data). They had higher resolution pictures, but they were unlabaled and linked with CSV. Using os.join.path, that was relatively easy to fix.

The final notebook for dataset 2 can be found in my [Dataset 2 Final Notebook](https://github.com/imamun93/cell_organelle_classifer/blob/master/DataSet2FinalNotebook.ipynb). After linking the labels, here are the categories:
![image](https://user-images.githubusercontent.com/41834786/52599026-77cb7180-2e25-11e9-88c0-3b43681cfea2.png)

Dropping samples with less than 200 labels, I ran this through the machine algorithm I made in dataset 1.
After tweaking the algorithm some more, I finally achieved a high accuracy result

### Results

<img width="1012" alt="screen shot 2019-02-11 at 5 51 43 pm" src="https://user-images.githubusercontent.com/41834786/52599122-b95c1c80-2e25-11e9-8eb3-be2c2ddf4e30.png">

And here are the training and validation graph:
![image](https://user-images.githubusercontent.com/41834786/52599160-ddb7f900-2e25-11e9-9022-a358a1f743dc.png)

Here is some example of it's prediction:
![image](https://user-images.githubusercontent.com/41834786/52599476-aa299e80-2e26-11e9-8c06-d60fd579744f.png)

As you can see on the last picture, it was able to identify some aggresome cells, which are the first stages of occurence for cancer. Although I will need a lot more pictures of different variations of aggresome cells to be able to predict accurately.


## Conclusion

Although I am confident in my algorithm to train and classify cell organelles, I was not able to achieve the high accuracy I wanted due to lower resolution pictures. My goal is to get high resolution pictures of cancer cells, and run it through this model. This can potentially help detect cancer cells on the same level as a trained professional. 
