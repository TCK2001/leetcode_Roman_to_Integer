# leetcode_Roman_to_Integer
+ 이번엔 반대로 로마숫자를 주면은 숫자로 바꾸는 문제
+ 這次是剛好跟前一個題目相反，是羅馬數字改成數字

-----
+ Example1
```
Input: s = "III"
Output: 3
Explanation: III = 3.
```
----
+ Example2
```
Input: s = "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
```
----
+ Example3
```
Input: s = "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```
----
```python
class Solution:
    def romanToInt(self, s: str) -> int:
        book = {"I": 1, "V": 5, "X": 10, "L": 50, "C": 100, "D": 500, "M": 1000}
        res = []

        if "IV" in s: # 모든 가능한 가짓수 써놓기
            res.append(4)
            s = s.replace("IV", "")
        if "VI" in s:
            res.append(6)
            s= s.replace("VI","")
        if "IX" in s:
            res.append(9)
            s = s.replace("IX", "")
        if "XI" in s:
            res.append(11)
            s = s.replace("XI", "")
        if "XL" in s:
            res.append(40)
            s = s.replace("XL", "")
        if "XC" in s:
            res.append(90)
            s = s.replace("XC", "")
        if "CD" in s:
            res.append(400)
            s = s.replace("CD", "")
        if "CM" in s:
            res.append(900)
            s = s.replace("CM", "")

        for i in s: # 마지막으로 짤짤이 처리하기
            res.append(book[i])

        return sum(res) # append했기에 그 줄을 모두 더하기
```
---
```
결론 : 
IV같은 두개짜리를 먼저 처리하고 마지막으로 I
```
---
```
結論:
先把兩個以上的東西排除掉 再計算I或者M一些一個的東西
```
---
### Result
Runtime: 64 ms, faster than 67.24% of Python3 online submissions for Roman to Integer.\
Memory Usage: 13.8 MB, less than 76.12% of Python3 online submissions for Roman to Integer.
