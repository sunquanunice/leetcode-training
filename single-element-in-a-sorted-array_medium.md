Leetcode link: https://leetcode.com/problems/single-element-in-a-sorted-array/

```
class Solution {
    public int singleNonDuplicate(int[] nums) {
        for(int i = 0; i < nums.length; i+=2) {
            if (i == nums.length -1 || nums[i] != nums[i+1]) {
                return nums[i];
            } 
        }
        return nums[0];
    }
}
```