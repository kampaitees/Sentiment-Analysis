# Sentiment Analysis: Concept, Analysis & Applications

<p align="center"> 
<img src="images/sentiment.jpg">
</p>

## What is Text Classification?

Text Classification is a process of classifying data in the form of text such as tweets, reviews, articles, blogs, etc... into predefined categories. Sentiment analysis is a special case of Text Classification where users’ opinion or sentiments about any product are predicted from textual data.

### Sentiment Analysis

Sentiment Analysis(Opinion mining) is the process of determining whether a piece of writing is positive, negative or neutral. A sentiment analysis system for text analysis combines natural language processing (NLP) and machine learning techniques to assign weighted sentiment scores to the entities, topics, themes and categories within a sentence or phrase. There can be other forms of sentiment analysis or opinion mining like predicting rating scale on product’s review, predicting polarity on aspects of a product, detecting subjectivity and objectivity in sentences etc.

Sentiment analysis helps data analysts within large enterprises gauge public opinion, conduct nuanced market research, monitor brand and product reputation, and understand customer experiences. In addition, data analytics companies often integrate third-party sentiment analysis APIs into their customer experience management, social media monitoring, or workforce analytics platform, to deliver useful insights to their customers.

## Core Buildnig Block

                                                       
                                                        SENTENCE
                                                           ||
                                                           ||
                                                           ||
                                                           \/
                                                 |----------------------|
                                                 |  Sentence Sentiment  |
                                                 |      Classifier      |
                                                 |----------------------|     
                                                          /  \
                                                         /    \
                                                        /      \
                                                       /        \
                                               |----------|    |----------|
                                               | POSITIVE |    | NEGATIVE |
                                               |----------|    |----------|
                                               
                                               
## How does sentiment analysis work?

### The basics

Basic sentiment analysis of text documents follows a straightforward process:

- Break each text document down into its parts (sentences, phrases, tokens and parts of speech)
- Identify each sentiment-bearing phrase and component
- Assign a sentiment score to each phrase and component (-1 to +1)
- Optional: Combine scores for multi-layered sentiment analysis

As you’ll see, the underlying technology is very complicated. But for a simple explanation of sentiment analysis, consider these sentences:

                            Terrible pitching and awful hitting led to another crushing loss.
                            Bad pitching and mediocre hitting cost us another close game.

Both sentences discuss a similar subject, the loss of a baseball game. But you, the human reading them, can see that the first sentence’s tone is much more negative.

Your brain figures this out by looking for and interpreting sentiment-bearing phrases – that is, words and phrases that carry a tone or opinion. These usually appear as adjective-noun combinations. In the examples above, the sentiment-bearing phrases are:

                            Terrible pitching | awful hitting | crushing loss
                            Bad pitching | mediocre hitting | close game    
    
You have encountered words like these many thousands of times over your life across a range of contexts. And from these experiences, you’ve learned to understand the strength of each adjective, receiving input and feedback along the way from teachers and peers.

When you read the sentences above, your brain draws on your accumulated knowledge to identify each sentiment-bearing phrase and interpret their negativity or positivity. Usually, this happens subconsciously. For example, you instinctively know that a game that ends in a “crushing loss” has a higher score differential than the “close game” because you understand that “crushing” is a stronger adjective than “close”.

So, why are we using baseball games to explain how human brains do sentiment analysis? The answer is simple: **computer sentiment analysis works (almost) the same way.**

In order to calculate the sentiment of a sentence first that sentence should be in the form that is readable by machine, and we know that machine understands only number(text is not readable by machine) so we have to map the text of sentence into some numbers so that it can b feed to the machine and apply the machine learning algorithm to calculate the sentiment of sentence. There are many ways where the preprocessing of the input sentence can be done :

- **Word Count**

- **Tf-Idf Vector**

In this article we are going to discuss **Word Count**, **TF-IDF** method only.

## What is Word Count method?
Here we break the sentence into its component words then calculate the count of each word and store the information in form of python dictionary with the word as a key and count of each word as the value of that key.

**Example**
    Wow!, I love the dish prepared here in the restaurant. This is the best restaurant I think in this city

**Word Count Vector for the above sentence will be like**

     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     |   1   |  2  |   1    |   3   |    1   |     1     |   1   |  2  |      2       |    2   |   1  |    1   |    1    |   1   |       
     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     |  Wow  |  I  |  love  |  the  |  dish  |  prepare  | here  | in  |  restaurant  |  this  |  is  |  best  |  think  | city  |                     

Above vector is the **Word Count** vector but you will be wondering what I didn't include '!', '.' and why 'prepare' instead of 'prepared' because the punctuation marks don't tell anything about the sentiment and also whether the verb is past or present it doesn't matter so all these things are removed while using different **NLP** libraries.

So same **word Count** vector will be created for all the sentences and in the above **Word Count** vector I had included only the words which are in the sentence but while doing using libraries there different corpus of words which are already there in the libraries like in **NLTK** there are around 10000 words so only a new dictionary is created every time and count is included in those dictionaries.
So from this, we can see that this type of vectors is very sparse as out of 10000 words there is a possibility that only 10-20 words are there in a sentence so rest is just zero's.
so after calculating the **Word Count** vector, we feed this vector to the classifier to train it and later it can be used to predict the sentiment of the sentence.

