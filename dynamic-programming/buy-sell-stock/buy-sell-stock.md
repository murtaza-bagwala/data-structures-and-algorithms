***You are given an integer array prices where prices[i] is the price of a given stock on the ith day.
Find and return the maximum profit you can achieve.***

Input: prices = [7,1,5,3,6,4]
Output: 7

```
var maxProfit = (prices) => {
    
    let min = prices[0]
    let maxProfit = 0;
    let currentProfit = 0;
    
    for (i = 1; i < prices.length; i++ ) {
        
        currentProfit = prices[i] - min
        
        maxProfit = maxProfit > currentProfit ? maxProfit : currentProfit
        
        min  = min < prices[i] ? min : prices[i]
    }
    
    return maxProfit;
    
};

```