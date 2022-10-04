[Leet code question](https://leetcode.com/problems/pascals-triangle-ii/)

```
var getRow = (rowIndex) => {
    const n = rowIndex + 1
    
    table = Array(n).fill().map(() => Array(n + 1).fill(0))
    
    table[0][1] = 1
    
    for (i = 1 ; i < n; i++ ) {
       for (j = 1; j <= i + 1; j++) {
         table[i][j] = table[i-1][j-1] + table[i-1][j]
       }
    }
    
    return table[rowIndex].filter((y) => y != 0);
    
};
```