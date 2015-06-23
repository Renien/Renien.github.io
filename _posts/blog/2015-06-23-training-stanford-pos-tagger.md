---
layout: post
title: "Training Stanford Part-of-Speech (POS) Tagger"
description: "Training POS Tagger"
category: blog
tags: [NLP, POS-tagger]
image:
  feature: cover/nlp-words.png
  credit:
  creditlink:
comments: true
share: true
---

In Natural Language Process (NLP), POS-tagger is an essential process, which helps to understand the Natural Language queries for computer. In abstract an implemented model is trained with tags, linguistic corpus and generates trained tagger model.

The Stanford POS-tagger is one of the most popular tagger. It’s been developed, optimized and pruned for more than 10 years.  The POS-tagger can be downloaded from this following site: [**nlp.stanford.edu**](http://nlp.stanford.edu/software/tagger.shtml){:target="_blank"}


Stanford is matured framework where it allows to train the models with our own corpus.

To train a model, navigate to Stanford POS-tagger package, which you downloaded.  The **standford-postagger.jar** is instructed using a PROPS file. First generate the property file which includes the template:

{% highlight bash %}
java -mx1g -classpath stanford-postagger.jar edu.stanford.nlp.tagger.maxent.MaxentTagger -genprops
{% endhighlight %}

This will generate the default property file with all the details as comments. You can modify the default option or use the default option to train the models.

These are the modification I have done to my default property file:

{% highlight bash %}
model = models/retail_queries.model 
arch = generic,suffix(4),prefix(4),unicodeshapes(-1,1),unicodeshapeconjunction(-1,1),words(-2,-2),words(2,2) 
trainFile = models/retail_queries.train 
tagSeparator = _ 
encoding = utf-8 
iterations = 100 
openClassTags = A Adv ET NC NP V 
tokenize = false
{% endhighlight %}

Training Data set for a specific domain (Eg: Retail Domain)

{% highlight bash %}
I_PRP want_VBP a_DT birthday_NN present_JJ for_IN seven_CD year_NN old_JJ ._.
I_PRP want_VBP flip-flops_NNS from_IN nike_JJ with_IN five_CD star_NN rating_NN ._.
I_PRP want_VBP a_DT queen_NN bed_NN sheet_NN which_WDT has_VBZ stripes_NNS ._.
I_PRP want_VBP Bedding_NN Protection_NN Kit_NN ._.
I_PRP want_VBP Reebok_NNP Tennis_NN Polo_NNP ._.
I_PRP want_VBP a_DT red_JJ tie_NN with_IN stripes_NNS ._.
I_PRP want_VBP a_DT gents_NNS wristwatch_NN ._.
I_PRP want_VBP Curvy_JJ Fit_NN Straight-Leg_NNP Trouser_NNP Pants_NNPS ._.
i_LS want_VBP dresses_NNS for_IN toddlers_NNS ._.
i_FW need_VBP to_TO purchase_VB different_JJ pattern_NN in_IN hand-towel_NN ._.
I_PRP want_VBP Coffee_NNP table_NN and_CC mug_NN ._.
I_PRP need_VBP gold_NN watches_NNS ._.
polo_NN men_NNS blue_JJ Squares_NNS shirt_NN medium_NN ._.
nike_JJ sport_NN small_JJ shoes_NNS price_NN ._.
polo_NN men_NNS blue_JJ stipes_NNS shirt_NN medium_NN ._.
polo_NN men_NNS blue_JJ Circle_NNP &_CC Dots_NNP shirt_NN ._.
Square_NN pattern_NN Washcloths_NNS ._.
Blue_JJ mens_NNS shirt_NN ._.
red_JJ men_NNS flip_VBP flop_NN ._.
Black_JJ mens_NNS sandals_NNS ._.
{% endhighlight %}

To train the tagger, use the following command:

{% highlight bash %}
java -mx1g -classpath stanford-postagger.jar edu.stanford.nlp.tagger.maxent.MaxentTagger -props models/retail_queries.props
{% endhighlight %}