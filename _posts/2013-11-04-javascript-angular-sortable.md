---
layout: post
title: "JQueryUI Accordion Sortable ng:repeat binding"
description: "Effetively as do the sorting with angular."
category: articles
tags: [javascript, angular.js]
image:
  feature: so-simple-sample-image-2.jpg
  credit: Renien Joseph
  creditlink: 
comments: true
share: true
---

I have been trying to figure out solution to work smoothly with angular.js and JQuery UI. In my client project we need to implement sortable component.

But ng:repeat (angular.js) works only one way (top-bottom). So if we change model using JQuery UI – sortable the model will change only in one way (top-bottom) and if we sort from bottom-top our dom component it will get sorted in UI side but the binded values won’t change.

Angular.js chat room provided a solution that to perform this action we need to write our own UI sortable component using angular.js.

But found a work around solution for this and it works perfectly. So it will help us to use JQuery UI Sortable component with Angular.js binding.

Bind the data and bind the scope function with JQuery UI:-

{% highlight html %}
<ul ui-sortable="sortableOptions" ng:model="rawStudy.playlist"/>
{% endhighlight %}

Then call the JQuery UI function and manually change data model and apply the changes to the UI using anglar. It works perfectly without any flaws.

{% highlight javascript %}
$scope.sortableOptions = {
  start: function (e, ui) {
    ui.item.data('start', ui.item.index());
 },
update: function (e, ui) {
   $scope.editForm.$dirty = true;
   var start = ui.item.data('start'),
   end = ui.item.index();
   if(end > start) { 
      $scope.rawStudy.playlist.splice(end, 0, $scope.rawStudy.playlist.splice(start, 1)[0]);   
   }
   $scope.$apply();
 }
};
{% endhighlight %}

So with the one line of code problem solved :)

{% highlight javascript %}
if(end > start)
 $scope.rawStudy.playlist.splice(end, 0, $scope.rawStudy.playlist.splice(start, 1)[0]);
{% endhighlight %}
