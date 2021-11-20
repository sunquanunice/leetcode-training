Leetcode link: https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/

```
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        int rangeEnds = nums.length;
        List<Integer> disappearedNums = new ArrayList<>();
        for (int i = 1; i <= rangeEnds; i++) {
            final int j = i;
            boolean contains = IntStream.of(nums).anyMatch(x -> x == j);
            if (!contains) {
                disappearedNums.add(i);
            }
        }
        
        return disappearedNums;
    }
}
```
