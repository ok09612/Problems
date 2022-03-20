# 1910. Remove All Occurrences of a Substring
# https://leetcode.com/problems/remove-all-occurrences-of-a-substring/

```python
class Solution:
    def removeOccurrences(self, s: str, part: str) -> str:
        
        while s.count(part) > 0:
            # s = s.replace(part,'')
            s = s[0:s.index(part) + len(part)].replace(part,'') + s[s.index(part) + len(part):]

        return s
```