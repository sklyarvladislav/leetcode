## [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/)
### Description:
![Intersection of Two Arrays II](intersectionOfTwoArraysII.png)
### Solution:
```Go
func intersect(nums1, nums2 []int) []int {
	seen := make(map[int]int)
	result := make([]int, 0, len(nums1))
	
	for _, num := range nums1 {
		seen[num]++
	}
	
	for _, num := range nums2 {
		if seen[num] > 0 {
			result = append(result, num)
			seen[num]--
		}
	}
	
	return result
}
```
### Time complexity: 
$$ O(n + m) $$
### Space complexity:
$$ O(min(n, m)) $$

---
