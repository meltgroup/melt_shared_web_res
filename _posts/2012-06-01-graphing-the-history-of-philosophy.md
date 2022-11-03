---
layout: post
title:  Graphing the history of philosophy
date:   2020-05-02 09:16:35 +0600
categories: [jekyll]
post_image: "/assets/images/posts/classical.png"
author: Simon
redirect_from:
  - /2012/06
---

This one came about because I was searching for a data set on horror films (don't ask) and ended up with one describing the links between philosophers.

To cut a long story very short I've extracted the information in the <em>influenced by</em> section for every philosopher on Wikipedia and used it to construct a network which I've then visualised using <a href="http://gephi.org/" target="_blank">gephi</a>

It's an easy process to repeat. It could be done for any area within Wikipedia where the information forms a network. I chose philosophy because firstly the influences section is very well maintained and secondly I know a little bit about it. At the bottom of this post I've described how I got there.

First I'll show why I think it's worked as a visualisation. Here's the whole graph.

<a href="/assets/images/posts/philPrettyV4.png"><img title="philPrettyV4" src="/assets/images/posts/philPrettyV4.png" alt="" width="100%" /></a>

Each philosopher is a node in the network and the lines between them (or edges in the terminology of graph theory) represents lines of influence. The node and text are sized according to the number of connections (both in and out). The algorithm that visualises the graph also tends to put the better connected nodes in the centre of the diagram so we see the most influential philosophers, in large text, clustered in the centre. It all seems about right with the major figures in the western philosophical tradition taking the centre stage. (I need to also add the direction of influence with a arrow head - something I've not got round to yet.) A shortcoming however is that this evaluation only takes into account direct lines of influence. Indirect influence via another person in the network does not enter into it. This probably explains why Descartes is smaller than you'd think. It would also be better if the nodes were sized only by the number of outward connections although I think overall the differences would be slight. I'll get round to that.

It gets more interesting when we use Gephi to identify communities (or modules) within the network. Roughly speaking it identifies groups of nodes which are more connected with each other than with nodes in other groups. Philosophy has many traditions and schools so a good test would be whether the algorithm picks them out.

It has been fairly successful. Below we can see the so called continental tradition picked out in green, stemming from Hegel and Nietzsche, leading into Heidegger and Sartre and ending in the isms of the twentieth century. It's interesting that there is separate subgroup, in purple, influenced mainly by Schopenhauer (out of shot) and Freud.

<img class="size-full wp-image-620" title="Continental" src="/assets/images/posts/continental1.png" alt="" width="100%"/>

And this close up is of the analytical tradition emerging out of Frege, Russell and Wittgenstein. At the top and to the left you can see the British empirical school and the American pragmatists.

<img title="analytical" src="/assets/images/posts/analytical.png" alt="" width="100%"/>


It would be interesting to play with the number of groups picked out by the algorithm. It would hopefully identify sub groups within these overarching traditions.

The graph is probably most insightful when you zoom in close. Gephi produces a vector graphic output so if you're interested you can download it <a href="https://github.com/coppeliaMLA/graphingPhilosophy" target="_blank">here</a> and explore it yourself.

Now for how you do it.

The first stop is <a href="http://dbpedia.org" target="_blank">dbpedia</a>. This is a fantastic resource which stores structured information extracted from wikepdia in a database that accessible through the web. Among other things it stores all of the information you see in an infobox on a Wikipedia page. For example I was after the influenced and influenced by fields that you find on the infobox on the page for <a href="http://en.wikipedia.org/wiki/Plato" target="_blank">Plato</a>.

The next step is to extract this information. For this we need two things: a SPARQL endpoint (try <a href="http://dbpedia.org/snorql/">snorql</a>), which is an online interface to submit our queries and little knowledge of <a href="http://en.wikipedia.org/wiki/SPARQL">SPARQL</a> a specialist language for querying the semantic web. This is a big (and exciting) area that has to do with querying information that is structured in triples (subject-relationship-object). I assume it has its roots in predicate logic so the analytical philosophers would have been pleased. However the downside is that the language itself a lot more difficult to learn than say SQL and to complicate things still further you need to know the ontological structure of the resource you are querying. I probably wouldn't have got anywhere at all were it not for a great <a href="http://www.snee.com/bobdc.blog/2007/11/querying-dbpedia.html">blog post</a> by Bob DuCharme which is a simple guide for getting the information out of wikipedia.

In the end the query I needed was very simple. You can test it by submitting it in <a href="http://dbpedia.org/snorql/">snorql</a>.

<pre><code>
SELECT *
WHERE {
?p a &lt;http://dbpedia.org/ontology/Philosopher&gt; .
?p &lt;http://dbpedia.org/ontology/influenced&gt; ?influenced.
}
</code></pre>

It then needed a bit of cleaning as the punctuation was coded for URLS. For this I used the following online <a href="http://meyerweb.com/eric/tools/dencoder/">URL decoder</a>.

After a bit more simple manipulation in excel I had a finished csv file that consisted of three columns
<code>
Philosopher A
Philosopher B
Weight
</code>

Each row in the data set represented a line of influence from philosopher A to philosopher B. The weight column contained a dummy entry of 1 because in our graph we do not want any one link to matter more than any other.

<a href="http://gephi.org/">Gephi </a>is the tool I used to create the visualisation of the graph. It's both fantastic and open source. You can download it and set it up in minutes. For a quick tutorial see this <a href="https://gephi.org/users/quick-start/">link</a>. There are many settings you can use to change the way your graph looks. I used a combination of the force atlas and the <a href="http://en.wikipedia.org/wiki/Force-based_algorithms_(graph_drawing)">fruchterman-reingold</a> layout algorithms. I then scaled text and node size by node degree (number of connections) and suppressed all nodes with less than four connections (it was overwhelming otherwise). The partition tool is used to create the communities. Full instructions are in the tutorial. I also found this <a href="http://www.mkbergman.com/968/a-new-best-friend-gephi-for-large-scale-networks/">blog entry</a> very useful as a guide.

I hope that helps anyone who is trying to do something similar. If anyone does has a data set on horror films tagged with keywords please let me know!

Simon

<strong>Update</strong> Griff at <a href="http://griffsgraphs.wordpress.com/2012/07/03/graphing-every-idea-in-history" target="_blank">Griff's graphs</a> has used the instructions above to create a fantastic visualization of the influence network of everyone on Wikipedia. It's well worth a look.

<a href="http://creativecommons.org/licenses/by-nc-sa/3.0/" rel="license"><img style="border-width:0;" src="http://i.creativecommons.org/l/by-nc-sa/3.0/80x15.png" alt="Creative Commons Licence" /></a>
Graphing the history of philosophy by <a href="http://drunks-and-lampposts.com/" rel="cc:attributionURL">Simon Raper</a> is licensed under a <a href="http://creativecommons.org/licenses/by-nc-sa/3.0/" rel="license">Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License</a>.
Based on a work at <a href="http://drunksandlampposts.files.wordpress.com/2012/06/philprettyv4.png" rel="dct:source">drunksandlampposts.files.wordpress.com</a>.
Permissions beyond the scope of this license may be available at <a href="http://drunks-and-lampposts.com/" rel="cc:morePermissions">http://drunks-and-lampposts.com/</a>.