## Limitation of Word Count method

- Frequently occurring words present in all files of corpus irrespective of the sentiment, like in this case, ‘the movie’, ‘acting’, etc will be treated equally like other distinguishing words in the document.

- Stop words will be present in the vocab if not processed properly.

- Rare words or keywords which can be distinguishing will not get special weight.

**Here comes tf-idf weighting factor which eliminates these limitations. The first question that comes to your mind  is “what does tf-idf do to these conventional features ?”.**

## What is TF-IDF method?

Full form of **TF-IDF** is **TERM FREQUENCY-INVERSE DOCUMENT FREQUENCY**

**TERM FREQUENCY**

It increases the weight of the terms (words) that occur more frequently in the document. Quite intuitive, right ?? So it can be defined as  tf(t,d) = F(t,d) where F(t,d) is number of occurrences of term ‘t’ in documented’. But practically, it seems unlikely that thirty occurrences of a term in a document truly carry thirty times the significance of a single occurrence. So, to make it more pragmatic, we scale tf in a logarithmic way so that as the frequency of terms increases exponentially, we will be increasing the weights of terms in an additive manner.

                                          tf(t,d) = log(F(t,d))
**INVERSE DOCUMENT FREQUENCY**

It diminishes the weight of the terms that occur in all the documents of corpus and similarly increases the weight of the terms that occur in rare documents across the corpus. The rare keywords get special treatment and stop words/non-distinguishing words get punishment. We define idf as:
                                    
                                        idf(t,D) = log(N/Nt∈d)


Here, ‘N’ is the total number of files in the corpus ‘D’ and ‘Nt ∈ d‘ is the number of files in which the term ‘t’ is present. By now, we can agree to the fact that tf is an intra-document factor which depends on individual document and idf is a per corpus factor which is constant for a corpus. Finally, We calculate tf-idf as:

                                        tf-idf(t,d,D) = tf(t,d) . idf(t,D)

Let's take the above example of **Word Count** method:

**Term Freuency Vector**

     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     |   1   |  2  |   1    |   3   |    1   |     1     |   1   |  2  |      2       |    2   |   1  |    1   |    1    |   1   |       
     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     |  Wow  |  I  |  love  |  the  |  dish  |  prepare  | here  | in  |  restaurant  |  this  |  is  |  best  |  think  | city  |
     

Yes!, term frequency vector will remain same because it is nothing but frequency of the each in the sentence. Whatever, changes are there is reflected form the **Inverse Document Ferequency** vector.

**Inverse Document Frequency Vector**

     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     | 2.493 | .04 |  3.18  | 0.002 |  0.03  |  0.00784  | 0.041 | .01 |    0.0456    | 0.0034 | .002 |  3.99  |  0.16   | 0.145 |      
     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     |  Wow  |  I  |  love  |  the  |  dish  |  prepare  | here  | in  |  restaurant  |  this  |  is  |  best  |  think  | city  | 


**Final Vector(Input to the Machine Learning Model)**

                                        Term Frequency Vector * Inverse Document Frequency 
                                                             ||
                                                             ||
                                                             ||
                                                             \/
     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     | 2.493 | .08 |  3.18  | 0.006 |  0.03  |  0.00784  | 0.041 | .02 |    0.0912    | 0.0068 | .002 |  3.99  |  0.16   | 0.145 |      
     |-------|-----|--------|-------|--------|-----------|-------|-----|--------------|--------|------|--------|---------|-------|       
     |  Wow  |  I  |  love  |  the  |  dish  |  prepare  | here  | in  |  restaurant  |  this  |  is  |  best  |  think  | city  |

As we know that the sentiment from the sentence is **Positive** so the words which are actaully positive from the sentence are **Wow**, **love**, **best**. From final product of **TF & IDF** we can see that more weightage is given to these important words than unimportant words like **I**, **the**, **i** etc.. thus in this we can say that this method is going to work far more better than **Word Count** method as here we are giving more accurate data to the alogrithm than before.

