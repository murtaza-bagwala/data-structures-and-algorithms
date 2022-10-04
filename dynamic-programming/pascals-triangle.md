[Leet code question](https://leetcode.com/problems/pascals-triangle/)


```
var generate = (numRows) => {
    const n = numRows
    
    table = Array(n).fill().map(() => Array(n + 1).fill(0))
    
    table[0][1] = 1
    
    for (i = 1 ; i < n; i++ ) {
       for (j = 1; j <= i + 1; j++) {
         table[i][j] = table[i-1][j-1] + table[i-1][j]
       }
    }
    
    return table.map((x) => x.filter((y) => y != 0));
    
};

```