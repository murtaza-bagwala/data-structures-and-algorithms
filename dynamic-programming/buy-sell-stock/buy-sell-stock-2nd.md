[Leet code question](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

```
var profit = (prices, index, canBuy, memo = {}) => {
    if ( `${index}${canBuy}` in memo ) return memo[`${index}${canBuy}`]
    
    if (index == prices.length) return 0;
    
    let prof = 0;
    
    if(canBuy) {
        prof = Math.max(-prices[index] + profit(prices, index + 1, false, memo),
                          0 + profit(prices, index + 1, true, memo));
        memo[`${index}${canBuy}`] = prof
                         
    }
     else {
        prof = Math.max(prices[index] + profit(prices, index + 1, true, memo),
                          0 + profit(prices, index + 1, false, memo))
         memo[`${index}${canBuy}`] = prof
     }
    
    return prof;
}


var maxProfit = (prices) => {
    return profit(prices, 0, true)
    
};

```