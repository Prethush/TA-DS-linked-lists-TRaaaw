## Implement Sorting Algorithms

1. Write down the steps to perform for different sorting algorithms i.e merge and quick sort. Write the steps in your own words. After writing the algorithm take an example of an array and draw the diagram for each step for different algorithm.

Example:

#### Bubble Sort

step-1: We will compare the first item with the second. If the first item is bigger than the second item we will swap them so that the bigger one stays in the second position.

step-2: And then compare second with third item. If second item is bigger than the third, we swap them. otherwise, they stayed in their position. Hence, the biggest among first three is in the third position.

step-3: We keep doing it. Until we hit the last element of the array. In that way we bubble up the biggest item of the array to the right most position of the array.

step-4: Now we will repeat the step 1, 2 and 3 but we will keep in mind not to touch the last element.

step-5: After repeating all the above steps you will get a sorted array

![Bubble Sort Example](./bubble.png)

<!-- You answer -->

2. Create a function named `mergeSort` that accepts an array of numbers and returns the array with sorted values. The elements should be in ascending order. Use the bubble sorting algorithms. After writing the function test it with an array and check if you are getting the right output.

```js
function mergeSort(unsortedArray) {
  if (unsortedArray.length <= 1) {
    return unsortedArray;
  }
  let middle = Math.floor(unsortedArray.length / 2);
  let left = unsortedArray.slice(0, middle);
  let right = unsortedArray.slice(middle);
  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  let resultArray = [],
    leftIndex = 0,
    rightIndex = 0;
  while (leftIndex < left.length && rightIndex < right.length) {
    if (left[leftIndex] < right[rightIndex]) {
      resultArray.push(left[leftIndex]);
      leftIndex++;
    } else {
      resultArray.push(right[rightIndex]);
      rightIndex++;
    }
  }
  return resultArray
    .concat(left.slice(leftIndex))
    .concat(right.slice(rightIndex));
}
```

3. Create a function named `quickSort` that accepts an array of numbers and returns the array with sorted values. The elements should be in ascending order. Use the selection sorting algorithms. After writing the function test it with an array and check if you are getting the right output.

```js
function quickSort(origArray) {
  // your code
  if (origArray.length <= 1) {
    return origArray;
  } else {
    let left = [];
    let right = [];
    let newArray = [];
    let pivot = origArray.pop();
    let length = origArray.length;

    for (let i = 0; i < length; i++) {
      if (origArray[i] <= pivot) {
        left.push(origArray[i]);
      } else {
        right.push(origArray[i]);
      }
    }

    return newArray.concat(quickSort(left), pivot, quickSort(right));
  }
}
```

4. After writing all the sorting algorithm check the output with the array given below and make sure you are getting the right output.

```js
let values = [76, 34, 12, 32, 4, 2, 123, 5667, 8, 1, 3];
```
