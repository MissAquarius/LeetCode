# [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->


## <a name="Description">Description</a>
>Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.</br>
An input string is valid if:</br>
Open brackets must be closed by the same type of brackets.</br>
Open brackets must be closed in the correct order.</br>
Note that an empty string is also considered valid.</br>

## <a name="Example">Example</a>
>Input: "()"</br>
Output: true</br></br>
Input: "()[]{}"</br>
Output: true</br></br>
Input: "(]"</br>
Output: false</br></br>
Input: "([)]"</br>
Output: false</br></br>
Input: "{[]}"</br>
Output: true</br></br>

## <a name="Solution">Solution</a>
```python

# 定义一个匹配函数
def isMatch(a, b):
        if ((a=='(' and b==')') or (a=='[' and b==']') or (a=='{' and b=='}')):
            return True
        return False
    
class Solution:
    def isValid(self, s):
        # 栈
        t=[]
        if len(s) == 0:
            return True
        else:
            t.append(s[0])
            i=1
            while(i<len(s)):
                if len(t)>0 and isMatch(t[-1], s[i]): #特别注意条件len(t)>0不要忘记
                    t.pop()
                else:
                    t.append(s[i])
                i += 1
        return len(t) == 0
           
        
            
            
```
## <a name="Note">Note</a>
* 本题是简单的括号匹配问题,用的是栈操作:将每个字符与栈顶元素比较,若相同则出栈并继续往下一个元素比较;若不同,则当前元素进栈,继续比较下一个元素
* 注意点:在出栈比较的时候特别注意此时栈里至少有一个元素,否则会出现错误
* py中,删除列表中的元素有三种方法,分别是:
  ** list.pop(index);  接收的参数是索引,默认是最后一个元素(出栈)
    * list.remove(value); 接收的参数是待删除元素的值.这样做风险大,因为 list 允许重复,remove() 删除的列表中第一个和参数值相等的元素
    * list.del(value)
* py中,插入列表中的元素有三种方法,分别是:
    * list.append(value);  在最后一个元素后追加(入栈)
    * listA.extend(listB) 将一个列表中每个元素分别添加到另一个列表中,只接受一个参数,相当于是将list B 连接到list A上
    * list.insert(index,value) 参数有两个:第一个参数是索引点,即插入的位置;第二个参数是插入的元素值




