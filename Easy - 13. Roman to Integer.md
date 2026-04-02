
Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

**Symbol**       **Value**
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

For example, `2` is written as `II` in Roman numeral, just two ones added together. `12` is written as `XII`, which is simply `X + II`. The number `27` is written as `XXVII`, which is `XX + V + II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9. 
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90. 
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer.

**Example 1:**

**Input:** s = "III"
**Output:** 3
**Explanation:** III = 3.

**Example 2:**

**Input:** s = "LVIII"
**Output:** 58
**Explanation:** L = 50, V= 5, III = 3.

**Example 3:**

**Input:** s = "MCMXCIV"
**Output:** 1994
**Explanation:** M = 1000, CM = 900, XC = 90 and IV = 4.

**Constraints:**

- `1 <= s.length <= 15`
- `s` contains only the characters `('I', 'V', 'X', 'L', 'C', 'D', 'M')`.
- It is **guaranteed** that `s` is a valid roman numeral in the range `[1, 3999]`.
<h1> Solution </h1>

```java
class Solution {
    public int romanToInt(String s) {
        int sum = 0;
        for (int i = s.length()-1; i >= 0; i--)
        {
            System.out.println("index value from loop"+ i);
            if(s.charAt(i) == 'I')
            {
                sum+=1;
                System.out.println("Value added 1");
            }
            if(s.charAt(i) == 'V')
            {
                sum+=5;
            System.out.println("Value added 5");
                if( i > 0 && s.charAt(i-1) == 'I' )
                {
                    sum = sum -1;
                    i = i -  1;
                    System.out.println("Value subtracted 1");
                }
            }
            if(s.charAt(i) == 'X')
            {
                sum+=10;
                System.out.println("Value added 10");
                if( i > 0 && s.charAt(i-1) == 'I')
                {
                    sum = sum -1;
                    i = i -  1;
                    System.out.println("Value subtracted 1");
                }
            }
            if(s.charAt(i) == 'L')
            {
                sum+=50;
                System.out.println("Value added 50");
                if( i > 0 && s.charAt(i-1) == 'X' )
                {
                    sum = sum -10;
                    i = i -  1;
                    System.out.println("Value subtracted 10");
                }
            }
            if(s.charAt(i) == 'C')
            {
                sum+=100;
                System.out.println("Value added 100");
                if( i > 0 && s.charAt(i-1) == 'X' )
                {
                    sum = sum -10;
                    i = i -  1;
                    System.out.println("Value subtracted 10");
                }
            }
            if(s.charAt(i) == 'D')
            {
                sum+=500;
                System.out.println("Value added 500");
                if( i > 0 && s.charAt(i-1) == 'C' )
                {
                    sum = sum -100;
                    i = i -  1;
                    System.out.println("Value subtracted 100");
                }
            }
            if(s.charAt(i) == 'M')
            {
                sum+=1000;
                System.out.println("Value added 1000");
                if( i > 0 && s.charAt(i-1) == 'C')
                {
                    sum = sum -100;
                    i = i -  1;
                    System.out.println("Value subtracted 100");
                }
            }
        }
    return sum;
    }
}
```

<h1> LeetCode solution </h1>

```java
class Solution {
    public int romanToInt(String s) {
        int res = 0;
        Map<Character, Integer> roman = new HashMap<>();
        roman.put('I', 1);
        roman.put('V', 5);
        roman.put('X', 10);
        roman.put('L', 50);
        roman.put('C', 100);
        roman.put('D', 500);
        roman.put('M', 1000);

        for (int i = 0; i < s.length() - 1; i++) {
            if (roman.get(s.charAt(i)) < roman.get(s.charAt(i + 1))) {
                res -= roman.get(s.charAt(i));
            } else {
                res += roman.get(s.charAt(i));
            }
        }

        return res + roman.get(s.charAt(s.length() - 1));        
    }
}
```
