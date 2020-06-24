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



[34]:https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/
[388]:https://leetcode-cn.com/problems/longest-absolute-file-path/
