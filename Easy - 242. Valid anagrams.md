Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

**Example 1:**

**Input:** s = "anagram", t = "nagaram"

**Output:** true

**Example 2:**

**Input:** s = "rat", t = "car"

**Output:** false

**Constraints:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` and `t` consist of lowercase English letters.

<h1> Solution </h1>
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length())
        {
            return false;
        }
        else
        {
            TreeMap<Character, Integer> tTreeMap = new TreeMap<>();
            for(int i = 0; i < t.length() ; i++)
            {
                if(tTreeMap.containsKey(t.charAt(i)))
                {
                    tTreeMap.compute(t.charAt(i), (key, value) -> value + 1);
                }
                else
                {
                    tTreeMap.put(t.charAt(i),1);
                }
            }
            System.out.println(tTreeMap);
            TreeMap<Character, Integer> sTreeMap = new TreeMap<>();
            for(int i = 0; i < s.length() ; i++)
            {
                if(sTreeMap.containsKey(s.charAt(i)))
                {
                    sTreeMap.compute(s.charAt(i), (key, value) -> value + 1);
                }
                else
                {
                    sTreeMap.put(s.charAt(i),1);
                }
            }
            System.out.println(sTreeMap);
            if(tTreeMap.equals(sTreeMap))
            {
                return true;
            }
            else
            {
                return false;
            }
        }
    }
}
```
