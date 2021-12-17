# Modeling Speaker Networks: A relational graph from Quotebank

Team DADA
Authors : 
- [Benchelabi, Salim](salim.benchelabi@epfl.ch)
- [Emam, Ahmed](ahmed.emam@epfl.ch)
- [Guirardel, Lucas](lucas.guirardel@epfl.ch)
- [Marie, Geoffray ](geoffray.marie@epfl.ch)

## Abstract

An integral part of any news reporting is the use of quotes of people of interest. Quotes do not exist in isolation and therefore have underlying connection markers.  Quotes from different speakers are often grouped together, and some speakers refer to other speakers. What insights can these connections bring to us ?
This project aims to explore the relationships between people quoted in the Quotebank dataset. Visualizing these relationships can give us an understanding of the networks and communities that are behind quotes, such as professional domains and fields of expertise, political orientation, and even like-mindedness. It’s a common human behavior to surround oneself with like-minded people, who reinforce one’s views. Is it possible to visualize these information bubbles ? And is it possible to create a meaningful network based on speakers and their unknown communities ?

## Research Questions 

More specifically, the aim of this project is to investigate the following research questions: 

1. **What are the communities present amongst quoted speakers?**
	We expect to observe communities matching to political parties as well as other areas of expertise and/or occupations: cinema, sports and sciences to name a few.


    
2. **How do influential events dictate how groups of people are quoted together?**
	Here we will investigate how diversity of the communities and associated parameters mentioned above changed before and after the 2016 US Election, and during the COVID pandemic. 
	Are communities from opposite parties linked more during election season?
    Are scientists and politicians quoted together more often now than pre-pandemic? 
3. **Do speakers primarily mention or quote others who they agree with ?**
	Human behavior dictates that we associate ourselves with people we generally agree with, is this the case? Can we classify one’s neutrality by the polarity of their statements or who they quote?
    




## Additional datasets

The provided Wikidata metadata will be used to complete the Quotebank dataset.

## Methods

### Approach

To create the necessary networks to address the research questions outlined above, two types of relations between quotes will be analyzed: 

1. Quotes grouped in the same news article (Co-quotation relation)
2. Quotes of speakers referring to other speakers (Reference relation)

Once the networks are created and refined, we will investigate the influence of the attribution markers mentioned (political orientation, occupations...) to visualize the communities behind the quotes. The networks will also help us characterize the extent of speakers’ impartiality and their “bubble” when it comes to information and views. 

### Data Processing

There is uncertainty with the attribution of speakers to quotes by *Quobert*. This is characterized by the *probas* parameter. A specific *probas* cutoff will be chosen to filter the data.
<!-- along with any errors found in the data as those listed below for example. -->

#### Website filtering

Several quotes from the same given domain refer to the same page. Some quotes also contain many links leading to the same domain, where the corresponding news pages no longer exist or have nothing to do with the quote.

### Graph building

We want to study networks of relationships between speakers, and the communities they form. For that purpose, we will generate a graph with the speakers as nodes, and a certain relationship between speakers as edges, culminating into a large network.

#### Co-quotation relation

The first way to establish a relation between two speakers is to count articles where they are quoted together. 
<!-- If this results in multimodal data we will then investigate the relationship of quotes in the same article through the lens of the group they pertain to: political party, occupation and so on.  -->

#### Reference relation

Another way to examine the relationship between speakers is to search for occurrences of one speaker referencing another one. For example, when Bernie Sanders says "*To defeat Donald Trump, who will be a very formidable opponent for a number of reasons, we need to have the largest voter turnout in American history.*", we have a link from Bernie Sander to Donald Trump. 

##### Named Entity Recognition

To extract the references to other speakers from quotes, we can use natural language processing tools such as `spaCy`. `spaCy` can perform Named Entity Recognition, and in particular locate the name of a person in a sentence.

##### Sentiment analysis

Using the python library `TextBlob`, we can identify the polarity of a statement. 
We can apply this tool to identify whether quotations are positive or negative. This way, we can identify subgraphs of positive or negative quotations.

### Clustering

To identify clusters of speakers in our network we will use DBSCAN, as it's agnostic w.r.t the number of clusters. These clusters will aid in the visualizations of the communities associated with speakers.

## Proposed timeline

* 19/11 : Finishing data analysis and preprocessing, building the network graphs.
* 26/11 : Graph analysis : clustering, correlations with speakers' properties, and identification of communities. 
* 03/12 : Graph analysis : studying evolution over time. 
* 10/12 : Plotting, website programming.
* 17/12 : Completing story and website polishing.


## Team organization

Eventually, team tasks were split according to the following:

* Geoffray: Data analysis, Data filtering, Graph 3D structure, Data story
* Salim: Data processing, Graph Analysis, Data story
* Lucas: Graph building, Graph 3D vizualisation
* Ahmed: Jekyll website, Datastory, Graph 3D vizualisation

## Data Story

Our data story can be find at the following link: https://aemam022.github.io/
We strongly encourage you to play with the graph ! You can look at the structure and at the nodes, move nodes, change the attribute to color...
We hope you enjoy our data story.


