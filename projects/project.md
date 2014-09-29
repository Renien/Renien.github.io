---
layout: page
permalink: /projects/
title:
description: "Projects"
modified: 2013-09-11
tags: []
image:
  feature:
  credit:
  creditlink:
---

<link rel="stylesheet" href="{{ site.url }}/assets/css/content.extend.css">

<!-- <link rel="stylesheet" href="{{ site.url }}/assets/grid-layout/babylongrid-default.css"> -->
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<script src="{{ site.url }}/assets/grid-layout/jquery.babylongrid.min.js"></script>

<div class="container">

	<div id="babylongrid">

		<article class="grid_tile">
		<div class="h3 title">
			Project E-Remote
			<div class="sub-title">
				SMS Based Home and PC Automation System
			</div>
		</div>
		<div class="grid_desc">
			A simple home and PC automation solution to control your home and PC from elsewhere. This solution gives ability to control any home appliances using SMS.
		</div>
		</article>

		<article class="grid_tile">
		<div class="h3 title">
			Project V-Lab
			<div class="sub-title">
				Augmented Reality Science Laboratory
			</div>
		</div>
		<div class="grid_desc">
			An interactive science laboratory using Augmented Reality Technology. Aim of the project is to provide cheap and effective science laboratory solution...<a href="/v-lab/" class="read-more-link">(Read More)</a>
		</div>
		</article>

		<article class="grid_tile">
		<div class="h3 title">
			Project Value Life
			<div class="sub-title">
				An Interactive Web Based First Aid Trainer
			</div>
		</div>
		<div class="grid_desc">
			An interactive web based first aid trainer application which trains users to perform various first aid maneuver using Wii Remote and 3D human avatars...<a href="/value-life/" class="read-more-link">(Read More)</a>
		</div>
		</article>

		<article class="grid_tile">
		<div class="h3 title">
			Build-IT
			<div class="sub-title">
				An Interactive Web Application for 3D Construction & Interior and Exterior Design
			</div>
		</div>
		<div class="grid_desc">
			Build-IT framework is a user friendly 3D visualizer and 3D editor which help to design the users dream building without needless expenses and in a short time period...<a href="/build-it/" class="read-more-link">(Read More)</a>
		</div>
		</article>
	</div>

	<!-- <div id="babylongrid2">

		<article class="grid_tile">
		<div class="h3 title">
			Project E-Remote
			<div class="sub-title">
				SMS Based Home and PC Automation System
			</div>
		</div>
		<div class="grid_desc">
			A simple home and PC automation solution to control your home and PC from elsewhere. This solution gives ability to control any home appliances using SMS.
		</div>
		</article>

		<article class="grid_tile">
		<div class="h3 title">
			Project V-Lab
			<div class="sub-title">
				Augmented Reality Science Laboratory
			</div>
		</div>
		<div class="grid_desc">
			An interactive science laboratory using Augmented Reality Technology. Aim of the project is to provide cheap and effective science laboratory solution...<a href="/v-lab/" class="read-more-link">(Read More)</a>
		</div>
		</article>

		<article class="grid_tile">
		<div class="h3 title">
			Project Value Life
			<div class="sub-title">
				An Interactive Web Based First Aid Trainer
			</div>
		</div>
		<div class="grid_desc">
			An interactive web based first aid trainer application which trains users to perform various first aid maneuver using Wii Remote and 3D human avatars...<a href="/value-life/" class="read-more-link">(Read More)</a>
		</div>
		</article>

		<article class="grid_tile">
		<div class="h3 title">
			Build-IT
			<div class="sub-title">
				An Interactive Web Application for 3D Construction & Interior and Exterior Design
			</div>
		</div>
		<div class="grid_desc">
			Build-IT framework is a user friendly 3D visualizer and 3D editor which help to design the users dream building without needless expenses and in a short time period...<a href="/build-it/" class="read-more-link">(Read More)</a>
		</div>
		</article>
	</div> -->
</div>



<script>
	(function($){

		$('#babylongrid').babylongrid({
			scheme: [
				{
					minWidth: 960,
					columns: 3
				},
				{
					minWidth: 500,
					columns: 2
				},
				{
					minWidth: 0,
					columns: 1
				}
			]
		});


	}(jQuery));

</script>
