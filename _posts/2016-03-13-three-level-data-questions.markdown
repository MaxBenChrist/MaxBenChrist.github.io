---
layout: post
title:  "Who? What? Where?"
date:   2016-03-13 20:00:00 +0100
categories: working techniques
comments: True
---

__TLDR: The following posts sdescribes a three step paradigm on how to make yourself familiar with column based data sources.__

---
<br>

# The Problem

In the beginning of every Data Science project you have to make yourself familiar with given data sources. To do so, you as a Data Scientist has to understand the underlying business processes that generate those data. This is especially true if one fulfills more of a consulting role where you switch industries, clients, investigated issues and with it the data structures every few months.


![Before you understand the data](https://media.giphy.com/media/ohdY5OaQmUmVW/giphy.gif)

Depending on the industry, data generating processes can be very complex and as always the 'devil is in the details'. Further, stakeholders often do not understand important concepts for the successful application of Machine Learning applications. So the Data Scientists has to make sure that the right questions are asked. How do you make sure that you do not miss any details during discussions with the stakeholders?

Even experienced statisticians and Data Scientists often jump between asking questions on a global level 

*"How can I associate Table 1 with Table 2"*
{: style="text-align: center"}

and going into detail by asking very specific questions

*"What does Value 3 in Row 5 in Table 3 mean?“.*
{: style="text-align: center"}

What is dangerous of asking in such a unstructured fashion? It can confuse the client. He can not deduce how deep your current understanding of the data is. Detailed questions that are asked too early could leave the impression that all general questions are already solved.

Further one could miss important point, for example you forget to ask how one can relate a certain tables to the others. If you do this later during the building of statistical models, it could appeal unprofessional.

I developed a three phase question method for myself.
As I could not find any Data Science question structuring method or guideline I decided to share my approach.

# The Solution

So how should we structure the asking process? The principle is to start by getting to know the data on a global overview and then later zoom in. So we start asking very general questions that are continuously sharpened. It is not a strict three step tutorial but more of a way of structuring your thoughts while getting a deep understanding of the data sources in the project.

My method works as following. There are three levels in the familiarizing process. After completing all questions of one level, one moves one level forward. The three level in sequential order are: Tabular, column and cell level. The following picture visualizes the three phases of the make-yourself-familiar process:

![The three levels: Tabular, column and cell](/images/www_overview_level_questions.png)

The three phases go as follows:

__1.) Tabular level:__

Here questions on the information that the different tables contain and the relation between them are under investigation:

*   Association: How can the different tables be associated? How can one construct keys to associate them? (ALWAYS ask this question! [^1] )
*   Origin: Where do the different tables originate from? This could relate to technical systems, departments or processes.
*   Construction: Were they joined from other tables or were they create from database dumps?
*   Stakeholder: How were the tables collected? Which organization, departments or persons were involved?
*   ...

__2.) Row level:__

Now we understand the tables which is why we start asking questions about the different columns.

*   Purpose: What is the meaning of the different columns? Which information should the contain?
*   Processes: How was the data for this column collected? Was it generated automatically or by human?
*   Range of values: What is the expected range for the different values. This information can be used to detect outliers.
*   ...

__3.) Cell level:__

Now we have a deeper understanding of both columns and tables which is why we start caring about individual values.

*   Meaning of values: What does the different values mean? What is the meaning of abbreviations? 
*   Ordering of values: Is there a natural ordering in certain classes? (Think of credit classes A, B, C where A is the most solvent, B is medium solvent and C is less solved)
*   Meaning if missing values: Is there really missing information or was the information hidden by purpose?
*   ...

In total this methods seems very obvious but I noticed that many, even experienced Data Scientists, under stress become chaotic in their getting-familiar-process.

# Positive side effects

Now in my work as a Data Scientist I always try to respect this order when getting to know new data sources.

There are several advantages of my structured question method. It will help you structure your thoughts and the getting-familiar-with-the-data process. Further it demonstrates a escalation to your clients and stakeholders. From the detail level of the questions your clients can get a feeling on how deep your understanding is. 

Further you can omit certain detail questions if you find out that a certain table can not be linked to the other tables. This will help you to save valuable time and be more productive. For example if the data in one table can not be reliable linked to other tables, you would probably omit that table in your analyses.

The method is thought for relational data where several tables have to be connected. Probably it can generalized to other data sources as well but I am lacking experience in those fields.

I would love to get your feedback and change suggestions. Just leave a comment, send me an email or hit me up on twitter. Further I uploaded to scheme to github so you can make suggestions there as well.

----- 
[^1]: In one of the projects I participated there were several tables having columns with the same name "ID". It was obvious that those were used as keys to associate the tables together. What was not clear was that one had to add 1 to every "ID" in one table to get the right association key to the other tables. We would have missed this and probably build wrong features if we would had not asked detailed questions about the association process.