# Algorithmic Complexity + Big O Notation

## Learning Objectives
* Identify what makes a good algorithm
* Use Big-O Analysis to Evaluate Algorithms

### What makes a good algorithm?

When we work with relatively small inputs, like we have for the most part in this class, using an efficient algorithm to solve a problem is not crucial. Instead, it is more important to have clean code, good interfaces, and bug-less applications. However, once we are working with huge inputs our code will get a lot slower. At that point, building efficient algorithms becomes really important.

When we write code, one of our main goals is to make that code execute quickly. If our code is inefficient, our sites will load slowly and users may leave. We also want to use as little memory as possible when we execute our code so that it is less expensive to host our sites. These are usually the two best measures of the effectiveness of an algorithm, their speed and their memory use.

## Run Time and Big-O Analysis

We can look at a program and say -- "Oh that took two seconds to run". But that two seconds is dependent on a lot of factor. That two seconds is for a very specific input. If we make the input 100 items instead of 10, what happens? Also, that two seconds is on a certain computer with a certain version of your programming language. Instead, we should generalize the algorithm's complexity.

We do so using a notation that mathematicians and computer scientists use, called Big-O notation. This notation standardizes how we discuss the efficiency of algorithms. Most of the time, we use Big-O notation to describe time complexity, but we can also use it to describe memory efficiency.

Big-O notation is not an exact metric for benchmarking algorithms. Rather, it gives us an abstract idea about how costly or efficient an algorithm is, with respect to how much computing power it takes. With Big-O notation, we are comparing orders of magnitude.

A few notes on Big-O notation:
* When we calculate the Big-O of the function, we are calculating the **worst** possible runtime for a given function.
* Sometimes, Big-O notation is referred to as [asymptotic analysis](http://www.cs.cornell.edu/courses/cs3110/2013sp/supplemental/lectures/lec19-asymp/review.html).

For time complexity, we want to count how many times the code is run in context of how large the input to the code is. For example, O(1) is a very efficient piece of code, O(N!) is very inefficient. Let's break this down into categories of Big-O.

### O(1) Complexity (aka Constant Complexity)

O(1) means that an algorithm's runtime is static or constant. The complexity stays the same no matter the input.

```javascript
function helloWorld (arr) {
	console.log('hello world')
}

function returnFirstItem (arr) {
	return arr[0]
}
```

In both of the above examples, no matter what size the `arr` argument is, the function will run once.

### O(N) Complexity (aka Linear Complexity)

O(N) complexity means that, as the input sizes increase, the processing time increases linearly. Or, more simply, the code runs once for each input.

```javascript
function iterate (arr) {
	arr.forEach(item => console.log(item))
}

function iterateLoop (arr) {
	for (let i = 0; i < arr.length; i++) {
		console.log(arr[i])
	}
}

function addOne (arr) {
	return arr.map(item => item + 1)
}
```

In each of the above examples, we go through the array and perform an action with each item in it. If we have the array `[1]`, each will execute once. If we have the array `[3, 5, 1000]` the code will run 3 times. If our array has 1000 items, the code will execute 1000 times!

### O(N^2) Complexity (aka Quadratic Complexity)

For an input with the size n, quadratically complex algorithms execute n*n times. 

```javascript
function consoleLogLots (arr) {
	for (let i = 0; i < arr.length; i++) {
		for (let j = 0; j < arr.length; j++) {
			console.log(arr[i], arr[j])
		}
	}
}
```
For the array `[1, 3]`, this function will print:
```js
[1, 1]
[1, 3]
[3, 1]
[3, 3]
```
For a 2 item array, the code executes 4 times. This scales pretty fast -- for an array with 100 items this code will `console.log` 10,000 times!

### Big-O Summary
![](https://i.stack.imgur.com/jIGhf.png)

The following table shows how algorithms with different complexities scale when given different numbers of inputs. Note: some values are rounded.

|Complexity |1|10      |100  |
|-----------|-|--------|-----|
|O(1)       |1| 1      |1    |
|O(N)       |1|10      |100                            |
|O(N^2)     |1|100     |10000                          | 
|O(2^N)     |1|1024    |1267650600228229401496703205376|       
|O(N!)      |1|3628800 |doesn't fit on screen! |


Let's look at this demo in javascript...
- Code: [JS](https://git.generalassemb.ly/ga-wdi-lessons/cs-algorithms/blob/master/js-example/script.js), [HTML](https://git.generalassemb.ly/ga-wdi-lessons/cs-algorithms/blob/master/js-example/index.html)
- [Deployed](http://aboard-thought.surge.sh)

### You Do: Study Big-O Families

[Write down the complexities of these functions](https://gist.github.com/amaseda/c4283f5c58b9b68be9318259098f0298). 


## Learn More!
* https://www.youtube.com/watch?v=V6mKVRU1evU
* http://www.cs.cmu.edu/afs/cs/academic/class/15451-s10/www/lectures/lect0203.pdf
* https://stackoverflow.com/questions/487258/what-is-a-plain-english-explanation-of-big-o-notation/487278
* https://www.codenewbie.org/basecs
* http://bigocheatsheet.com/

