---
layout: post
title: "Image Drag Bound function – kineticjs.com"
description: "Drag the 2D shapes inside the image canvas"
category: articles
tags: [javascript, 2D, kinetic.js]
image:
  feature: post/js-2D-collision.jpg
  credit: 
  creditlink: 
comments: true
share: true
---

To bound the movement of nodes being dragged and dropped inside regions with [**KineticJS**](http://kineticjs.com/){:target="_blank"}, we can use the dragBoundFunc property to define boundaries that the node cannot cross.

But in my client project I need to deal with more complex groups and multiple shapes. While using the dragBoundfuntion I realized there is bug and the main group position is not maintained properly.

So at last thought of writing my own dragbound function and the over view of this work around solution as follows.


<figure>
	<a href="{{ site.url }}/images/post/withinbounds.png"><img src="{{ site.url }}/images/post/withinbounds.png" alt="image" title="Drag bound theoretical picture"></a>
	<figcaption><div style="text-align:center;">Drag bound theoretical picture</div></figcaption>
</figure>

This idea was tested and developed in .NET framework and it works perfectly. So it only a matter of implementing the solution in Java Script. In here a particular shape consist of many multiple shapes such as Circles , Lines and Polygon shapes or rectangle Shapes.

> So what we have to do is extract the min and max position of the whole group shape.

{% highlight javascript %}
//Extarct and get the small and large points coordintes from the point list
var smallPoint = { x: Math.min.apply(Math, pointListX), y: Math.min.apply(Math, pointListY) };
var largePoint = { x: Math.max.apply(Math, pointListX), y: Math.max.apply(Math, pointListY) };
{% endhighlight %}

From the Kinetics dragbound function get the position of the main group and update the correct min and max position of the whole shape group.

{% highlight javascript %}
//Calculate the min and max points of the shape main group position
var minPoint = { x: mainGroup.getAbsolutePosition().x - smallPoint.x, y: mainGroup.getAbsolutePosition().y - smallPoint.y };
var maxPoint = { x: largePoint.x - mainGroup.getAbsolutePosition().x, y: largePoint.y - mainGroup.getAbsolutePosition().y };
{% endhighlight %}

That’s it now we have got the correct absolute position of the main group. Now it’s a matter of blocking the shape movement from the boundary.

{% highlight javascript %}
/* Check for boundray values and
Update the Position of the shape */
var x = pos.x;
var y = pos.y;
if (x &lt; minX) {
x = minX;
}
if (x &gt; maxX) {
x = maxX;
}
if (y &lt; minY) {
y = minY;
}
if (y &gt; maxY) {
y = maxY;
}
return ({
x: x,
y: y
});
{% endhighlight %}

This above logic will check for the condition and will return the correct maingroup position so it will be bound inside a particular boundary.

The below is the overall solution in Java Script – Kinetics.js

{% highlight javascript %}
/*
 This function mainly deals with drag bound limitation
 So basically when a polygon is moved through the canvas
 it will check for min points and max points weather it
 has been jumped from the border
 But this funtion method has bug because of the "Kinetic.js" file
 Renien (26/08/2013)
 */
 function shape_BoundingBox(pos, mainGroup) {
 /* Extract the point group from the main group
 - Then get all the anchor points and identi
 -fy the small and large coordinates in the
 polygon
 */
 var pointGroup = mainGroup.getChildren()[1];
 var anchorPoints = pointGroup.getChildren();
 
//Order all the anchor point list to an array
 var pointListX = [];
 var pointListY = [];
 
 anchorPoints.forEach(function (anchor) {
 pointListX.push(anchor.getAbsolutePosition().x);
 pointListY.push(anchor.getAbsolutePosition().y);
 });
 
//Extarct and get the small and large points coordintes from the point list
 var smallPoint = { x: Math.min.apply(Math, pointListX), y: Math.min.apply(Math, pointListY) };
 var largePoint = { x: Math.max.apply(Math, pointListX), y: Math.max.apply(Math, pointListY) };
 
//Calculate the min and max points of the shape main group position
 var minPoint = { x: mainGroup.getAbsolutePosition().x - smallPoint.x, y: mainGroup.getAbsolutePosition().y - smallPoint.y };
 var maxPoint = { x: largePoint.x - mainGroup.getAbsolutePosition().x, y: largePoint.y - mainGroup.getAbsolutePosition().y };
 
// pre-calc some bounds so dragBoundFunc has less calc's to do
 var minX = stage.getX() + (anchor_Radious * stage.getScale().x) + minPoint.x;
 var minY = stage.getY() + (anchor_Radious * stage.getScale().y) + minPoint.y;
 
//Calclaulte the exact boundary for the polygon
 var maxX = stage.getX() + stage.getWidth() - maxPoint.x - (anchor_Radious * stage.getScale().x);
 var maxY = stage.getY() + stage.getHeight() - maxPoint.y - (anchor_Radious * stage.getScale().y);
 
/* Check for boundray values and
 Update the Position of the shape */
 var x = pos.x;
 var y = pos.y;
 if (x &lt; minX) {
 x = minX;
 }
 if (x &gt; maxX) {
 x = maxX;
 }
 if (y &lt; minY) {
 y = minY;
 }
 if (y &gt; maxY) {
 y = maxY;
 }
 return ({
 x: x,
 y: y
 });
 }
 {% endhighlight %}