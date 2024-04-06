---
title: Social Network Analysis
handle: network_analysis
icon: diagram-3
layout: service
post_image: /melt_shared_web_res/images/page_images/social_network.png
header_image: /melt_shared_web_res/images/headers/bees.jpg
blurb: "Find out the best way to reach your customers by understanding the flow of information through a social network."
linked_services: [information_extraction, customer_segmentation, recommender_systems, data_visualisation]
clients: [hope_not_hate]
status: published
display_score: S06
---

#### What is social network analysis?

Social network analysis is about modelling the relationships between people in a social network in order to understand how information flows through the network. We might find, for example, that two different groups of people are connected by just one person and therefore that person is extremely important when it comes to spreading a message. 

The analysis is made even more powerful when we label the relationships between people. We can then see who is connected to who *and in what way*.

#### Why would you need it?

Social network analysis is useful whenever your aim is either to get a message out there or to stop disinformation or harmful messages from spreading. 

#### How does it work?

Social network analysis works by representing individuals as points (nodes). These points are are connected to each other by lines (edges), which in turn represent the relationships between the individuals. The resulting structure is known in mathematics as a [graph](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)). We also typically use [Information Extraction](/services/information_extraction) to pull out useful data from text and images that we can then attach to the individuals and the relationships. For example if the relationship involved a conversation on twitter we might label the relationship with the topic of conversation.

Once we have loaded your social data into a [graph database](https://neo4j.com/developer/graph-database/) we can then use algorithms to answer questions like 
-   Who is connected to who and in what way?
-   Which users are most influential in that they are 
	-   The most active?
	-   The most connected to other users?
	-   Acting as bridges between disparate groups?
-    Are there clusters of users (cliques) who are connected mainly to each other?

This analysis works best when we use [Data Visualisation](/services/data_visualisation) to visually display the networks and highlight the patterns.


