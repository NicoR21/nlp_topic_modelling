# NLP school project with Optimal Transport

## Goal of the project

#### OBJECTIVE 

This is a school project that I did with 2 friends of mine in early 2020. Our goal is to find the commentary that best 
defines our restaurant. We will use NLP (Natural Language Processing) techniques to do sentiment analysis and topic 
modelling to characterize the comments. 

We will use the optimal transport technique which will help us to create clusters to find the comment that best defines 
our restaurant, and compares those results with another topic modelling method : LDA (Latent Dirichlet Allocation).

I've redone this project up to where I finished it with my friends but with a more complete structure here on GitHub and
coding it in a more "Python way" thanks to what I've discovered about Python coding conventions.


#### DATASET

For this project we took a database with 1000 comments from a restaurant available on the 
[following website](https://acadgild.com/blog/analysis-of-restaurant-reviews-with-nlp) 


#### METHOD

We therefore assume that we take 1000 comments from a restaurant. Out of these 1000 comments, we are going to carry out 
a sentiment analysis. This technique will allow us to know whether the comment is positive or negative.

In a second step, we will use the optimal transport method to create clusters. These clusters will group together 
sentences that talk about the same subject. For example, all the comments talking about desserts in restaurants will be 
grouped in a cluster. 

Once these 2 techniques are done, we will create a table that will cross the results of the sentiment analysis and the 
results of the optimal transport. This table will allow us to know if a subject (cluster) is positive or negative. If 
we take the example of the comments on desserts, they will all be grouped in a cluster. The table will allow us to know 
whether the desserts have a positive or negative opinion. 

Once this analysis has been carried out, we will compare it to the LDA method (which uses distribution and not distance 
as the optimal transport). We proceed in the same way with the table that combines sentiment analysis and topic 
modelling. We then compare it with the first method (Optimal transport) to see which one is the most efficient and 
gives the most representative opinion.

Finally, we hope to be able to make a representative comment using GPT2, TextBlob or other techniques. These methods 
should enable us to make a comment that is grammatically and spelling correct.




## Organization of the repo

#### NOTEBOOKS

- In the notebook 01_sentiment_analysis.ipynb contains a quick and basic sentiment analysis to compare what do they call
negative / positive comments and what does the algorithm describes as positive / negative 
- In the notebook 02_optimal_transport.ipynb, we applied the method of optimal transport provided by our professor 
- In the notebook 03_Latent_Dirichlet_Allocation.ipynb, we implemented an other topic modelling method : 
[LDA](https://www.machinelearningplus.com/nlp/topic-modeling-gensim-python/)
- The notebook 04_cluster_analysis.ipynb compares the hierarchical clustering found by each topic modelling method to 
see potential differences between those methods

#### RESOURCES

- The mallet-2.0.8 that allowed us to perform the LDA model
- .csv files will be stored there when running the .to_csv() commands


## Launching

- Git clone the project
- pip install requirements
- Download the dataset from the link given above and store it in the "resources" file
- Run the notebooks one by one in the right order and uncomment the cells with a df.to_csv("...") to be able to run the 
last notebook 
 

## Results

Here is the dataframe we have with the comment and the topic to which it belongs according to our 2 methods.
We have the 10 most representatives keyword of each topic generated by the LDA method. Optimally we would have like to 
generate a coherent sentence representing each topic thanks to a text generation API. But the results we get were not as
good as expected.

|Review	| Liked | polarity | sentiment_binary |	sentiment_type | cluster_OT | dominant_topic_LDA | topic_percentage_contribution |	keywords |
| :---: | :---: | :------: | :--------------: | :------------: | :--------: | :----------------: | :---------------------------: | :-------: |
|0 | Wow... Loved this place. | 1 | 0.40 | 1 | Positive | 7 | 7.0 | 0.1154 |	love, amazing, taste, meal, bland, find, suck,... |
|1 | Crust is not good. | 0 | -0.35 | 0 | Negative | 0 | 4.0 | 0.1175 |	good, quality, thing, enjoy, sushi, price, dis...
|2 | Not tasty and the texture was just nasty. | 0 | -1.00 | 0 | Negative | 3 | 4.0 | 0.1132 | good, quality, thing, enjoy, sushi, price, dis...
|3 | Stopped by during the late May bank holiday of... | 1 | 0.20 |	1 |	Positive | 6 | 9.0 | 0.1169 | friendly, minute, chicken, pizza, menu, price,...
|4 | The selection on the menu was great and so wer... | 1 | 0.80 |	1 | Positive | 1 | 9.0 | 0.1235	| friendly, minute, chicken, pizza, menu, price,...


Sentiment by cluster with Optimal transport method

| sentiment_type | Negative | Positive   |
| :------------: | :------: | :--------: |
| cluster_OT     |          |            |
|   0	         |  0.574074 |	0.425926 |
|   1	         |  0.455882 |	0.544118 |
|   2	         |  0.534091 |	0.465909 |
|   3	         |  0.535714 |	0.464286 |
|   4	         |  0.482759 |	0.517241 |
|   5	         |  0.385542 |	0.614458 |
|   6	         |  0.500000 |	0.500000 |
|   7	         |  0.493333 |	0.506667 |
|   8	         |  0.484375 |	0.515625 |
|   9	         |  0.446154 |	0.553846 |


Sentiment by cluster with LDA method

| sentiment_type         | Negative | Positive   |
| :--------------------: | :------: | :--------: |
| dominant_topic_LDA     |          |            |
| 0.0                    |	0.593103 |	0.406897 |
| 1.0                    |	0.583893 |	0.416107 |
| 2.0                    |	0.429825 |	0.570175 |
| 3.0                    |	0.545455 |	0.454545 |
| 4.0                    |	0.428571 |	0.571429 |
| 5.0                    |	0.389610 |	0.610390 |
| 6.0                    |	0.311688 |	0.688312 |
| 7.0                    |	0.372549 |	0.627451 |
| 8.0                    |	0.540230 |	0.459770 |
| 9.0                    |	0.520548 |	0.479452 |
# nlp_topic_modelling
