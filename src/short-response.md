# Short Responses

For this short response assignment, aim to write a response with the following qualities (your instructor will give you feedback on these areas):
- [] Addresses all parts of the prompt
- [] Accurately uses relevant technical terminology
- [] Is free of grammar and spelling mistakes (double check with grammarly!)
- [] Uses markdown to enhance readability (preview in VS Code with Command/Control + Shift + V)
- [] Is easy to comprehend

For each prompt below, write your response in the space provided. Aim to answer each prompt in 2-5 concise sentences. Make sure to preview your markdown to check how it is rendered before submitting.

## Prompt 1

Read the following code:

```js
const playlist1 = { name: "My Favorites", songCount: 10 };
const playlist2 = playlist1;
playlist2.songCount = 15;
console.log(playlist1.songCount);
```

Part A: What will be logged to the console? Why?

Part B: How would you modify the code so that reassigning `playlist2.songCount` does NOT affect `playlist1`.songCount? Write the corrected code below your response (we've provided the broken code again for you to fix).

### Response 1

#### Part A:
The console will log `15`. This is because `playlist1` and `playlist2` both references the same object in memory. Updating `playlist2 .songCount` changes the object itself, so the `playlist1 .songCount` reflects the updated value. 

**Corrected Code:**

```js
// fix this!
const playlist1 = { name: "My Favorites", songCount: 10 };
const playlist2 = { ...playlist1};
playlist2.songCount = 15;
console.log(playlist1.songCount);
console.log(playlist2.songCount);
```

---

## Prompt 2

```js
const students = [
  { name: "Maya", grade: 92, passed: true },
  { name: "Jamal", grade: 78, passed: true },
  { name: "Destiny", grade: 88, passed: true },
  { name: "Marcus", grade: 95, passed: true }
];
```

For each task below, identify which array method (forEach, filter, map, find, or reduce) you would use.

1. You need to get an array containing only students who scored above 85.
2. You need to find the student named "Destiny" and update their grade to 90.
3. You need to calculate the average grade of all students.
4. You need to create an array of strings in the format: "Maya: 92"

### Response 2

1. In order to find the students who scored above 85, we would need to use the `.filter` method because it will `return` a new array of students which meets the condition.
2. In order to find `Destiny` and update the grade, we would need to use the `.find` method so it can locate the specific student object. 
3. In order to calculate the average grade of all students we have to use the `.reduce` method which will accumulate the sum of all grades to calculate the average.
4. In order to create an array of strings `"Name: grade"` we can use the `.map` method which transforms each student object into a formatted string.

---

## Prompt 3

We should expect that the code below prints the array `[ 'A', 'B', 'C', 'D' ]` but an error is thrown when the third line of code is executed.

Explain why this error occurs, how to fix it, and provide a suggestion for how to avoid this error in the future.

```js
const letters = ['a', 'b', 'c', 'd'];
const capitalize = (str) => str.toUpperCase();

const upperCaseLetters = letters.map(capitalize());
// Uncaught TypeError: Cannot read properties of undefined (reading 'toUpperCase')

console.log(upperCaseLetters);
```

### Response 3

The error occurs because `capitalize()` calls the function immediately and passes `undefined` to `map`, instead of passing the function itself  `.map` expects a function reference, not the result of a function call.

#### Fix
Pass the function without parenthesis.

```js
const letters = ['a', 'b', 'c', 'd'];
const capitalize = (str) => str.toUpperCase();

const upperCaseLetters = letters.map(capitalize);

console.log(upperCaseLetters);

```

---

## Prompt 4

Given this code:

```js
const orders = [
  { id: 1, total: 45 },
  { id: 2, total: 23 },
  { id: 3, total: 67 }
];

const grandTotal = orders.reduce((sum, order) => {
  return sum + order.total;
}, 0);
```

- Part A: What will `grandTotal` equal after this code runs?
- Part B: Explain what the `0` at the end of the reduce method does. Why is it important?
- Part C: Walk through what happens in the FIRST iteration of reduce:
    - What is the value of sum?
    - What is the value of order?
    - What gets returned?

### Response 4

#### Part A
`grandTotal` will equal `135`.

#### Part B
The `0` at the end of `reduce` the initial value of the accumulator(sum). It is important because it ensures that the first iteration has a valid starting point and prevents errors if the array is empty.

#### Part C
- sum = 0 (initial value)
- order = { id : 1, total: 45 } (first element of the array)
- Returned value = sum + order.total -> 0 + 45 = 45
The returned value becomes the new sum for the next iteration.