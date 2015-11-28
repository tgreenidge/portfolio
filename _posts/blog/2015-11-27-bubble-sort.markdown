---
layout: post
title:  "Bubble Sort Algorithm"
date:   2015-11-27 19:28:51
categories: blog
featured: true
comments: true
excerpt: "Bubble Sort Algorithm"
---

Although it is considered the worst sorting algorithm, the bubble sort is an algorithm that is very easy to implement. Let's say we have an array of integer elements. The bubble sort starts at the beginning of the array, compares adjacent elements, and swaps the elements until the largest number moves to the right or the end of the array.

### Recursive

{% highlight javascript %}
var myArray = [-1, 4, -2, 3, 4, 10, 16, 3, 0];

var bubbleSort = function( array, pointer ) {
  var pointer = pointer || array.length - 1 ;
  if (pointer === 1) {
    return array;
  }
  for(var i = 0; i <= pointer; i++) {
    var temp;
    if(array[i] > array[i+1]) {
      temp = array[i];
      array[i] = array[i + 1];
      array[i + 1] = temp;
    }
  }   
  return bubbleSort(array, pointer - 1);  
}

bubbleSort(myArray); 
console.log(myArray); //[ -2, -1, 0, 3, 3, 4, 4, 10, 16 ]
{% endhighlight %}


### Iterative
Remember that all recursive functions may be refactored to iterative functions. In this example,
{% highlight javascript %}
var myArray = [12, 24, 1, 13, 0, 8, 0, -1, -6, 8,  5, 3, 10];

function bubbleSort(array) {
  var length = array.length -1;
  for (var i = 0; i < length; i++) {
    for (var j = 0; j <= length - i; j++) {
      if (array[j + 1] < array[j]) {
        var temp = array[j];
        array[j] = array[j + 1];
        array[j + 1] = temp;
      }
    }
  }
  return array;
}

console.log(bubbleSort(myArray)); //[ -6, -1, 0, 0, 1, 3, 5, 8, 8, 10, 12, 13, 24 ]
{% highlight javascript %}