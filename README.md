# Building iterators
Let's build our own iterators: `myEach`, `myMap`, and `myReduce`.

## Getting started

1. **Fork & Clone** this repo.
2. **Plan Ahead**: Research each iterator before you write any code.
3. **Check Your Solution**: Write Driver Code, or run the included Tests (see below).

#### Before You Start Coding

For each of the following challenges, it is essential that you understand the requirements to fully implement the built-in array method you're emulating. See [MDN Array Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

Before you start each problem, ask yourself questions such as:

* What are our inputs?
* What is our output?
* What happens on each loop?
* What does the callback function do?
* What gets passed into our callback function? i.e. what arguments does it receive? (its inputs)
  * Where does the callback come from?
  * How do we know what to name it?

You should be able to answer most of these questions based on the documentation you just read or by experimenting in the browser developer tools.

## Challenges
1. Create a function `myEach` which implements `Array.prototype.forEach`
2. Create a function `myMap` which implements `Array.prototype.map`
3. Create a function `myFilter` which implements `Array.prototype.filter`


> **Pro-Tip**: It's easier to build incrementally than to try to do everything all at once. Remember to start small and add features later.

**Bonuses**:

* Create a function `myReduce` which implements `Array.prototype.reduce`
* Create a function `mySome` which implements `Array.prototype.some`
* Create a function `myEvery` which implements `Array.prototype.every`
* Create a function `myFind` which implements `Array.prototype.find` (`find` is a new JavaScript function!)


# Check Your Solution

## Checking Your Code Using Tests

For each problem (`problems.forEach`!), you can run the provided tests to check your work and confirm your solution.

#### Test Setup

Make sure you are inside the `building_js_iterators_lab` directory.

From the command-line, run:

```bash
# make sure you are inside the building_js_iterators_lab directory
npm install
```

### Running the tests

To run the tests for `myMap` from the command-line, type:

```bash
# make sure you are inside the building_js_iterators_lab directory
mocha test/test-myMap.js
```

This will test the `myMap` function you wrote in `myMap.js`.

You can do the same thing for the other iterators as well:

```bash
# make sure you are inside the building_js_iterators_lab directory
mocha test/test-myEach.js
mocha test/test-myReduce.js
```

> **Pro-Tip**: Let the tests call your function for you. You should not be calling, e.g. `myMap` in your code directly.

#### Sample output:

<strong style="color:green;">GREEN</strong> (✓) - test has passed. Nice work!
<strong style="color:red;">RED</strong> - test has failed. Keep working!

For example, here is some test output with three passing (✓) tests:

```
$ mocha test/test-myMap.js


 myMap
   1) takes and calls a callback function
      results:  []
   2) passes each item in the array to the callback
      results:  []
   3) passes each index in the array to the callback
   ✓ passes the entire array to the callback
      results:  undefined
   4) returns an array
      results:  undefined
   5) returns an array with the same number of elements
      results:  undefined
   6) returns an array constructed from the return values of the callback
      results:  [ 'a', 'b', 'c', 'd' ]
   ✓ doesn't alter the original array
      results:  []
   ✓ works with arrays of length 0
      results:  []
   7) works with arrays of length 1
```

> **Note**: Sometimes tests pass right away. This is called a "false positive". As you start writing code, some of your prematurely "green" tests will turn "red"!

**Example - Failure Message 7**

Here's an example of a failure messages (pay close attention to these, they give you hints!):

```
7) myMap works with arrays of length 1:

  AssertionError: expected 0 to equal 1
  + expected - actual

  +1
  -0

  at Context.testArrayL1 (test/test-myMap.js:115:38)
```

An **assertion** is a statement that *asserts* or says this "MUST BE TRUE".  If
the statement turns out to be false, then the assertion fails and the test fails.  

In the above output we can see that the assertion in `test/test-myMap.js:115:38` (at line 115, and at character 38) expected `0` (the "actual" result) to equal `1` (the "expected" result).

**Example - Failure Message 2**

```
2) myMap passes each item in the array to the callback:
   AssertionError: expected [] to have the same members as [ 'a', 'b', 'c', 'd' ]
    at Context.testEachItem (test/test-myMap.js:37:36)
```

*What do you think this means?*

At line 37 in the test file there was an expectation that an array would have the elements `['a', 'b', 'c', 'd']`.  But instead it got an empty array!

## Checking Your Code By Hand

To check your code manually, we recommend you write simple test code inside of `index.js` instead of from inside your iterator files (e.g. `myEach.js`, `myMap.js`, `myReduce.js`). This helps keep your test code seperate from your "implementation code".

Here's an example of what good manual test code looks like:

``` javascript
//index.js
var input = ["a","b","c"];
var output = myMap(input, function capitalize(v){
    return v.toUpperCase();
});
console.log('Testing myMap')
console.log("Expected:", ["A", "B", "C"], "Got:", output)
```

To execute this code from the command-line, you need to type:

``` bash
# make sure you are inside the building_js_iterators_lab directory
node index.js
```


> **Note**: Even though `myMap` lives in a different file, we still have access to it in `index.js`. That's what `require` is doing.
