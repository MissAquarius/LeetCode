# [Validate IP Address](https://leetcode.com/problems/validate-ip-address/description/)

<!-- GFM-TOC -->
* <a href="#Description">Description</a>
* <a href="#Example">Example</a>
* <a href="#Solution">Solution</a>
* <a href="#Note">Note</a>
<!-- GFM-TOC -->

## <a name="Solution">Solution</a>
```python
class Solution:
    
    def validIPv4(self, IP):
        ## IPv4的规则:四个数，三个点分隔，每个数的范围是0~255，除了0外不允许0开头  
        list1 = IP.split('.')
        count1 = 0
        if len(list1) == 4:
            for s1 in list1:
                if (len(s1) > 1 and s1[0] == '0') or s1 == None or s1 == '':
                    return False
                else:
                    for i in range(len(s1)):
                        if s1[i] not in '0123456789' :
                            return False
                    sint1 = int(s1)
                    if  0 <= sint1 <= 255:
                        count1 += 1
            if count1 == 4:
                return True

    def validIPv6(self, IP):
        ## IPV6的规则:完全形态是8个16进制填满的四位数（四位全都有数，可以填充0），7个：分隔，每个数0开头的地方可以省略，但是全0不可省为''
        list2 = IP.split(':')
        count2 = 0
        if len(list2) == 8:
            for s2 in list2:
                if len(s2) > 4 or s2 == None or s2 == '':
                    return False
                else:
                    for i in range(len(s2)):
                        if s2[i] not in '0123456789abcdefABCDEF':
                            return False
                    count2 += 1
            if count2 == 8:
                return True
            
    def validIPAddress(self, IP): 
        """
        :type IP: str
        :rtype: str
        """
        if '.' in IP:
            if self.validIPv4(IP):   
                return "IPv4"
            else:
                return "Neither"
            
        if ':' in IP:
            if self.validIPv6(IP):
                return "IPv6"
            else:
                return "Neither"
        return "Neither"

 ```
## <a name="Note">Note</a>
* py中没有三目运算符?
* 注意None和''的区别
* 搞清楚IPv4和IPv6的规则约束
* 美团测开问到过






