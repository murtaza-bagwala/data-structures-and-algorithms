**Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.**

```
var maxSubArray = (nums) => {
  let currentSum = 0;
    
  let max = 0;
    
  if (nums.length == 1) return nums[0]
    
  if (nums.filter((x) => x < 0).length == nums.length) {
    max = nums[0]
    for(let i = 0; i < nums.length; i++) {
      max = max > nums[i] ? max : nums[i]
    }
    
  } else {
      for (let i = 0; i < nums.length; i++) {
        currentSum += nums[i];
      
        if (currentSum > max) {
          max = currentSum;
        }
      
        if (currentSum < 0) {
          currentSum = 0;
        }
      
      }
    
    }
    
  return max;
};
```

More optimized

```
var maxSubArray = (nums) => {
    
 
  let max = nums[0]
  let sum = 0;
    
  for (let i = 0; i < nums.length; i++) {
      sum += nums[i]
      
      if (sum < nums[i]) {
          sum = nums[i]
      }
      
      max = Math.max(max, sum)
  }  
    
  return max;
};

```