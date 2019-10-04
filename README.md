# Sentiment Analysis: Concept, Analysis and Applications

<p align="center"> 
<img src="images/sentiment.jpg">
</p>

## What is Text Classification?

Text Classification is a process of classifying data in the form of text such as tweets, reviews, articles, blogs, etc... into predefined categories. Sentiment analysis is a special case of Text Classification where users’ opinion or sentiments about any product are predicted from textual data.

### Sentiment Analysis

Sentiment Analysis(Opinion mining) is the process of determining whether a piece of writing is positive, negative or neutral. A sentiment analysis system for text analysis combines natural language processing (NLP) and machine learning techniques to assign weighted sentiment scores to the entities, topics, themes and categories within a sentence or phrase. There can be other forms of sentiment analysis or opinion mining like predicting rating scale on product’s review, predicting polarity on aspects of a product, detecting subjectivity and objectivity in sentences etc.

Sentiment analysis helps data analysts within large enterprises gauge public opinion, conduct nuanced market research, monitor brand and product reputation, and understand customer experiences. In addition, data analytics companies often integrate third-party sentiment analysis APIs into their own customer experience management, social media monitoring, or workforce analytics platform, in order to deliver useful insights to their own customers.

## How does sentiment analysis work?

### The basics

Basic sentiment analysis of text documents follows a straightforward process:

1 Break each text document down into its component parts (sentences, phrases, tokens and parts of speech)
2 Identify each sentiment-bearing phrase and component
3 Assign a sentiment score to each phrase and component (-1 to +1)
4 Optional: Combine scores for multi-layered sentiment analysis

As you’ll see, the underlying technology is very complicated. But for a simple explanation of sentiment analysis, consider these sentences:

    Terrible pitching and awful hitting led to another crushing loss.
    Bad pitching and mediocre hitting cost us another close game.

Both sentences discuss a similar subject, the loss of a baseball game. But you, the human reading them, can clearly see that first sentence’s tone is much more negative.

Your brain figures this out by looking for and interpreting sentiment-bearing phrases – that is, words and phrases that carry a tone or opinion. These usually appear as adjective-noun combinations. In the examples above, the sentiment-bearing phrases are:

    Terrible pitching | awful hitting | crushing loss

    Bad pitching | mediocre hitting | close game
    
You have encountered words like these many thousands of times over your lifetime across a range of contexts. And from these experiences, you’ve learned to understand the strength of each adjective, receiving input and feedback along the way from teachers and peers.

When you read the sentences above, your brain draws on your accumulated knowledge to identify each sentiment-bearing phrase and interpret their negativity or positivity. Usually this happens subconsciously. For example, you instinctively know that a game that ends in a “crushing loss” has a higher score differential than the “close game”, because you understand that “crushing” is a stronger adjective than “close”.

So, why are we using baseball games to explain how human brains do sentiment analysis? The answer is simple: **computer sentiment analysis works (almost) the same way.**

In order to calculate the sentiment of a sentence first that sentence should be in the form that is readable by machine, and we know that machine understands only number(text is not readable by machine) so we have to map the text of sentence into some numbers so that it can b feed to the machine and apply the machine learning algorithm to calculate the sentiment of sentence. There are many ways where this can be done, like using :

    - Word Count
    - Tf-Idf Vector

etc...


## Applications

**How is sentiment analysis used?**
Broadly speaking, sentiment analysis is most effective when used as a tool for Voice of Customer and Voice of Employee. Business analysts, product managers, customer support directors, human resources and workforce analysts, and other stakeholders use sentiment analysis to understand how customers and employees feel about particular subjects, and why they feel that way.

**Sentiment analysis for voice of customer**
In the age of social media, a single viral review can burn down an entire brand. On the other hand, research by Bain & Co. shows that good experiences can grow 4-8% revenue over competition by increasing customer lifecycle 6-14x and improving retention up to 55%.

Automated sentiment analysis tools are the key drivers of this growth. By analyzing tweets, online reviews and news articles at scale, business analysts gain useful insights into how customers feel about their brands, products and services. Customer support directors and social media managers flag and address trending issues before they go viral, while forwarding these pain points to product managers to make informed feature decisions.

**Sentiment analysis for voice of employee**
The cost of replacing a single employee averages 20-30% of salary, according to the Center for American Progress. Yet 20% of workers voluntarily leave their jobs each year, while another 17% are fired or let go. To combat this issue, human resources teams are turning to data analytics to help them reduce turnover and improve performance.

Sentiment analysis helps workforce analysts and HR directors cut off employee churn at the source by understanding what employees are discussing and how they feel. Through rich analytics of employee surveys, Slack messages, emails, and other communications, HR teams get the info they need to proactively address pain points and improve morale.
