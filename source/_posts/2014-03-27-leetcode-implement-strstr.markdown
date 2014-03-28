---
layout: post
title: "[leetcode] Implement strStr()"
date: 2014-03-27 22:47:45 -0400
comments: true
categories:
- leetcode
- coding
- string
---
###Algorithm
brute force, stop matching when the remaining string in source is shorter than target
There is KMP algorithm, if you are interested. Not implementing here.
``` java Implement strStr() http://oj.leetcode.com/problems/implement-strstr/ Leetcode Link
/**
 *
 * Implement strStr().
 * Returns a pointer to the first occurrence of needle in haystack,
 * or null if needle is not part of haystack.
 *
 * Created by lightsaber on 3/27/14.
 */
public class StrStr
{
    public String strStr(String haystack, String needle) {
        for(int i = 0; i <= haystack.length() - needle.length(); ++i)
        {
            if(haystack.substring(i, i + needle.length()).equals(needle))
            {
                return haystack.substring(i);
            }
        }

        return null;
    }
}
```
