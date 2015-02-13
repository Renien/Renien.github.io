---
layout: page
permalink: /publication/
title: Publication
description: "Research based white papers"
modified: 2013-09-11
tags: []
image:
  feature: cover/publication-page.jpg
  credit: 
  creditlink: 
---

[**DREAM – IT – 3D RECONSTRUCTION AND BUILDING INFORMATION MODELLING >>**](http://www.ijeset.com/volume-6-issue-2.html){:target="_blank"} 

<div class="publication-header-conference">International Journal of Engineering Sciences & Emerging Technologies</div>
<div class="publication-date">October 1, 2013</div>
<div class="publication-header"></div>
<div class="read-more-content">
<p>
Throughout the architecture engineering and construction lifecycle, 3D building models are extremely helpful. Such models coupled with virtual walk through can enable customers to decide and be satisfied with their dream building. Manually creating a polygonal 3D model of a set of floor plans is nontrivial and requires skill and time. Additionally, applying concise design principles makes a holistic design in order to create comfortable and cosy living environments. This project introduces and reviews a mechanism for applying design constructs after the conversion of 2D drawings into 3D Building Information Model. This research utilizes and demonstrates an automated 3D model reconstruction of real world object from an un-calibrated image sequence targeting the 
same scene obtained using a common camera; which can be used for interior and exterior design. There are many key techniques in 3D reconstruction from un-calibrated image sequences, including feature matching, fundamental matrix estimation, projective reconstruction, camera self-calibration and Euclidean reconstruction. The effectiveness of the algorithms was evaluated in the experiments with many real image sequences.
</P>
</div>
<div markdown="0" class="read-more-toggle" align="right"><a class="btn">Read More</a></div>



[**BUILD-IT - AN INTERACTIVE WEB APPLICATION FOR 3D CONSTRUCTION, INTERIOR & EXTERIOR DESIGN >>**](http://ijssst.info/Vol-15/No-3/start.pdf){:target="_blank"} 

<div class="publication-header-conference">Fifth International conference on Intelligent Systems, Modelling and Simulation (http://isms2014.info/) [IEEE]</div>
<div>January 26, 2014</div>
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
<div markdown="0" class="read-more-toggle" align="right"><a class="btn">Read More</a></div>

[**SINGLE PAGE APPLICATION AND CANVAS DRAWING >>**](http://arxiv.org/abs/1502.03530){:target="_blank"} 

<div class="publication-header-conference">International Journal of Web & Semantic Technology (IJWesT) Vol.6, No.1, January 2015</div>
<div class="publication-date">January 31, 2015</div>
<div class="publication-header"></div>
<div class="read-more-content">
<p>
Recently, with the impact of AJAX a new way of web development techniques have been emerged. Hence, with the help of this model, single-page web application was introduced which can be updated/replaced independently. Today we have a new challenge of building a powerful single-page application using the currently emerged technologies. Gaining an understanding of navigational model and user interface structure of the source application is the first step to successfully build a single- page application. 

In this paper, it explores not only building powerful single-page application but also Two Dimensional (2D) drawings on images and videos. Moreover, in this research it clearly express the findings on 2D multi-points polygon drawing concepts on client side;  real-time data binding in between drawing module on image , video and view pages.
</P>
</div>
<div markdown="0" class="read-more-toggle" align="right"><a class="btn">Read More</a></div>


<style type="text/css">
/*.read-more-toggle .btn{
	padding: 3px;
	font-size: 12px;
}*/

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
	if(!$(this).prev('.read-more-content').is(":visible")){
		$('.read-more-content').addClass('hide');
	}
   
   $(this).prev('.read-more-content').toggleClass('hide');

   $('html, body').animate({
    	scrollTop: $(this).prev('.read-more-content').offset().top
	}, 2000);
});
</script>