# [Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given an array of strings, group anagrams together.</br>

## <a name="Example">Example</a>
>Input: ["eat", "tea", "tan", "ate", "nat", "bat"],</br>
Output:</br>
[</br>
  ["ate","eat","tea"],</br>
  ["nat","tan"],</br>
  ["bat"]</br>
]</br>


## <a name="Solution">Solution</a>
```python
class Solution:
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        ## 以每个单词排序后的值作为key(不可重复),对应的单词作为value,可以将单词分类
        dic = {}
        res =[]
        for i in strs:
            sortstr = ''.join(sorted(i))  ## 因为str是不可变类型,因此将其排序后赋值给另一个变量
            if sortstr in dic:  ## 判断key是否存在,存在就追加到value后面,不存在就创建
                dic[sortstr]+=[i]  ## 这个地方一定要注意是[i],不然加进去的类型是str
            else:
                dic[sortstr] =[i]
            
        ## 输出
        for i in dic:
            res.append(sorted(dic[i]))          
        return res
 ``` 
## <a name="Note">Note</a>
* 比较巧妙的做法:利用dictionary的特性,key不可重复,value可以重复.
* 首先将每个单词的排序后作为key,单词作为value.这样由于key的不可重复性,有着相同字母组合的单词会被分类在一起;然后将dict的value排序输出即可
* 注意:
  * 首先string类型是不可变的,在对其sorted时,可以将其sorted后的结果赋值给其他元素,其本身是不会变的;
  * 在判断key存在: if key in dictionary 存在返回true,不存在返回false
  * 本题中key对应的value是list类型,所以用的是[i],i仅仅是表示那个单词
  
