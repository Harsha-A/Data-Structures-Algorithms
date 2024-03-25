# DS-ALGO
Data structure and Algorithm

# Pascal's Triangle
-------------------
Here's a JavaScript function to generate Pascal's Triangle up to a given number of rows:

```javascript
function generatePascalsTriangle(numRows) {
    const triangle = [];

    for (let i = 0; i < numRows; i++) {
        triangle[i] = new Array(i + 1); // Initialize each row with the appropriate length

        // Fill the first and last element of each row with 1
        triangle[i][0] = 1;
        triangle[i][i] = 1;

        // Fill the rest of the elements based on the sum of the elements above in the previous row
        for (let j = 1; j < i; j++) {
            triangle[i][j] = triangle[i - 1][j - 1] + triangle[i - 1][j];
        }
    }

    return triangle;
}
```

You can use this function to generate Pascal's Triangle with a given number of rows. For example:

```javascript
const numRows = 5;
const pascalsTriangle = generatePascalsTriangle(numRows);
console.log(pascalsTriangle);
```

This will output Pascal's Triangle with 5 rows:

```
[
  [1],
  [1, 1],
  [1, 2, 1],
  [1, 3, 3, 1],
  [1, 4, 6, 4, 1]
]
```

Each inner array represents a row of Pascal's Triangle. The elements in each row are the binomial coefficients obtained from the combinations of the row number and the position within the row.


--------------

# Next Permutation 

Here's a JavaScript function to find the next permutation of a given array of numbers:

```javascript
function nextPermutation(nums) {
    // Find the first element from the right that is smaller than the element next to it
    let i = nums.length - 2;
    while (i >= 0 && nums[i] >= nums[i + 1]) {
        i--;
    }

    // If no such element is found, it means the entire sequence is in descending order
    // and it is already the last permutation
    if (i === -1) {
        reverse(nums, 0, nums.length - 1);
        return;
    }

    // Find the smallest element from the right that is greater than nums[i]
    let j = nums.length - 1;
    while (nums[j] <= nums[i]) {
        j--;
    }

    // Swap nums[i] and nums[j]
    [nums[i], nums[j]] = [nums[j], nums[i]];

    // Reverse the elements from i+1 to the end of the array
    reverse(nums, i + 1, nums.length - 1);
}

// Utility function to reverse an array or a portion of it in-place
function reverse(nums, start, end) {
    while (start < end) {
        [nums[start], nums[end]] = [nums[end], nums[start]];
        start++;
        end--;
    }
}
```

You can use this function to find the next permutation of a given array of numbers. For example:

```javascript
let nums = [1, 2, 3];
nextPermutation(nums);
console.log(nums); // Output: [1, 3, 2]
```

This function modifies the input array `nums` in place to generate the next permutation. If the input array is the last permutation, it rearranges the array into the first permutation.


--------


# Kadane's Algorithm

Kadane's Algorithm is used to find the maximum sum subarray within a given array of integers. Here's the JavaScript implementation of Kadane's Algorithm along with an example:

```javascript
function maxSubArray(nums) {
    let maxEndingHere = nums[0]; // Maximum sum ending at the current position
    let maxSoFar = nums[0]; // Maximum sum found so far

    // Iterate through the array starting from the second element
    for (let i = 1; i < nums.length; i++) {
        // Calculate the maximum sum ending at the current position
        maxEndingHere = Math.max(nums[i], maxEndingHere + nums[i]);
        
        // Update the maximum sum found so far
        maxSoFar = Math.max(maxSoFar, maxEndingHere);
    }

    return maxSoFar; // Return the maximum sum found
}

// Example usage:
const nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4];
console.log("Maximum sum of a subarray:", maxSubArray(nums)); // Output: 6 (subarray [4, -1, 2, 1])
```

In this example, the input array is `[-2, 1, -3, 4, -1, 2, 1, -5, 4]`. The maximum sum subarray is `[4, -1, 2, 1]`, and its sum is `6`. Kadane's Algorithm efficiently finds this maximum sum subarray in linear time complexity.



--------


# Sort an array of 0's, 1's and 2's


You can sort an array of 0's, 1's, and 2's, also known as the Dutch National Flag problem, using a variation of the quicksort algorithm called the "Three-Way Partitioning". Here's a JavaScript implementation of sorting an array containing 0's, 1's, and 2's:

```javascript
function sortColors(nums) {
    let low = 0;
    let mid = 0;
    let high = nums.length - 1;

    while (mid <= high) {
        switch (nums[mid]) {
            case 0:
                // Swap nums[low] and nums[mid], increment both pointers
                [nums[low], nums[mid]] = [nums[mid], nums[low]];
                low++;
                mid++;
                break;
            case 1:
                // No swap needed, just move mid pointer forward
                mid++;
                break;
            case 2:
                // Swap nums[mid] and nums[high], decrement high pointer
                [nums[mid], nums[high]] = [nums[high], nums[mid]];
                high--;
                break;
        }
    }
}

// Example usage:
const nums = [2, 0, 2, 1, 1, 0];
sortColors(nums);
console.log(nums); // Output: [0, 0, 1, 1, 2, 2]
```

In this example, the input array `nums` is `[2, 0, 2, 1, 1, 0]`. After sorting using the `sortColors` function, the array becomes `[0, 0, 1, 1, 2, 2]`. This algorithm sorts the array in-place with a time complexity of O(n), where n is the number of elements in the array.


----------

# Stock Buy and Sell

The Stock Buy and Sell problem is a classic problem in which you are given an array of stock prices representing the prices of a stock on different days. The task is to find the maximum profit that can be achieved by buying and selling the stock at most once. Here's a JavaScript implementation of the Stock Buy and Sell problem:

```javascript
function maxProfit(prices) {
    let minPrice = Infinity; // Initialize minimum price to a very large value
    let maxProfit = 0; // Initialize maximum profit to 0

    // Iterate through the array of prices
    for (let price of prices) {
        // Update minimum price seen so far
        minPrice = Math.min(minPrice, price);
        
        // Update maximum profit if selling at the current price gives a better profit
        maxProfit = Math.max(maxProfit, price - minPrice);
    }

    return maxProfit; // Return the maximum profit
}

// Example usage:
const prices = [7, 1, 5, 3, 6, 4];
console.log("Maximum profit:", maxProfit(prices)); // Output: 5
```

In this example, the input array `prices` represents the stock prices on different days. The maximum profit that can be achieved by buying and selling the stock at most once is `5`, which corresponds to buying the stock on day 2 (price = 1) and selling it on day 5 (price = 6). This algorithm has a time complexity of O(n), where n is the number of elements in the array.

