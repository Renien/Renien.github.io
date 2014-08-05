---
layout: post
title: "Collision Detection using Custom Bounding Rectangle/Box"
description: "Detect the 2D collision using javascript"
category: articles
tags: [javascript, 2D]
image:
  feature: 
  credit: 
  creditlink: 
comments: true
share: true
---

While working on the client project I came cross to implement a module using kineticjs framework. In this module the users can draw multiple points polygon shapes. In each drawings and changes on the polygon the shapes need to be sorted according to the ascending order of the shape areas. Since it deals with many polygon shapes it required to implement an algorithm to faster the ordering or position of the Z index in 2D perspective view.

To solve this problem:

* After each update of polygon shapes retrieve all the shapes form the drawing canvas.
* Then calculate the min and max vertex points of each polygon. So basically it’s like you will get to point where we can draw 	  virtual rectangle or box shape.
* After calculating the min and max vales of each polygon check for the shape collision. In simple term check for each min and   max points of shape is intersecting with other shape min and max points. Here you can find a simple code for virtual collision detection for multiple point shapes.

{% highlight javascript %}
function shape_Colliding(rec1X, rec1Y, rec1Width, rec1Height,
 rec2X, rec2Y, rec2Width, rec2Height) {
 
 var status = false;
 var rec1Top = rec1Y;
 var rec1Bottom = rec1Height;
 var rec1Left = rec1X;
 var rec1Right = rec1Width;
 var rec2Top = rec2Y;
 var rec2Bottom = rec2Height;
 var rec2Left = rec2X;
 var rec2Right = rec2Width;
 
//Check for the bounding box collsion
 
if (!(rec1Bottom < rec2Top ||
 rec1Top > rec2Bottom ||
 rec1Left > rec2Right ||
 rec1Right < rec2Left))
 status = true;
 
return status;
}
{% endhighlight %}

Once you have detected the collision/Shapes are overlapping each other then only need is to calculate areas of each colliding shapes. This will help to reduce the computational time and faster the process.

The below code is to calculate the area of multiple point shape polygon.

{% highlight javascript %}
/*
# Area of any shape is calculated using 'polygon_Area'
method. Using this method it will return the area of
shape in the canvas.
Note :- This works only for clock wise pin points.
This whole anchor was implement initially with
pin pointing the points as clock wise. So this
method works perfectly.
This function has been add to sort the area of the polygon
and set the Z index of the canvas
Renien (21/8/2013)
*/
 
function polygon_Area(x, y, numPoints) {
 
var area = 0; // Accumulates area in the loop
 var j = numPoints - 1; // The last vertex is the 'previous' one to the first
 
 for (var i = 0; i < numPoints; i++) {
 area = area + (x[j] + x[i]) * (y[j] - y[i]);
 j = i; //j is previous vertex to i
 }
 
return area / 2;
}
{% endhighlight %}

Now that’s all. According the areas size sort the Z index position in ascending order.

Note that since it is dealing with multiple shapes it is must this logic need to be run as a recursive function so until it get sorted and match with all the shapes.

Happy Coding  :)
