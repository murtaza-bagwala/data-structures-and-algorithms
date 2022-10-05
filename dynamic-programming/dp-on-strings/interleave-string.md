[Leetcode Question](https://leetcode.com/problems/interleaving-string/)

```
var computeInterleave = (text1, text2, text3, index1, index2, index3, memo = {}) => {

    
    if ( `${index1}*${index2}*${index3}` in memo ) return memo[`${index1}*${index2}*${index3}`]
    
    if (index1 === text1.length && index2 === text2.length && index3 === text3.length) return true
    
    if ( index1 === text1.length ) {
         memo[`${index1}*${index2}*${index3}`] = text2[index2] === text3[index3] ? computeInterleave(text1, text2, text3, index1, index2 + 1, index3 + 1, memo) : false
        return memo[`${index1}*${index2}*${index3}`] 
    }
    if ( index2 === text2.length ) {
         memo[`${index1}*${index2}*${index3}`] = text1[index1] === text3[index3] ? computeInterleave(text1, text2, text3, index1 + 1, index2, index3 + 1, memo) : false
        return memo[`${index1}*${index2}*${index3}`] 
    }
    
    let a = false;
    let b = false;
    
    if (text1[index1] === text3[index3]) {
        a = computeInterleave(text1, text2, text3, index1 + 1, index2, index3 + 1, memo)
    } 
        
     if (text2[index2] === text3[index3]) {
        b = computeInterleave(text1, text2, text3, index1, index2 + 1, index3 + 1, memo)
     }     
    
        
    memo[`${index1}*${index2}*${index3}`] = a || b    
    
    return memo[`${index1}*${index2}*${index3}`];
    
}


var isInterleave = function(s1, s2, s3) {
    
   return computeInterleave(s1, s2, s3, 0, 0 ,0)
};

```

- Idea was to compare each char of main string with the chars if other 2 string 
- If matches increament indexes

- If all strings are parsed return true

- Memoized the same