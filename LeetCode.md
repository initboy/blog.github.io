# Python 刷LeetCode


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




[388]:https://leetcode-cn.com/problems/longest-absolute-file-path/
