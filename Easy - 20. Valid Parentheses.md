Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
 
Example 1:
Input: s = "()"
Output: true
Example 2:
Input: s = "()[]{}"
Output: true
Example 3:
Input: s = "(]"
Output: false
Example 4:
Input: s = "([])"
Output: true
Example 5:
Input: s = "([)]"
Output: false

Constraints:
1 <= s.length <= 104
s consists of parentheses only '()[]{}'.

<h1> Solution </h1>

```java

class Solution {
    public boolean isValid(String s) {
        ArrayList<Character> openBraces = new ArrayList<>();
        if (s.length() %2 != 0)
        {
            System.out.println("returning from 1");
            return false;
        }
        else
        {
            for (int i = 0; i < s.length() ; i++)
            {
                System.out.println("processing" + s.charAt(i));
                if((s.charAt(i) == '{') || (s.charAt(i) == '(') || (s.charAt(i) == '['))
                {
                    openBraces.add(s.charAt(i));
                    System.out.println("added : "+ s.charAt(i));
                }
                else
                {
                    int remove = 0;
                    if(openBraces.size() > 0)
                    {
                        if((s.charAt(i) == '}') && (openBraces.get(openBraces.size() - 1) == '{'))
                        {
                            System.out.println("remove from 1");
                            remove = 1;
                            // openBraces.remove(openBraces.size()-1);
                        }
                        if((s.charAt(i) == ')') && (openBraces.get(openBraces.size() - 1) == '('))
                        {
                            System.out.println("remove from 2");
                            remove = 1;
                            // openBraces.remove(openBraces.size()-1);
                        }
                        if((s.charAt(i) == ']') && (openBraces.get(openBraces.size() - 1) == '['))
                        {
                            System.out.println("remove from 3");
                            remove = 1;
                            // openBraces.remove(openBraces.size()-1);
                        }
                        if(remove != 0)
                        {
                            openBraces.remove(openBraces.size()-1);
                        }
                        else
                        {
                            System.out.println("returning from 5");
                            return false;
                        }
                    }
                    else
                    {
                        System.out.println("returning from 6");
                        return false;
                    }
                }
            }
        }
        if(openBraces.size() == 0)
        {
            return true;
        }
        return false;
    }
}
```

<h1> Leetcode solution </h1>

```java

class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        Map<Character, Character> mapping = new HashMap<>();
        mapping.put(')', '(');
        mapping.put('}', '{');
        mapping.put(']', '[');

        for (char c : s.toCharArray()) {
            if (mapping.containsValue(c)) {
                stack.push(c);
            } else if (mapping.containsKey(c)) {
                if (stack.isEmpty() || mapping.get(c) != stack.pop()) {
                    return false;
                }
            }
        }
        return stack.isEmpty();        
    }
}
```
