---
layout: post
title:  "The five conditions to successful boost your business with Machine Learning"
date:   2016-09-05 20:00:00 +0100
categories: Consulting, Business Processes, Machine Learning
comments: True
tldr: Judging if machine learning can enhance your business is hard. I will show five key aspects of business processes that are suitable to be enhanced by Machine Learning.
---

__TLDR: Judging if machine learning can enhance your business is hard. I will show five key aspects of business processes that are suitable to be enhanced by Machine Learning.__

---
<br>


As the buzzwords Big Data, Artificial Intelligence, Machine Learning and Data Science are on everybody lips, I am more and more often approached by friends to discuss the potential of Machine Learning for their line of work. For somebody without Data Science experience it can be hard to judge where Machine Learning or AI techniques can generate business value. So, in the following, I will sketch five characteristics of business processes that are worthy to be enhanced by ML.

### Everything in a business can be expressed as business process

So first of all, what is a business process? According to [wikipedia](https://en.wikipedia.org/wiki/Business_process){:rel="nofollow"} it is

*"A business process or business method is a collection of related, structured activities or tasks that produce a specific service or product (serve a particular goal) for a particular customer or customers.".*

So basically, everything that happens in a business is a business process. When I think about a business process, I visualize a flow chart, similar to this diagram

<figure>
<center>
  <img src="/images/20170514_businessprocess.png" alt="Diagram of a business process" style="width: 60%;"/>
  <figcaption> <i> A business process can be visualized as a flowchart of decisions (*"It may often be visualized as a flowchart of a sequence of activities with interleaving decision points or as a process matrix of a sequence of activities with relevance rules based on data in the process.“.*) </i></figcaption>
  </center>
</figure>

Even though the press sometimes talks about AI taking over all walks of live, I feel that Machine Learning in the near future will be most beneficial to enhance existing business processes. So Machine Learning is not used to automate everything but optimize small aspects. There are some applications like autonomous driving or the google translator app that are disruptive and totally new value chains, but the majority of applications/startups is based on existing business cases. So, how can one find BP that are worthy to be enhanced the holy ML methods?

Actually there are five characteristics such processes have to fulfill. Let us start with some examples.

### Examples for successful applications of ML

If we visualize a business process as a flowcharts of decision, then machine learning should be used to automate one or multiple decisions in that process. Examples are

1.    replenishment systems (how much do I order? => replenishment forecasting systems)

2.    optimization of service routes based on failure predictions (which service worker do I send where, and when? => optimization of service schedules)

3.    identification of spam/fraud (Does this mail contains spam? => spam detection)

4.     personalized marketing (This client that just visited my homepage, for which product do I give discounts to him? => targeting systems)

### The five conditions

Those are all decisions that can be enhanced by ML. So, what do those business cases have in common? They fulfill five important characteristics:

*    **Uncertainty in the optimal decision:** If the business process is already deterministic, then there is no needs to deploy ML to automate it. For example in 1. it is not clear how much the customers will buy while in 3. it is not clear if a mail is spam or not.

*     **Lots of small/micro decisions and not big decisions:** An unfitting example for a ML process would be the decision when to start a global sale. This stands in contrast to lots of small decisions such as which product to put on sale versus. Also you could automate which customers to send marketing material, like in 4. So we need „small“ business processes that are frequently made. So, focus on operational and not strategic decisions.

*    **Direct impact:** Only when the ML predictions/decisions are automatically used and the algorithm can directly control the flow of the process, this is real value generated. This is an requirement on both a technical level as well as on an organizational level. So to gain business value, you have to automate!! Otherwise you get stuck with one time improvements or analysis.

*    **Continuous patterns:** There should historic data about how the old business processes went. Otherwise models can not be trained (for non ML people: training  describes the process of developing a ML system). So if you do not track old business processes, you are done.

* **Evidence:** The input should be internally linked to the optimal decision. This can only be checked by analyzing the data. For example in a predictive Maintenance case, it could be that 80% of all failures are not predictable and occur spontaneous. In such a case ML can not be used to optimize the service routing like in 3. You can often only check this condition by looking at the data. So there should be a meaningful input on which the BP can be optimized. Also, it could be that very related business cases are behaving totally differently. E.g. in the case of a replenishment system, one could predict on a week bases but not on a day base.

So, checking those five conditions will give you an basic understanding if your business process can be enhanced by ML techniques.

### Of course there is more

Of course there is a huge range of success factors like Change Management or Dev OPs that you also have to tackle, however those are topics for future blogposts.

Also,

*"optimizing a failing process make you only fail harder“.*
{: style="text-align: center"}

E.g. if you are still in the business of renting VHS or DVDs, I am sorry, no algorithm will help you. If your business model is seriously flawed, you are done.


So, what do you think about those five aspects? Did I miss a key point?
