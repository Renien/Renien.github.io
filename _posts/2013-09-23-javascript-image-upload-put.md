---
layout: post
title: "Image Upload and Update with PUT API call"
description: "Uploading images using PUT API call"
category: articles
tags: [javascript]
image:
  feature: post/js-cover.jpg
  credit: 
  creditlink: 
comments: true
share: true
---

In Image upload generally we used to send the image data as form data. When we try to upload a file for a POST API call it works perfectly.

But for PUT API call the files are getting uploaded success fully but the data is getting corrupted. We tested API call using Google POSTMAN but the same issue, data is getting corrupted.

Initially I thought under HTML form context both API call (POST and PUT) will do the same job but it is wrong!

I confirmed this by doing simple image upload for PUT API call in .NET And also I try to send the request using Firefox ‘HTTP Requester’ works perfectly.
This happen because .NET and the Fireforx extension push the data as Base64 format where Google POSTMAN send the data as Formdata.

###Solution to this problem in JavaScript 

Using HTML5 File API can easily read as binary data format using ‘readAsBinaryString’ method. But this method seems to be having a problem due to some bug and returns corrupted data.

So the overall work around for this problem is to read the image as ‘readAsDataURL’ and get the image data then basically needed to wrap the raw binary in an arraybuffer and convert the binary chars to Unicode. At last push this data to the server. This works perfectly!

{% highlight javascript %}
dataUri //Image data from readAsDataURL
 
var dataURIComponents = dataUri.split(',');
var mimeString = dataURIComponents[0].split(':')[1].split(';')[0];
var byteString;
 
if (dataURIComponents[0].indexOf('base64') != -1) {
byteString = atob(dataURIComponents[1]);
}
else {
byteString = unescape(dataURIComponents[1]);
}
 
var length = byteString.length;
var arrayBuffer = new window.ArrayBuffer(length);
var unicodeArray = new Uint8Array(arrayBuffer);
 
for (var i = 0; i < length; i++) {
unicodeArray[i] = byteString.charCodeAt(i);
}
 
unicodeArray //’Put’ this data to the server
{% endhighlight %}
