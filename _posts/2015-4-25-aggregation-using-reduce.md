---
layout: post
title:  "Aggregation using reduce"
date:   2015-04-25 23:34:52
categories: javascript
---

Aggregate only certain fields in a javascript array. Aggregating 'a' in array [{a:1, b:2}, {a:5, c:2}] should yield { a: 6 }

##### Code
{% highlight javascript %}
function getAggregation(dataArray, aggregationObject){
			dataArray.reduce(function(a, b){
			 _.forOwn(a, function(value, key) {
				  b[key] && (a[key] = value + b[key]);
				});
			 return a;
			}, aggregationObject);

			return aggregationObject;
		};
{% endhighlight %}

##### Tests
{% highlight javascript %}
getAggregation([{a:1, b:2}, {a:5, c:2}], { a:0 });
getAggregation([{a:1, b:2}, {a:5, c:2}], { c:0, b:0 });
{% endhighlight %}