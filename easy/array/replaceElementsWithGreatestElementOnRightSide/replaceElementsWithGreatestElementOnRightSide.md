## [Replace Elements with Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/description/)
### Description:
![Replace Elements with Greatest Element on Right Side](./replaceElementsWithGreatestelementOnRightSide.png)
### Solution:
```Go
func replaceElements(arr []int) []int {
	result := make([]int, len(arr))
	
	templateMax := -1
	for i := len(arr)-1; i >= 0; i-- {
		result[i] = templateMax
		templateMax = max(templateMax, arr[i])
	}
	
	return result
}
```
### Time complexity: 
$$ O(n) $$
### Space complexity:
$$ O(1) $$

---
