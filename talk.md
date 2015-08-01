---
layout: page
permalink: /talk/
title: Talks
description: "I love to talk tech"
modified: 2013-09-11
tags: []
---

[**ISMS 2014 Conference - Kuala Lumpur, Malaysia**](http://ijssst.info/Vol-15/No-3/start.pdf){:target="_blank"} 

<div class="publication-header-conference">3D Reconstruction, Interior and Exterior Design</div>
<div>January 2014</div>
<div class="publication-header"></div>
<div class="read-more-content">
<p> 
<figure class="third">
	{% for item in (1..11) %}
	<a href="{{ site.url }}/images/publication/{{ item }}.jpg"><img src="{{ site.url }}/images/publication/{{ item }}.jpg" alt="image"></a>
	{% endfor %}
	<figcaption>Fifth International conference on
Intelligent Systems, Modelling and Simulation <a href="http://isms2014.info/" target="_blank">(http://isms2014.info/)</a> 

Langkawi, Malaysia, 27 – 29 January 2014
Sheraton Hotel, Langkawi, Malaysia</figcaption>
</figure>

</P>
</div>
<div markdown="0" class="read-more-toggle" align="right"><a class="btn">v More</a></div>

[**Angular js Fundamentals**](http://www.slideshare.net/Renien/angular-js-fundamentals-51158673){:target="_blank"}

<div class="publication-header-conference">HTML5 and JavaScript</div>
<div>June 2014</div>

<div markdown="1" class="read-more-content">
Angular JS talk was conducted in [**Zone24x7 (Private) Limited**](http://www.zone24x7.com/){:target="_blank"} (460, Nawala Road,Koswatte, Sri Lanka).
With my colleague [**Malinda Prasad**](https://twitter.com/malindaprasad){:target="_blank"} we had interactive session to expose about SPA and Angular JS framework. 
During the session we did a code walk-through to explain all the key features of Angular JS framework.
<br><br>Sample Code :- [https://github.com/Renien/angularjs-fundamentals-demo](https://github.com/Renien/angularjs-fundamentals-demo){:target="_blank"}

<figure class="half">
    {% for item in (1..2) %}
    <a href="{{ site.url }}/images/talk/angularjs-fundamental/{{ item }}.jpg">
            <img src="{{ site.url }}/images/talk/angularjs-fundamental/{{ item }}.jpg" alt="image">
            </a>
    {% endfor %}
	<figcaption>Before the session 19 June 2014</figcaption>
</figure> 
</div>

<div markdown="0" class="read-more-toggle" align="right"><a class="btn">v More</a></div>

[**Introduction - Augmented Reality**](http://www.slideshare.net/Renien/introduction-augmented-reality-51158369){:target="_blank"}

<div class="publication-header-conference">Augmented Reality</div>
<div>July 2015</div>

<div markdown="1" class="read-more-content">
[**Society of Computer Science**](https://www.facebook.com/scs.usjp){:target="_blank"}, [**University of Sri Jayewardenepura**](http://www.sjp.ac.lk/){:target="_blank"} organized [**Aurora 2K15**](https://www.facebook.com/aurora.usjp){:target="_blank"}. A computing conference aimed at introducing IT careers to school students and helps improve their IT skills as well.

The Conference was featured with variety of speakers and I was glad to meet and talk about Augmented Reality to younger crowd. 

After presentation we had interactive demo session with Augmented Reality toys and my colleague [**Michael Lu**](https://twitter.com/mikelu51){:target="_blank"} helped me throughout the presentation.

<figure class="half">
    {% for item in (1..6) %}
    <a href="{{ site.url }}/images/talk/augmented-reality/{{ item }}.jpg">
            <img src="{{ site.url }}/images/talk/augmented-reality/{{ item }}.jpg" alt="image">
            </a>
    {% endfor %}
	<figcaption>During the session 28 July 2015</figcaption>
</figure> 
</div>

<div markdown="0" class="read-more-toggle" align="right"><a class="btn">v More</a></div>

<style type="text/css">
.read-more-toggle .btn{
	padding: 3px;
	font-size: 12px;
}

.hide {
  display: none;
}

</style>
<script src="{{ site.url }}/assets/js/vendor/jquery-1.9.1.min.js"></script>
<script type="text/javascript">
// Hide the extra content initially, using JS so that if JS is disabled, no problemo.
$('.read-more-content').addClass('hide');

// Set up the toggle.
$('.read-more-toggle').on('click', function() {

    $('.read-more-toggle').html("<a class='btn'>v More</a>");

	if(!$(this).prev('.read-more-content').is(":visible")){
		$('.read-more-content').addClass('hide');
        $(this).html("<a class='btn'>^ Less</a>");
	}
   
   $(this).prev('.read-more-content').toggleClass('hide');

   $('html, body').animate({
    	scrollTop: $(this).prev('.read-more-content').offset().top
	}, 2000);
});
</script>