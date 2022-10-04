[Leet code question](https://leetcode.com/problems/delete-operation-for-two-strings/)

```
 
var commonSubsequence = (text1, text2, index1, index2, memo = {}) => {
    
    if ( index1 == text1.length || index2 == text2.length ) return 0
    
    if ( `${index1}${index2}` in memo ) return memo[`${index1}${index2}`]
    
    if (text1[index1] === text2[index2]) {
        memo[`${index1}${index2}`] = 1 + commonSubsequence(text1, text2, index1 + 1, index2 + 1, memo)
    } else {
        memo[`${index1}${index2}`] = Math.max(commonSubsequence(text1, text2, index1 + 1, index2, memo), commonSubsequence(text1, text2, index1, index2 + 1, memo))
    }
    
    return memo[`${index1}${index2}`];
    
}

var minDistance = function(word1, word2) {
     return word1.length + word2.length - 2 * commonSubsequence(word1, word2, 0, 0)
    
};

```