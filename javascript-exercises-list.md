# JavaScript Exercises List

### Function that takes two numbers as parameters and returns their sum.

#### Example 1
```js
function getSum(n1, n2) {
  return n1 + n2;
}
const sum = getSum(5, 2);
console.log(sum);  
// Output: 7
```
#### Example 2: Using arrow function
```js
const getSum = (n1, n2) => {
  return n1 + n2;
}
const sum = getSum(5, 2);
console.log(sum);  
// Output: 7
```

### Function to return the length of an array:
```js
function getArrayLength(arr) {
  return arr.length;
}
```

### Function to reverse a string:
```js
function reverseString(str) {
  return str.split('').reverse().join('');
}
```

### Function to return the largest number in an array:

```js
function getMaxNumber(arr) {
  return Math.max(...arr);
}
```

### Function to count the number of words in a sentence:

```js
function countWords(sentence) {
  return sentence.split(' ').length;
}
```

###Function to capitalize all strings in an array:

```js
function capitalizeStrings(arr) {
  return arr.map(str => str.toUpperCase());
}
```

### Function to check if a number is even:

```js
function isEven(number) {
  return number % 2 === 0;
}
```

### Function to filter even numbers from an array:

```js
function getEvenNumbers(arr) {
  return arr.filter(number => number % 2 === 0);
}
```

### Function to check if a string is a palindrome:

```js
function isPalindrome(str) {
  const reversedStr = str.split('').reverse().join('');
  return str === reversedStr;
}
```

### Function to find the longest string in an array:
```js
function getLongestString(arr) {
  return arr.reduce((longest, current) => {
    return current.length > longest.length ? current : longest;
  }, '');
}
```

### Function to calculate the factorial of a number:
```js
function calculateFactorial(num) {
  if (num === 0 || num === 1) {
    return 1;
  }
  return num * calculateFactorial(num - 1);
}
```

### Function to calculate the sum of numbers in an array:

```js
function calculateSum(arr) {
  return arr.reduce((sum, number) => sum + number, 0);
}
```


### Function to check if a string contains only digits:

```js
function containsOnlyDigits(str) {
  return /^\d+$/.test(str);
}
```

### Function to find common elements between two arrays:

```js
function getCommonElements(arr1, arr2) {
  return arr1.filter(element => arr2.includes(element));
}
```
Function to reverse the order of words in a sentence:
