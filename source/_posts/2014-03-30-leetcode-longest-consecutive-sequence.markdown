---
layout: post
title: "[leetcode] Longest Consecutive Sequence"
date: 2014-03-30 14:23:31 -0400
comments: true
categories:
- leetcode
- coding
- array
---
###Algorithm:
Store all elements in an HashSet H.
Start scaning the array, for each element i in the array, if i is in H, check whether i-1 is in H, if yes, remove i-1 from H, continue to check i - 2 and not found in H. Do the same thing from i to its right. Keep track of current max length. Return max length at the end.
``` java Longest Consecutive Sequence http://oj.leetcode.com/problems/longest-consecutive-sequence/ Leetcode Link
/**
 *
 * Given an unsorted array of integers,
 * find the length of the longest consecutive elements sequence.
 *
 * For example,
 * Given [100, 4, 200, 1, 3, 2],
 * The longest consecutive elements sequence is [1, 2, 3, 4]. Return its length: 4.
 * Your algorithm should run in O(n) complexity.
 *
 * Created by lightsaber on 3/27/14.
 */
public class LongestConsecutiveSequence
{
    public int longestConsecutive(int[] num)
    {
        Set<Integer> numbers = new HashSet<Integer>();
        for(int i : num)
        {
            numbers.add(i);
        }

        int longest = 0;
        for(int i : num)
        {
            if(numbers.contains(i))
            {
                int left = i, right = i;

                while(numbers.contains(left - 1))
                {
                    numbers.remove(--left);
                }

                while(numbers.contains(right + 1))
                {
                    numbers.remove(++right);
                }

                if(right - left + 1 > longest)
                {
                    longest = right - left + 1;
                }
            }
        }

        return longest;
    }
}
```

