## [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring)

### 1 способ:

- скользящее окно и паттерн нашей строки

```go
func minWindow(s string, t string) string {
	if len(s) < len(t) { return "" }
	minLen, minStart, start := math.MaxInt32, 0, 0
	count := len(t)
	freqMap := [128]int{}
	
	for _, char := range t {
		freqMap[char]++
	}
	
	for end := 0; end < len(s); end++ {
		if freqMap[s[end]] > 0 {
			count--
		}
		freqMap[s[end]]--
		
		for count == 0 {
			if end-start+1 < minLen {
				minLen = end-start+1
				minStart = start
			}
			
			freqMap[s[start]]++
			if freqMap[s[start]] > 0 {
				count++
			}
			start++
		}
	}
	
	if minLen == math.MaxInt32 { return "" }
	return s[minStart:minStart+minLen]
}
```
time complexity:$$ O(n) $$
space complexity:$$ O(1) $$

---
## [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/description)

### 1 способ: 

- пишем вспомогательную функцию для сливания двух списков, а затем идем по списку списков и парами сливаем

```go
func mergeTwoLists(l1, l2 *ListNode) *ListNode  {
	dummy := &ListNode{}
	previous := dummy
	
	for l1 != nil && l2 != nil {
		if l1.Val < l2.Val {
			previous.Next = l1
			l1 = l1.Next
		} else {
			previous.Next = l2
			l2 = l2.Next
		}
		previous = previous.Next
	}
	
	if l1 != nil {
		previous.Next = l1
	} else {
		previous.Next = l2
	}
	
	return dummy.Next
}

func mergeKLists(lists []*ListNode) *ListNode {
	if len(lists) == 0 { return nil }
	
	for len(lists) > 1 {
		var mergedLists []*ListNode
		for i := 0; i < len(lists); i += 2 {
			l1 := lists[i]
			var l2 *ListNode
			if i+1 < len(lists) {
				l2 = lists[i+1]
			}
			mergedLists = append(mergedLists, mergeTwoLists(l1, l2))
		}
		lists = mergedLists
	}
	
	return lists[0]
}
```
time complexity:$$ O(n \cdot log(k)) $$
space complexity:$$ O(log(k)) $$

---
