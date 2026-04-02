Given an integer `x`, return `true` _if_ `x` _is a_ _**palindrome**__, and_ `false` _otherwise_.

**Example 1:**

**Input:** x = 121
**Output:** true
**Explanation:** 121 reads as 121 from left to right and from right to left.

**Example 2:**

**Input:** x = -121
**Output:** false
**Explanation:** From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.

**Example 3:**

**Input:** x = 10
**Output:** false
**Explanation:** Reads 01 from right to left. Therefore it is not a palindrome.

**Constraints:**

- `-231 <= x <= 231 - 1`

**Follow up:** Could you solve it without converting the integer to a string?

<h1>Solution1</h1>
```java
class Solution {
    public boolean isPalindrome(int x) {
        String numStr = String.valueOf(x);
        System.out.println(numStr.length());
        for (int i = 0; i < numStr.length()/2; i++)
        {
            System.out.println("value at i : " + numStr.charAt(i));
            System.out.println("value at i : " + numStr.charAt(numStr.length()-1 - i));
            if(numStr.charAt(i) != numStr.charAt(numStr.length()-1-i))
            {
                return false;
            }
        }
        return true;
    }
}
```

<h1>Solution 2</h1>
```java
class Solution {
    public boolean isPalindrome(int x) {
        String numStr = String.valueOf(x);
        StringBuilder strbuild = new StringBuilder(numStr);
        return strbuild.reverse().toString().equals(numStr);
    }
}
```

<h1> Leetcode solution </h1>

```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x<0 || (x!=0 && x%10==0)) return false;
        int rev = 0;
        while (x>rev){
            rev = rev*10 + x%10;
            x = x/10;
        }
        return (x==rev || x==rev/10);
    }
}

```
