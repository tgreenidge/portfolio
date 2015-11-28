---
layout: post
title:  "Bubble Sort Algorithm"
date:   2015-11-27 19:28:51
categories: blog
featured: true
comments: true
excerpt: "Bubble Sort Algorithm"
---

Although it is considered the most inefficient sorting algorithm, the bubble sort is an algorithm that is very easy to implement. Let's say we have an array of integer elements. The bubble sort starts at the beginning of the array, compares adjacent elements, and swaps the elements until the largest number moves to the right or the end of the array. 


### My Logic
Below is the logic that I used to arrive at my solution:

* iterate through the array
  * if left element > right element
    * swap
    (once this iteration is done, the largest value is at end of the array, so
    create a pointer to next largest element, so won't have to go through the entire array)
* Repeat logic until pointer is at first element of the array
* Return array

### Recursive Approach
At first I implemented this algorithm using recursion because of the way I envisioned the problem.

{% highlight javascript %}

var bubbleSort = function ( array, pointer ) {
  var pointer = pointer || array.length - 1 ;
  if (pointer === 1) {
    return array;
  }
  for (var i = 0; i <= pointer; i++) {
    var temp;
    if (array[i] > array[i + 1]) {
      temp = array[i];
      array[i] = array[i + 1];
      array[i + 1] = temp;
    }
  }   
  return bubbleSort(array, pointer - 1);  
}

var myArray = [-1, 4, -2, 3, 4, 10, 16, 3, 0];
console.log(bubbleSort(myArray); ); //[ -2, -1, 0, 3, 3, 4, 4, 10, 16 ]
{% endhighlight %}


### Iterative Approach
Remember that all recursive functions may be refactored to iterative functions. In this example, I simply refactored using a nested loop. I used the inner loop to stop just before the previously sorted element to the right, ignoring all larger elements that have already been sorted to the end of the array.

{% highlight javascript %}

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

var myArray = [12, 24, 1, 13, 0, 8, 0, -1, -6, 8,  5, 3, 10];
console.log(bubbleSort(myArray)); //[ -6, -1, 0, 0, 1, 3, 5, 8, 8, 10, 12, 13, 24 ]
{% endhighlight %}

### A Test Case
I used a 5 element integer array to step through the process of the bubble sort, just so that I can test my solution. 

**Array to Sort**: 
```
[1, -5, -1, 6, 0]
```
**Iteration 1**
* Starting at the first element, we compare to the second. Since 1 is greater that -5, we need to swap them.

{:.centered}
```
[-5, 1, -1, 6, 0]
```

* Then we compare the second element in the array to the third. Since 1 is greater than -1, we need to swap the second and third elements.

{:.centered}
```
[-5, -1, 1, 6, 0]
``` 

* Now we compare the third element in the array to the fourth element. Since 1 is less than 6, we do not swap.

{:.centered}
```
[-5, -1, 1, 6, 0]
```

* We now move to the fourth element of the array and compare it to the fifth element. Since 6 is greater than 0, we need to swap.

{:.centered}
```
[-5, -1, 1, 0, 6]
```

Notice at the end of the first iteration the largest number in the array moves all the way to the right. This is now the bubble sort works - it sorts by moving the largest numbers to the right on each iteration.

We then repeat this process again until the array is sorted. 

**Iteration 2**

* We start with:

{:.centered}
```[-5, -1, 1, 0, 6]```

* Since the first element (-5) is less than the second element (-1), we do not swap.

{:.centered}
```
[-5, -1, 1, 0, 6]
```

* Now we compare the second and third elements. Again, no swapping is necessary since -1 is less than 1.

{:.centered}
```
[-5, -1, 1, 0, 6]
```

* But when we compare the third and fourth elements, because 1 is greater than 0, we swap the third and fourth elements in the array.

{:.centered}
```
[-5, -1, 0, 1, 6]
```

**Iteration 3**

On the 3rd iteration, since all the elements are in order, no swapping occurs as we move through the array and compare elements. 

{:.centered}
```
[-5, -1, 0, 1, 6]
```

I believe this is a piece of information that was missing from my algorithm, since my solution ignores the fact that an array may already be sorted, causing unecessary work to be performed. Basically, the logic only needs to be repeated until no swapping occurs. In my example this occurs after the 3rd iteration of this process, however, my algorithms required 2 more iterations to be performed. 


### My Iterative Solution  - Refactored
I refactored my iterative approach to include a "swapped" variable that flags anytime elements are swapped in the array. I do like however, that my original solution avoids iterating through the entire array by ignoring elements that have already been sorted at the end of the array, so I kept that logic in my refactor.

{% highlight javascript %}
function bubbleSort(array) {
  var length = array.length -1;
  for (var i = 0; i < length; i++) {
    var swapped = false;
    for (var j = 0; j <= length - i; j++) {
      if (array[j + 1] < array[j]) {
        var temp = array[j];
        array[j] = array[j + 1];
        array[j + 1] = temp;
        swapped = true
      }
    }
    if (!swapped) {
      return array;
    }
  }
}
{% endhighlight %}

Notice that in the bubble sort algorithm, the smallest values are eventually "bubbled up" to the beginning of the array.

### Algorithm Complexity

**Best Case**: Linear, or O(n) if the array that we start with is already sorted.

**Worst Case**: Quadratic, or O(n^2). This occurs if the array that we start with is reversed sorted like [5, 4, 3, 2, 1] for example.
