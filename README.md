# CNN Article Headline Classification
> project for MSDS631 - Introduction to Deep Learning course 2022
### Joleena Marshall & Edith Lee (Cohort 10)

## Introduction
Natural language processing is currently one of the most compelling areas of machine learning. Common applications in our daily lives include chatbots (on many consumer websites), search recommendations (on search engines), sentence completion (email, text, etc.), and many more. One widely available dataset is the body of news articles available to us on various news sites. 

For the purposes of this project, we selected a [Kaggle dataset](https://www.kaggle.com/datasets/hadasu92/cnn-articles-after-basic-cleaning) of 40k news articles to experiment with. The data includes the article's author, publish date, category, section, headline, description, and full article text. As such, we have a variety of possible directions to explore.

## Our problem
Since our data includes convenient labels for the category of article published, we decided to explore the use of various deep learning models on classifying article category. Using just the headline, we want to see if we're able to predict the category of the article.

## Data
For the purposes of understanding our resulting models, we conducted some basic EDA on the data at hand.

To begin, we investigated the distribution of categories across our dataset.

![categories](https://user-images.githubusercontent.com/25912759/176734674-134be288-f667-4171-a5aa-5317a71d288e.png)
> Horizontal bar chart of news article categories and their frequencies.

From this, we are able to conclude there is a major (unexpected) imbalance in article categories. By far, the two most common categories were news and sports. This should be kept in mind when we evaluate model accuracy, since we do not have a large enough train set for some of these categories to perform extremely well.

Next, we investigated the distribution of news sections.
![sections](https://user-images.githubusercontent.com/25912759/176734729-5c6e3416-5c89-4b40-ac76-869b61e07690.png)
> Horizontal bar chart of news article sections and their frequencies.

To display these findings nicely, we chose to hide any sections that occurred with a frequency less than 50 times. It should be noted, however, that there were a little of 300 articles that had less commonly observed sections. Since there are no clear pluralities in article section, we chose not to use Section in our classification problem.

Additionally, we conducted investigations into the headlines themselves. After tokenizing and lemmatizing the headlines, and removing any commonly occurring stopwords (including CNN), we looked into commonly occuring words by category. 

For the sake of brevity, we've included the distribution of commonly observed words to the two largest categories - 'news' and 'sports'. We've also limited the barplot to the top 25 most commonly appearing words.

![news](https://user-images.githubusercontent.com/25912759/176734750-f991bae9-7d50-4870-b457-3dcbde2adae2.png)
![sports](https://user-images.githubusercontent.com/25912759/176734769-2ae2505e-10fe-4924-ae85-a0eb3a454dd8.png)


## Findings:

### Baseline
For our baseline model, we tried using [LinearSVC](https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html), a package implemented in scikit-learn that utilizes Support Vector Machines for classification problems. This had a surprisingly high model performance at 91% accuracy. 
### CBOW
Next, we tried using the Continuous Bag of Words approach to classify headlines. This model performed the worst at 47% accuracy. However, this was to be expected given the nature of the CBOW model. Since the CBOW model uses the center of the string's vector representation to make predictions, we would not expect it to perform highly.
### BERT
We tried using a pre-trained BERT model, but the expected train time and computer power was too high, so we cut it off. However, the BERT model for prediction would feasibly do quite well, given the corpus it was trained on.
### RNN
Our basic RNN architecture worked quite well with an accuracy of 61%.
### LSTM
Finally, we tried a basic LSTM architecture, reaching an accuracy of 75.5%.

| Model | Performance (Accuracy) |
| --- | --- |
| LinearSVC |  91% |
| LSTM | 75.5% |
| RNN | 61% |
| CBOW | 47% |

## Other approaches
Given more time, we would have spent more time experimenting with different RNN and LSTM architectures, such as adding additional layers. Also, it should be noted we generally stuck to a 5 epoch, 0.001 learning rate training regimen. Additional time would also be spent tweaking hyperparameters.

## Bonus task: Headline Generation
In the spirit of experimentation and learning, we also attempted a headline generation LSTM model. This proved interesting to play with, if only to learn more about the nature of the task. Surprisingly, the LSTM architecture remains pretty much identical for the LSTM model used in the classification task. The main difference lies in the creation of the Dataset. Instead of using the headline and its respective category label as x and y, we instead create a dataset using the headline as x and a shifted version of the same headline as y.

Additionally, we may choose to add weights to certain related vocabulary by passing it in to the loss function used in training.

Here's an example of our results:

![gen1](https://user-images.githubusercontent.com/25912759/176728120-74f67bf6-cc8d-496c-b7e8-fe449b891b72.png)
> LSTM model before training - generated randomly

![gen2](https://user-images.githubusercontent.com/25912759/176728186-0a478dc9-f491-4e92-8d7d-91d1761f5320.png)
> LSTM model after 4 epochs of training

In this case, we were not able to add weights in the training set. As we can see, the generation results are a little promising after 4 epochs of training. There are still many UNK values, even after 10 minutes of training though. 

This may be a result of a couple of factors:
* Not enough training data - most NLP models are trained with millions of rows of data.
* Weighted training is highly needed.

Other interesting generation examples:

![police_gen](https://user-images.githubusercontent.com/25912759/176731308-32679402-97d8-491d-bffb-334bbeb23d69.png)
![team_gen](https://user-images.githubusercontent.com/25912759/176731348-cfac098c-a887-4b04-8130-fc287d6e316f.png)
![london_gen](https://user-images.githubusercontent.com/25912759/176731375-5b992606-d7c5-4b6e-9aa0-90a2df33dd9b.png)

## Other interesting problems
NLP on news headlines has a variety of interesting problems to explore. Given more time, we would have liked to do more investigation into the following:
* classification of category based on full article text
* predict author based on category and article text (based on style, type of article, etc.)

## Acknowledgements
Thank you for reading! If you have any questions about our code, methodology, etc. feel free to reach out! 
![ed_jol_molang](https://user-images.githubusercontent.com/25912759/176145234-ca153733-eb52-493c-b58c-c65cf17d76a5.png)
