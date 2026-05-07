## [Maximum Number of Words Found In Sentences](https://leetcode.com/problems/maximum-number-of-words-found-in-sentences/description/)
### Description:
![Maximum Number of Words Found In Sentences](./maximumNumberOfWordsFoundInSentences.png)
### Solution:
```Go
func mostWordsFound(sentences []string) int {
	result := 0
	
	for _, sentence := range sentences {
		count := 0
		
		for i := 0; i < len(sentence); i++ {
			if rune(sentence[i]) == ' ' {
				count++
			}
		}
		
		result = max(result, count)
	}
	
	return result + 1
}
```
### Time complexity: 
$$ O(n \cdot m) $$
### Space complexity:
$$ O(1) $$

---
