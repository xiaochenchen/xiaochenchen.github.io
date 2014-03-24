---
layout: post
title: "[leetcode] Longest Common Prefix"
date: 2014-03-23 15:36:43 -0400
comments: true
categories:
- leetcode
- coding
- brute force
---
``` java Longest Common Prefix http://oj.leetcode.com/problems/longest-common-prefix/ Leetcode Link
/**
 * Write a function to find the longest common prefix string amongst an array of strings.
 *
 * Solution:
 *  start from the first char in first string, check if it in all other strings, if not, return
 *
 */
public class LongestCommonPrefix
{
    public String longestCommonPrefix(String[] strs)
    {
        // if null input or empty input, return empty string
        if(strs == null || strs.length == 0)
        {
            return "";
        }

        StringBuilder result = new StringBuilder();

        for(int i = 0; i < strs[0].length(); ++i)
        {
            for(int j = 1; j < strs.length; ++j)
            {
                // if the current char in strs[0] doesn't exist in any following str
                if(strs[j].length() <= i || strs[0].charAt(i) != strs[j].charAt(i))
                {
                    // return current common prefix result
                    return result.toString();
                }
            }
            // if the current char exists in all other strs, append it to common prefix
            result.append(strs[0].charAt(i));
        }

        // if all chars in strs[0] are prefix in other strs, return strs[0]
        return result.toString();
    }
}
```
