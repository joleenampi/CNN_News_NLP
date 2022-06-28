# CNN Article Headline Classification
### Joleena Marshall & Edith Lee (Cohort 10)

## Introduction
Natural language processing is currently one of the most compelling areas of machine learning. Common applications in our daily lives include chatbots (on many consumer websites), search recommendations (on search engines), sentence completion (email, text, etc.), and many more. One widely available dataset is the body of news articles available to us on various news sites. 

For the purposes of this project, we selected a [Kaggle dataset](https://www.kaggle.com/datasets/hadasu92/cnn-articles-after-basic-cleaning) of 40k news articles to experiment with. The data includes the article's author, publish date, category, section, headline, description, and full article text. As such, we have a variety of possible directions to explore.

## Our problem
Since our data includes convenient labels for the category of article published, we decided to explore the use of various deep learning models on classifying article category. Using just the headline, we want to see if we're able to predict the category of the article.

## Data
For the purposes of understanding our resulting models, we conducted some basic EDA on the data at hand.

To begin, we investigated the distribution of categories across our dataset.

![image](https://user-images.githubusercontent.com/25912759/176139771-c85ca0cd-8381-405f-8523-5e246b15a5a6.png)
> Horizontal bar chart of news article categories and their frequencies.

From this, we are able to conclude there is a major (unexpected) imbalance in article categories. By far, the two most common categories were news and sports. This should be kept in mind when we evaluate model accuracy, since we do not have a large enough train set for some of these categories to perform extremely well.

Next, we investigated the distribution of news sections.
![image](https://user-images.githubusercontent.com/25912759/176141093-a474b282-c0d9-4ed3-bc69-87066738a1fe.png)
> Horizontal bar chart of news article sections and their frequencies.

To display these findings nicely, we chose to hide any sections that occurred with a frequency less than 50 times. It should be noted, however, that there were a little of 300 articles that had less commonly observed sections. Since there are no clear pluralities in article section, we chose not to use Section in our classification problem.

Additionally, we conducted investigations into the headlines themselves. After tokenizing and lemmatizing the headlines, and removing any commonly occurring stopwords (including CNN), we looked into commonly occuring words by category. 

For the sake of brevity, we've included the distribution of commonly observed words to the two largest categories - 'news' and 'sports'. We've also limited the barplot to the top 25 most commonly appearing words.

![image](https://user-images.githubusercontent.com/25912759/176143653-2fa83a31-7e39-43e9-83a7-89899c15a518.png) ![image](https://user-images.githubusercontent.com/25912759/176143755-21c73a5c-6b6d-4866-9683-ce983e67f908.png)



## Findings:

### Baseline
### CBOW
### BERT
### LSTM

## Other approaches

## Other interesting problems
NLP on news headlines has a variety of interesting problems to explore. Given more time, we would have liked to do more investigation into the following:
* classification of category based on full article text
* predict author based on category and article text
* generate the headline using the article body

## Acknowledgements
Thank you for reading! If you have any questions about our code, methodology, etc. feel free to reach out! 
![ed_jol_molang](https://user-images.githubusercontent.com/25912759/176145234-ca153733-eb52-493c-b58c-c65cf17d76a5.png)
