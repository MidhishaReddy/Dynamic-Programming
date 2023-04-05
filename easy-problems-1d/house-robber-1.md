---
description: This is a basic problem that has many other
---

# House robber 1

````java

class Solution {
      //now if we have mmore than two houses : we have two options either we try to rob or not rob the house 
        //if we decide not to rob , then we add nothing to the existing robbed amount keeping it dp(i-1) as we dont add i
        //incase we consider adding that house, then we shouldnt consider the previous house rather we shd consider the current one 
        //and the one before the previos to that dp(i-2)+ nums[i]
        
        //lets store the value at each step in the hashmap:

    HashMap<Integer, Integer> memo = new HashMap<>();
    private int[] nums;

    public int rob(int[] nums) {
        this.nums = nums;
        //have a helper class :
        return dp(nums.length-1);
    }

    //helper class:
    public int dp(int i){

        //base case:
        //one house: that value:
        if(i==0) return nums[0];
        //if there are two houses select the one with more money
        if(i==1) return Math.max(nums[0],nums[1]); 

      
        if(!memo.containsKey(i)) {
            memo.put(i,Math.max(dp(i-1),dp(i-2)+nums[i]));
        }   
        return memo.get(i);
    }
}
```

````
