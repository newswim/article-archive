### Reduce (reigns supreme)

> definition: A function that takes an array, and returns something else






#### 7. Pipeline

Let's say we have a task: Upon being given a value, that value should be
incremented, then doubled, then decremented. An imperative style might look like this:

```js
// here are the transformation functions

function increment(input) { return input + 1; }
function decrement(input) { return input - 1; }
function double(input) { return input * 2; }
function halve(input) { return input / 2; }

// begin imperative block of code

var initial_value = 1;
var incremented_value = increment(initial_value)
var doubled_value = double(incremented_value)
var final_value = decrement(doubled_value)

console.log(final_value)      // 3
```

Certainly, if we had to write these kinds of steps every day, we might consider
alternative career choices. As programmers, we may take a look a these steps and
think, "Oh, I can just write a function that does all of those steps."

That is correct, however imagine a scenario even a little more sophisticated than
this contrived example, the technical overhead of trying to debug quickly escalates.
But, for perpetuity sake, let's write what that might look like:

```js

var initial_value = 1;

var final_value = function(value) {
  return ((value + 1) * 2) - 1;
}

console.log(final_value)      // 3
```

This is a little better, in terms of code noise, however it's doing a lot of
value transformations, and is no longer doing just a single thing to our value.

With the native `Array.prototype.reduce()` function from JavaScript, we're able
to construct a pipeline which guides our value through a chain of transformations
and returns the altered data.

Let's create a pipeline:

```js
function increment(input) { return input + 1; }
function decrement(input) { return input - 1; }
function double(input) { return input * 2; }
function halve(input) { return input / 2; }

var initial_value = 1;

var pipeline = [
  increment,
  double,
  decrement
]

var final_value = pipeline.reduce(function(acc, fn) {
  return fn(acc)
}, initial_value)

console.log(final_value)        // 3

```

It might seem quite a bit more complex, and there are definitely more characters
that have to be banged out -- but look at what we've gained: complete control and
composability.

The pipeline is an array, and therefore it can be programmatically generated.

Imagine if the steps needed to change depending on user input,



###### most of the information here was presented as a course from Egghead.io
