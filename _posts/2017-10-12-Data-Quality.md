---
layout: post
title:  "Data Quality"
date:   2017-10-12
desc: "Data Quality"
keywords: "data quality"
categories: [Data_Quality]
tags: [Data_Quality, ETL, Data_Integration]
icon: fa-database
---

## What Data Quality is?
Data quality is one of the most severe data criteria, even though its definition may defer and vary from a source to another, but It has been always considered as a high-quality Data when it fits what it’s intended to be used for in terms of making decisions, operations, and planning.
Here’s how [Wikipedia](https://en.wikipedia.org/wiki/Data_quality "Wikipedia") defines Data Quality:
```Data is deemed of high quality if it correctly represents the real-world construct to which it refers.```

The most commonly asked questions when users get in touch with real-world data may be: Where does the data come from? Or, how precise it is? And, What confidence in the sources?

## Origin quality problems
-	Re-designing of SI from already existing systems, which leads to the homogenization of heterogeneous data regardless of the cost of data transfer, modification and apps re-development.

-	Partitioning the SI of different departments from the same organization, it may cause the multiplication of the procedures and the costs of maintaining data quality.

-	Merging SI systems, this latter may lead to enormous consequences such as type incompatibility, constraints contradictions, values incoherence…etc.

Common error types:
There are two types of errors: schema and semantic conflicts.

-	Incomplete data: Absence of attributes, values (null) and records.

-	Incorrect data: isolated values, typing mistakes, codification error...etc.

-	False data information: records that don't match values, contradictory values.

-	Incomprehensive data information.

-	Duplicates.

-	Constraints conflicts.

- etc

Now that we have talked about the common problems that may cause data heterogeneity, let's jump now and talk about the factors and the dimensions that allow us to judge, and let say whether out data is clean enough or not, in other words, is our data in an appropriate quality to work on and to make sensible business decisions or not?

## Quality factors
1. Data Consistency: Data consistency refers to whether the types of data align with the expected versions of the data that should be coming in.

2. Data Accuracy: Data accuracy refers to whether the collected data is correct, and accurately represents what it should.

3. Data Validity: Validity of data is determined by whether the data measure that which it is intended to measure.

4. Data Timeliness: Data timeliness refers to the expectation of when data should be received in order for the information to be used effectively. The expectation and reality often do not align, leading to ineffective use of the data and a lack of data-driven decisions.

## Real World Example

Let's have a real-world example so that we see the problem from a conquer perspective, so for this, we will work with datasets from the official open sourced [data of France gouvernement](https://www.data.gouv.fr/fr/datasets/ "data.gouv.fr").

Say we have 3 different data resources:
1. [The counting of upbound passengers in Transilien trains in 2016](https://www.data.gouv.fr/fr/datasets/comptage-des-voyageurs-montants-dans-les-trains-transilien-1/).

2. [Rail stations of all types, whether or not operated](https://www.data.gouv.fr/fr/datasets/gares-ferroviaires-de-tous-types-exploitees-ou-non-idf/).

3. [Communes of the Ile-de-France Region](https://www.data.gouv.fr/fr/datasets/les-communes/).

And for this, we aim to calculate the total number of passengers in Transilien trains in Ile-de-France region by:
- Departement, city, and municipality.

- Station and train line.

- Date, day and hourly range.

Here's a simple from the datasets :

{% include image.html url="home/static/assets/img/blog/2017-10-12-Data-Quality/blog_post_1_pic3.png" description="Figure1. Communes of the Ile-de-France Region." %}

{% include image.html url="/home/static/assets/img/blog/2017-10-12-Data-Quality/blog_post_1_pic1.png" description="Figure2. The counting of upbound passengers in Transilien trains in 2016." %}

{% include image.html url="static/assets/img/blog/2017-10-12-Data-Quality/blog_post_1_pic2.png" description="Figure3. Rail stations of all types, whether or not operated." %}

{% include image.html url="assets/img/blog/2017-10-12-Data-Quality/blog_post_1_pic2.png" description="Figure3. Rail stations of all types, whether or not operated. assets" %}

## Identifying problems
For a very simple case, say that we have this dataset in one data form (Relational Tables) and we want to join them in this way (*not using the right syntax*)

```JOIN Figure1 ON Figure1.INSEE=Figure3.cp ``` and ``` JOIN Figure2 ON Figure2.Nomgare=Figure3.nom```

Before doing so, we have to make some changes on our tables to prevent any of the problems listed above, for instance :

- Encode `nom` in UTF-8.

- Reformate spaces in `Nom gare` to have ' - ' instead.

- Replace `Empty(NULL)` values in `Montants` by 0.

- Eliminate redundancies in `nom`.

- Transform `INSEE_code` to `ZipCode` format.

So as you can notice, data integration is a very complicated set of processes, I didn't go so far on it so that you get a little idea of how it looks like when working on integrating enormous heterogeneous multiple sources of data.

So here we stop for this post, in the next one of ETL blog series, I'll introduce you the different tools used in real-world data integration scenarios.
