
[Leet code question](https://leetcode.com/problems/longest-palindromic-subsequence/submissions/)


```
var commonSubsequence = (text1, index1, index2, memo = {}) => {
    
    if ( index1 > index2 ) return 0
    
    if ( index1 == index2 ) return 1
    
    if ( `${index1}${index2}` in memo ) return memo[`${index1}${index2}`]
    
    if (text1[index1] === text1[index2]) {
        memo[`${index1}${index2}`] = 2 + commonSubsequence(text1, index1 + 1, index2 - 1, memo)
    } else {
        memo[`${index1}${index2}`] = Math.max(commonSubsequence(text1, index1 + 1, index2, memo), commonSubsequence(text1, index1, index2 - 1, memo))
    }
    
    return memo[`${index1}${index2}`];
    
}


var longestPalindromeSubseq = function(s) {
    return commonSubsequence(s, 0, s.length - 1)
    
};

```