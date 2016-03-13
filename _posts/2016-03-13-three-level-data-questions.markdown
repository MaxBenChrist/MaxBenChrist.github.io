---
layout: post
title:  "Who? What? Where?"
date:   2016-03-13 20:00:00 +0100
categories: working techniques
comments: True
---

__TLDR: The following posts shows a three step paradigm on how to make yourself familiar with column based data sources.__

---
<br>

# The Problem

In the beginning of every Data Science project you have to make yourself familiar with given data sources. To do so, a Data Scientist has to understand the underlying business processes that generate those data. This is especially true if one fulfills more of a consulting role where you switch industries, clients, investigated issues and with it the data structures every few months.


![Before you understand the data](https://media.giphy.com/media/ohdY5OaQmUmVW/giphy.gif)

Depending on the industry, data generating process can be very complex and as always the 'devil is in the details'. Further, stakeholders often do not understand important concepts for the successful application of Machine Learning applications. So the Data Scientists has to make sure that the right questions are asked. How do you make sure that you do not miss any details during discussions with the stakeholders?

Even experienced statisticians and data scientists often jump between asking questions on a global level („How can I associate Table 1 with Table 2") and going into detail by asking very specific questions („What does Value 3 in Row 5 in Table 3 mean?“).

What is dangerous of asking in such a unstructured fashion? It can confuse the client. He can not deduce how deep your current understanding of the data is. Detailed questions that are asked too early could leave the impression that all general questions are already solved. Further one could miss important question, for example you forget to ask how one can relate a certain tables to the others. If you do this later during the building of statistical models, it could appeal unprofessional.

I developed a three phase question method for myself.
As I could not find any dedicate Data Science question method or guideline on how to ask questions as a Data Scientist I decided to share my approach.

# The Solution

So how should we structure the asking process? The principle is to start by getting to know the data on a global overview and then later zoom in. So we start asking very general questions that are sharpened. It is not a strict 3 step tutorial but more of a way of structuring your thoughts while getting a deep understanding of the pain points in the project.

My method works as following. There are three levels in the familiarizing process. After completing all questions of one level, one moves one phase forward. The three level in sequential order are: Tabular, column and cell level. The following picture visualizes the three phases of the make-yourself-familiar process:

![The three levels: Tabular, column and cell](/images/www_overview_level_questions.png)

The three phases go as follows:

__1.) Tabular level:__

Here questions on the information that the different tables contain and the relation between them are under investigation:

*   Association: How can the different tables be associated? How can one construct keys to associate them? (ALWAYS ask this question![^1])
*   Origin: Where do the different tables originate from? (System, process)
*   Construction: Were they joined from other tables?
*   Stakeholder: How were the tables collected? Which organization, departments or persons were involved?
*   ...

__2.) Row level:__

*   Processes: How are the process for collecting the data of this column? Was it generated automatically or by human?
*   Range of values: What is the expected range for the different values. This information can be used to detect outliers.
*   Purpose: What is the meaning of the columns? Which information should it contain?
*   ...

__3.) Cell level:__

*   Meaning of values: What does the values mean? What is the meaning of abbreviations? 
*   Ordering of values: Is there a natural ordering in certain classes? (Think of credit classes A, B, C where A is the most solvent, B is medium solvent and C is less solved)
*   Meaning if missing values: Is there really missing information or was the information hidden by purpose?
*   ...




# Positive side effects

Now in my work as a data scientist I always try to respect this order when getting to know new data sources.
I would love to get your feedback and change suggestions. Just leave a reply, send me an email or hit me up on twitter.

----- 
[^1] In one of the projects I worked with there were several columns with the same name "ID". It was obvious that those were used as keys to associate the tables together. What was not clear was that had to add 1 to every "ID" in one table to get the right association key to the other tables.


*Example: I was involved in a project where there was a key field in several tables. It had the same name „unit number“ in all tables with the same range. However in one table one had to subtract 1 of the unit number to relate it to the other tables. It was clear to all stake holders but of course not to anybody outside the company. Thanks to my question method I found that out pretty early in the project.




There are several advantages of my structured question method. It will help you structure your thoughts and the whole understanding process. Further it demonstrates a escalation to your clients. From the detail level of the questions your clients can get a feeling on how deep your understanding on the current data is. Further you can omit certain detail questions if you find out that for example a certain table can not be embedded in the model in an early phase. For example if the data in one table can not be reliable linked to other tables, you would probably omit that table in your analyses.

The method is so far only described for relational data where several tables have to be connected. So only for column based data. Probably It can generalized to other data sources as well but I am lacking experience in those fields.

Traditionally you start such a project with a Kick-Off Meeting to make first contact with project related stakeholders. Most projects will undergo three main phases: Analytics, Prediction and Delivery.


During the Analytics phase a deep understanding of the data and its processes are achieved. Further the data normalization is performed which is a standardization on shared value ranges and formats is realized. Later the data is cleaned which is a elimination of outliers and redundant inconsistent samples. 
Further a association of the data sources is performed by searching for keys and aggregation of variables. 
After this phase the data quality and understanding should allow the following feature engineering and training of machine learning models.

Accordingly in the prediction phase the tasks of interest for the project are investigated. Features are constructed, different Machine Learning models are build and evaluated.

Later in the project in the final delivery phase the results are collected. A story is told by searching for data stories, data quality report, etc.



