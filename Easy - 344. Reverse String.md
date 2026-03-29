Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with `O(1)` extra memory.

**Example 1:**

**Input:** s = ["h","e","l","l","o"]
**Output:** ["o","l","l","e","h"]

**Example 2:**

**Input:** s = ["H","a","n","n","a","h"]
**Output:** ["h","a","n","n","a","H"]

**Constraints:**

- `1 <= s.length <= 105`
- `s[i]` is a [printable ascii character](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

<h1> Soln </h1>

```java
class Solution {
    public void reverseString(char[] s) {
        for (int i = 0; i < (s.length)/2; i++)
        {
            char t = s[i];
            s[i] = s[s.length -1 -i];
            s[s.length -1 -i] = t;  
        }
        System.out.println(s);
    }
}
```



<h1> LeetCode soln </h1>


```java
class Solution {
    public void reverseString(char[] s) {
        for(int i = 0; i < s.length / 2; i++){
            int j = s.length - i - 1;
            char first = s[i];
            char last = s[j];
            s[j] = first;
            s[i] = last;
        }
    }
}
```
