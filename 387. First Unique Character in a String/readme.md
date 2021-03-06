Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

**Examples:**

s = "leetcode"
return 0.

s = "loveleetcode",
return 2.

**Note:** You may assume the string contain only lowercase letters.

**思路：**
蛮力法遍历

**网上思路：**<https://blog.csdn.net/coder_orz/article/details/52387946>
通过字典进行存储，统计字典中出现的次数
~~~
from jieba import xrange


class Solution(object):
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        letters = {}
        for c in s:
            letters[c] = letters[c] + 1 if c in letters else 1
        for i in xrange(len(s)):
            if letters[s[i]] == 1:
                return i
        return -1

if __name__ == "__main__":
    s = "aadd"
    s1 = "aassd"
    s2 = "loveleetcode"
    #print(Solution().firstUniqChar(s))
    print(Solution().firstUniqChar(s1))
    #print(Solution().firstUniqChar(s2))
~~~

