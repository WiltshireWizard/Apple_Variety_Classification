# Apple_Variety_Classification
Image classifiaction of 5 common British apple varieties using Deep Learning.

## Project Overview:
I built an apple variety classifier to identify apples typically found in British gardens. I worked a summer job where we produced personalised apple juice from the customers own apples. A common question from the customer would be what type of apple they had brought in and what the juice from them would taste like. This model could provide a framework to an app that addresses these questions. A picture of the delivered apples could be taken. The app would  identify the variety of apple, provide some general information about the variety as well as some tasting notes. Information such as apple variety and some tasting notes could also be included on the bottle labels.

A key part of the business model was customer satisfaction as it relied on repeat customers returning year after year. Word of mouth was the biggest source of advitising for the business. The app discussed would allow workers to address some of the most common questions from customers and allow more informative and accurate labels to be made. The app would also be a good approach to this problem as the business has a very high turnover in staff so educating all staff memebers on apple varieties would be difficult.

I was able to get the model to predict the apple variety with 75% accuracy after minimal tuning. This is significantly outperforms most peoples ability to identify apple varieties. The results are promising given the very small data set used. To get these results I used transfer learning on a CNN trained on resnet34. This created time efficiencies and solid results. An expansion in number of apple varieties classified would be needed to create a model suitable for the app discussed. However this project indicates that with a much larger dataset and some more model tuning then a genuinely useful model could be achieved.

![alt text](https://github.com/WiltshireWizard/Apple_Variety_Classification/blob/master/Confusion_Matrix.png)


## Data 
* I used the following chrome extension to download the data from google images. FatKun Batch Download Image
* Total dataset included 804 images in total: 184 Braeburn, 100 Bramley, 192 Cox, 150 Gala, 178 Russet.
* Images were downloaded into folders corresponding to the apple variety.
* A function was created to load the data and assign labels to each image.
* Image data was normalized by dividing by 255.

## Model Building and Performance
* Train Test split used a test split of 33%.
* **First approach used Keras to build my own model using a convulutional neural network:**
    * Model comprised of 5 layers. The first 3 layers were convulutional and last 2 were dense.
    * The Number of nodes in each sequential layer were: 16,32,64,128,5
    * After training for 25 epochs the validation accuracy was 65% but there was clear evidence of overtraining.
    * An early stop was added to the model to prevent overtraining.
    * Overfitting was still an issue.
    * Data Augmenation and dropout layers were included to deal with overfitting and helped address this issue.
    * The resulting validation accuracy from these chnages was not as high at 61%
* **A second approach seeked to improve model performance using fastai to use the bottleneck features of a pre-trained network:**
    * This model was refined by optimizing the learning rate values used.
    * This model resulted in a 75% accuracy.
   
   
   ![alt text](https://github.com/WiltshireWizard/Apple_Variety_Classification/blob/master/Confusion_Matrix.png)
