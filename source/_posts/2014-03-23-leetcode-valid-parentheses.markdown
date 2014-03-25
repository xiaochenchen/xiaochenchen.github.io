---
layout: post
title: "[leetcode] Valid Parentheses"
date: 2014-03-23 22:19:46 -0400
comments: true
categories:
- leetcode
- coding
- stack
---
Scan through the string, if left parenthesis is encountered, push into stack, if right parenthesis is encountered, match with the top element from the stack.
``` java Valid Parentheses http://oj.leetcode.com/problems/valid-parentheses/ Leetcode Link
/**
 * Valid Parentheses
 *
 * Given a string containing just the characters '(', ')', '{', '}', '[' and ']',
 * determine if the input string is valid. The brackets must close in the correct order,
 * "()" and "()[]{}" are all valid but "(]" and "([)]" are not.
 *
 * Created by lightsaber on 3/23/14.
 */
public class ValidParentheses
{
    public boolean isValid(String s) {
        Stack<Character> leftParentheses = new Stack<Character>();
        for(char c : s.toCharArray())
        {
            // if left parenthesis, push into stack, continue to next char
            if(c == '(' || c == '[' || c == '{')
            {
                leftParentheses.push(c);
                continue;
            }

            // if stack empty, return false
            if(leftParentheses.isEmpty())
            {
                return false;
            }

            // check if the top of stack matches with current char
            char topOfStack = leftParentheses.pop();
            if( !((c == ')' && topOfStack == '(')
                        || (c == ']') && topOfStack == '['
                        || (c == '}') && topOfStack == '{') )
            {
                return false;
            }
        }

        // if nothing left in the stack, return true
        if(leftParentheses.isEmpty())
        {
            return true;
        }
        else
        {
            return false;
        }
    }
}
```
