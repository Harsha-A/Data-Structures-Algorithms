# DS-ALGO
Data structure and Algorithm


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

