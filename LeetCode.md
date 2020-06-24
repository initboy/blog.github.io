# Python 刷LeetCode

## [34.在排序数组中查找元素的第一个和最后一个位置][34]

``` python
class Solution(object):
    def findIndex(self, nums, target, isLeft):
        left = 0
        right = len(nums)
        while left < right:
            mid = (left + right) // 2
            if (nums[mid] > target) or (isLeft and (target == nums[mid])):
                right = mid
            else:
                left = mid + 1
        return left

    def searchRange(self, nums, target):
        leftIndex = self.findIndex(nums, target, True)
        if (leftIndex == len(nums)) or (nums[leftIndex] != target):
            return [-1, -1]
        rightIndex = self.findIndex(nums, target, False) - 1
        return [leftIndex, rightIndex]  
```

## [388.文件的最长绝对路径][388]

``` python
    def lengthLongestPath(self, input):
        newLine = '\n'
        tab = '\t'
        dot = '.'
        lenTab = len(tab)
        maxPathLength = 0
        maxFileLength = {}
        lines = input.split(newLine)
        for line in lines:
            lenFile = len(line.replace(tab, ''))
            x = len(line) - lenFile
            key = int(x / lenTab)            
            for k in list(maxFileLength.keys()):
                if(k > key):
                    del maxFileLength[k]
            if((dot in line) and (line[-1] != dot)):
                maxFileLength[key] = lenFile
                temp = 0
                for k in maxFileLength:
                    temp = temp + int(maxFileLength[k])
                temp = temp + len(maxFileLength) - 1
                if(temp > maxPathLength):
                    maxPathLength = temp
            else:
                maxFileLength[key] = lenFile
        return maxPathLength
```

## [633. 平方数之和][633]
> 费马平方和定理，一个非负整数C, C能够表示为两个整数的平方和，当且仅当C的所有形如 4k+3的质因子的幂次均为偶数。  
费马平方和定理的表述是：奇质数能表示为两个平方数之和的充分必要条件是该质数被4除余1。
``` python
class Solution(object):
    def judgeSquareSum(self, c):
        i = 2
        while (i * i < c):
            n = 0
            if((c % i) == 0):
                while((c % i) == 0):
                    n += 1
                    c = c / i
                if((n % 2 != 0) and (i % 4 == 3)):
                    return False
            i += 1
        return (c % 4) != 3

```
> 常规双指针
``` python
class Solution(object):
    def judgeSquareSum(self, c):
        a = 0
        b = int(c**0.5)
        while a <= b:
            x = a**2
            y = c - b**2
            if x == y:
                return True
            elif y < x:
                b -= 1
            else:
                a += 1
        return False
```


[34]:https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/
[388]:https://leetcode-cn.com/problems/longest-absolute-file-path/
[633]:https://leetcode-cn.com/problems/sum-of-square-numbers/
