---
layout: post
title:  "Five conditions to identify AI-ready business processes"
date:   2016-09-05 20:00:00 +0100
categories: Consulting, Business Processes, Machine Learning
comments: True
tldr: Judging if machine learning can enhance your business is hard. I will show five key aspects of AI-worthy business processes.
---

__TLDR: Judging if machine learning can enhance your business is hard. I will show five key aspects of AI-worthy business processes.__

---
<br>


As the buzzwords Big Data, Artificial Intelligence, Machine Learning and Data Science are on everybody lips, I am more and more often approached by friends to discuss the potential of Machine Learning for their line of work.

<figure>
<center>
  <img src="/images/20170522_machine_learning_everywhere.jpeg" alt="Maschine Learning is everywhere" style="width: 60%;" rel="nofollow"/>
  <figcaption>
  <i> Machine Learning feels like a mega trend
  </i>
</figcaption>
  </center>
</figure>

For someone without Data Science experience it can be hard to judge where Machine Learning or AI techniques can generate business value. So, in this blog post, I will sketch five characteristics of business processes that are worthy to be enhanced by Machine Learning.

By the way, I will use the term Machine Learning synonymously to Artificial Intelligence to denote the usage of statistical techniques to develop learning systems.

### Everything in a business can be expressed as business process

So first of all, what is a business process? According to [wikipedia](https://en.wikipedia.org/wiki/Business_process){:rel="nofollow"} it is

*"A business process or business method is a collection of related, structured activities or tasks that produce a specific service or product (serve a particular goal) for a particular customer or customers.".*

So basically, everything that happens in a business is a business process. Well, that is easy. When I think about a business process, I visualize a flow chart, similar to this diagram

<figure>
<center>
  <img src="/images/20170514_businessprocess.png" alt="Diagram of a business process" style="width: 60%;" rel="nofollow"/>
  <figcaption> <i> A business process can be visualized as a flowchart of decisions
(image by <a href="https://www.flickr.com/photos/davegray/5630708345" rel="nofollow">Dave Gray</a>)
</i></figcaption>
  </center>
</figure>

I feel that Machine Learning in the near future will be most beneficial to enhance existing business processes.
There are some applications like autonomous driving or the google translator app that are disruptive and create totally new value chains, but the majority of applications/startups is based on existing business cases.

---
<br>

### Examples for the successful application of Machine Learning

So, how can one find business areas that are worthy to be enhanced the holy AI grail? Let us start with some examples where AI already creates value:

1.    _[Replenishment forecasting](https://www.blue-yonder.com/en/solutions/replenishment-optimization){:rel="nofollow"}_: Forecasts about the demand for singular articles can be used to anticipate future sales and order accordingly, reducing out of stock situations or waste while keeping the overall stock level low.

2.    _[Optimization of service routes based on failure forecasts](https://en.wikipedia.org/wiki/Predictive_maintenance)_: One can use forecasts about failures in the near future to organize service schedules and routes not based on intervals (as in classic, periodic maintenance) but based on the individual usage and risk profile. This is denoted as predictive maintenance.

3.    _[Classification of mails that contain spam](http://s3.amazonaws.com/academia.edu.documents/43906061/A_review_of_machine_learning_approaches_20160319-23716-gvrql2.pdf?AWSAccessKeyId=AKIAIWOWYYGZ2Y53UL3A&Expires=1495448535&Signature=uM2RheoTMvC0JT8gDZ%2B5ZQSriyw%3D&response-content-disposition=inline%3B%20filename%3DA_review_of_machine_learning_approaches.pdf){:rel="nofollow"}_: Based on the content,  metadata and context, a classification algorithm can estimate the probability that a given mail contains spam.

4.   _[Personalized marketing or prices](https://www.blue-yonder.com/en/solutions/price-optimization){:rel="nofollow"}_. AI can help to tailer promotions or discounts to a clients profile, which increases user engagement, revenue, conversion rate and other KPIs.

5.    _[Detection of fraudulent transactions](https://www.kaggle.com/dalpozz/creditcardfraud){:rel="nofollow"}_: Machine Learning can detect fraudulent payments by considering many factors such as the trustworthiness of the vendor, the recent cardholder’s behavior, time and location factors etc.

If we visualize those business processes as a flowcharts of decision, then in all those examples AI is used to automate one or multiple decisions in the business process:

<figure>
<center>
  <img src="/images/20170514_businessprocess_uncertainty.jpeg" alt="Diagram of a maschine learning enhanced business process" style="width: 60%;" rel="nofollow" />
  <figcaption> <i> A decision is made by a Machine Learning algorithm (abbreviated as ML here, image still by <a href="https://www.flickr.com/photos/davegray/5630708345" rel="nofollow">Dave Gray</a>)
</i></figcaption>
  </center>
</figure>

Further, there are some more things that all those applications have in common. They fulfill five conditions.

---
<br>

### Five conditions to enhance by AI

Those are all decisions that can be enhanced by machine learning. So, what do those business cases have in common? They fulfill five important characteristics:

#### _Uncertainty in the optimal decision_:

If the business process is already deterministic, then there is no needs to deploy machine learning to automate it. In example 1 it is not clear how much the customers will buy while in 3 it is not clear if a mail is spam or not.

<figure>
<center>
  <img src="/images/20170522_uncertainty.png" alt="Uncertainty in the optimal decision" style="width: 30%;" rel="nofollow"/>
<!--  <figcaption>
  <i> Uncertainty in the optimal decision
 </i>
 </figcaption> -->
  </center>
</figure>

<br>

#### Lots of small/micro decisions and not big decisions:

An unfitting example for a ML process would be the decision when to start a global sale. This stands in contrast to lots of small decisions such as which product to put on sale. Also you could automate which customers to send marketing material, like in 4.
For the application of machine learning, we need many „small“ business processes that are frequently made. So, focus on operational and not strategic decisions.

<figure>
<center>
  <img src="/images/20170522_small_decisions.png" alt="Micro decisions" style="width: 30%;" rel="nofollow"/>
<!--  <figcaption>
  <i> Micro decisions
 </i>
 </figcaption> -->
  </center>
</figure>

<br>

#### Direct impact:

Real value is only generated by the machine learning when  predictions/decisions are automatically used and the algorithm can directly control the flow of the process. This is an requirement on both a technical level as well as on an organizational level. So to gain business value, you have to automate! Otherwise you get stuck with one time improvements or analysis.

<figure>
<center>
  <img src="/images/20170522_direct_impact.png" alt="Direct impact" style="width: 60%;" rel="nofollow"/>
<!--  <figcaption>
  <i> Direct impact
 </i>
 </figcaption> -->
  </center>
</figure>

<br>

#### Data history:

There should historic data about how the old business processes. Otherwise models can not be trained (for non ML people: training  describes the process of developing a ML system). So if you do not track old business processes, you have to start collecting data before you develop your AI application.

<figure>
<center>
  <img src="/images/20170522_data_base.png" alt="Data history" style="width: 10%;" rel="nofollow"/>
<!--  <figcaption>
  <i> Data history
 </i>
 </figcaption> -->
  </center>
</figure>

<br>

#### Evidence:

There should be input that can be internally linked to the optimal decision.
This can only be checked by analyzing the data. For example in a predictive Maintenance case, it could be that 80% of all failures are not predictable and occur spontaneous. In such a case,  the machine learning techniques cannot be used to optimize the service routing like in example 3. Also, it could be that very related business cases are behaving totally differently. E.g. in the case of a replenishment system as in 1., it could be that one can anticipate the demand on a week bases but not on a day base.
You can often only check this condition by looking at the data and doing experiments.

<figure>
<center>
  <img src="/images/20170522_evidence.png" alt="Evidence" style="width: 30%;" rel="nofollow"/>
<!--  <figcaption>
  <i> Evidence
 </i>
 </figcaption> -->
  </center>
</figure>

<br>

So, checking those five conditions will give you an basic understanding if your business process can be enhanced by ML techniques.
If one of those is not fulfilled, this is probably a real showstopper for AI techniques.

---

<br>

### Of course there is more

Of course, beyond those five checkpoints, there is a huge range of other success factors that determine if AI will generate value for you.
For example, you will need change management to accompany the AI revolution, the algorithms will need a platform and infrastructure to run, and so on.

Also, keep it mind that

*"optimizing a failing process make you only fail harder“.*
{: style="text-align: center"}

so if you are still in the business of renting VHS or DVDs, I am sorry, no algorithm will help you. If your business model is seriously flawed, no data or algorithm can save you.


So, what do you think about those five aspects? Did I miss a key point? 