Enough with the theory part, let’s get hands-on and write python code for extracting such features using **GraphLab** machine learning library. It is an open-source python ML library which can be used by separate installation following [this](https://turi.com/download/install-graphlab-create.html).

## Importing Libraries

    import graphlab

## Loading Dataset
 
    products = graphlab.SFrame('amazon_baby.gl/')
 
    products.head(5)

![Dataset](images/2019-10-05%20(8).png)

## Exploratory Data Analysis

    products['rating'].show()

![Histogram1](images/histogram_Value%20of%20_SArray_.png)
![Histogram2](images/2019-10-04%20(2).png)

    products['rating'].show(view = 'Categorical)

![Histogram4](images/2019-10-05%20(3).png)
 
    products['name'].show()

![Bar Graph](images/2019-10-04%20(4).png)

    products.show()

![Graph](images/2019-10-05%20(9).png)

## Add Word Count Vector to exiting SFrame
 
    products['word_count'] = graphlab.text_analytics.count_words(products['review'])
 
    products.head(5)

![View](images/2019-10-05%20(6).png)

## Examining the reviews for most-sold product: 'Vulli Sophie the Giraffe Teether'

    giraffe_reviews = products[products['name'] == 'Vulli Sophie the Giraffe Teether']

    giraffe_reviews['rating'].show(view='Categorical')```

![Histogram3](images/2019-10-05%20(1).png)

## Define what's a positive and a negative sentiment
  
    products = products[products['rating'] != 3]
 
    products['sentiment'] = products['rating'] >=4
 
    products.head(5)

![View](images/2019-10-04%20(7).png)


## Let's train the Classifier(Logistic Regression)

    train_data,test_data = products.random_split(.8, seed=0)
    
    sentiment_model = graphlab.logistic_classifier.create(train_data, target='sentiment', features=['word_count'],     validation_set=test_data)
    
![Model1](images/2019-10-04%20(11).png)                                
 
![Model2](images/2019-10-04%20(5).png)

## Evaluate the sentiment model

    sentiment_model.evaluate(test_data, metric='roc_curve')
    
![Evaluate1](images/2019-10-04%20(12).png)
 
    sentiment_model.show(view='Evaluation')

![Evaluate2](images/line_False%20Positive%20Rate_True%20Positive%20Rate.png)
 
![Evaluate3](images/2019-10-04%20(13).png)
 
## Applying the learned model to understand sentiment for Giraffe

    giraffe_reviews['predicted_sentiment'] = sentiment_model.predict(giraffe_reviews, output_type='probability')

    giraffe_reviews.head()

![View](images/2019-10-04%20(14).png)

## Sort the reviews based on the predicted sentiment and explore¶
 
    giraffe_reviews = giraffe_reviews.sort('predicted_sentiment', ascending=False)
 
    giraffe_reviews.head()

![View](images/2019-10-04%20(15).png)

## Most positive reviews for the giraffe

    giraffe_reviews[0]['review']
 
![Review](images/2019-10-04%20(16).png)


## Applications

**How is sentiment analysis used?**

Broadly speaking, sentiment analysis is most effective when used as a tool for Voice of Customer and Voice of Employee. Business analysts, product managers, customer support directors, human resources and workforce analysts, and other stakeholders use sentiment analysis to understand how customers and employees feel about particular subjects, and why they feel that way.

**Sentiment analysis for the voice of customer**

In the age of social media, a single viral review can burn down an entire brand. On the other hand, research by Bain & Co. shows that good experiences can grow 4-8% revenue over the competition by increasing customer lifecycle 6-14x and improving retention up to 55%.

Automated sentiment analysis tools are the key drivers of this growth. By analyzing tweets, online reviews and news articles at scale, business analysts gain useful insights into how customers feel about their brands, products and services. Customer support directors and social media managers flag and address trending issues before they go viral while forwarding these pain points to product managers to make informed feature decisions.

**Sentiment analysis for the voice of employee**

The cost of replacing a single employee averages 20-30% of salary, according to the Center for American Progress. Yet 20% of workers voluntarily leave their jobs each year, while another 17% are fired or let go. To combat this issue, human resources teams are turning to data analytics to help them reduce turnover and improve performance.

Sentiment analysis helps workforce analysts and HR directors cut off employee churn at the source by understanding what employees are discussing and how they feel. Through rich analytics of employee surveys, Slack messages, emails, and other communications, HR teams get the info they need to proactively address pain points and improve morale.


## Conclusion

The age of getting meaningful insights from social media data has now arrived with the advance in technology. The above **Amazon review** case study gives you a glimpse of the power of Contextual Semantic Search. It’s time for your organization to move beyond overall sentiment and count-based metrics. Companies have been leveraging the power of data lately, but to get the deepest of the information, you have to leverage the power of AI, Deep learning and intelligent classifiers like Contextual Semantic Search and Sentiment Analysis.

Hope I have made justice to Tf-Idf features in this article. I have tried to explain the usefulness of these features with sentiment analysis application. Beginners are encouraged to implement it, match their outputs with the results shown here. Also, try to analyse the difference between conventional word count features and tf-idf weighted features.

The machine learning models (Logistic Regression) have been implemented here without giving a mathematical background. It may overwhelm the readers with so much information in a single article. One may apply other variants of these classifiers and other classifiers available in the **Graph Lab** to make comparison and analyse the underlying differences among them. Here, the purpose was to present an understanding of **Word Count** and **Term Frequency & Inverse Document Frequency** and its importance in text mining applications.

In addition, the full python implementation of sentiment analysis on **Amazon review** dataset using **Logistic Regression** can be found on GitHub link [here](https://github.com/kampaitees/Senitment-Analysis/blob/master/Amazon%20Product%20Sentiment%20Analysis.ipynb).

If you liked the post, follow my GitHub([**@kampaitees**](https://github.com/kampaitees)) to get updates about the upcoming articles. Also, share this article so that it can reach out to the readers who can gain from this. Please feel free to discuss anything regarding the post. I would love to hear feedback from you.
