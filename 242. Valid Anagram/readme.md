Given two strings s and t , write a function to determine if t is an anagram of s.

**Example 1:**

Input: s = "anagram", t = "nagaram"
Output: true

**Example 2:**

**Input:** s = "rat", t = "car"

**Output:** false

**Note:**
You may assume the string contains only lowercase alphabets.

**Follow up:**
What if the inputs contain unicode characters? How would you adapt your solution to such case?

**思路：**
采用字典进行存储，对每个字母进行相应的统计

~~~
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        sn = len(s)
        tn = len(t)
        lists = []
        listt = []
        if sn != tn:
            return False
        for i in range(0, sn):
            lists.append(s[i])
        #print(lists)
        #print("-----------------------------------")
        for j in range(0, tn):
            listt.append(t[j])
        #print(listt)
        listt.sort()
        #print(listt)
        lists.sort()
        #print(lists)
        if lists == listt:
            return True
        else:
            return False
        # letters = {}
        # letters2 = {}
        # for c in s:
        #     letters[c] = letters[c] + 1 if c in letters else 1
        #     #print(letters[c])
        #     print(letters)
        # print("=======================================")
        # for d in s:
        #     letters2[d] = letters2[d] + 1 if d in letters2 else 1
        #     #print(letters2[c])
        #     print(letters2)
        # if letters == letters2:
        #     return True
        # else:
        #     return False

if __name__ == "__main__":
    a = "anagram"
    b = "nagaram"
    print(Solution().isAnagram(a, b))
~~~
