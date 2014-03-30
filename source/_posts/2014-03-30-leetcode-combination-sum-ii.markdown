---
layout: post
title: "[leetcode] Combination Sum II"
date: 2014-03-30 15:44:39 -0400
comments: true
categories: 
- leetcode
- coding
- sum
---
###Algorithm:
This problem (P2) is similar to [Combination Sum](http://xiaochenchen.github.io/blog/2014/03/30/leetcode-combination-sum/)(P1) yet quite different.
1. P1 allows to use on element multiple times while P2 does not.
2. P1 has unique elements and P2 allows duplicates

Same recursion solution with the following difference:
1. When making recursive calls, set the `startIndex` to i + 1 instead i
2. Discard duplicates after `startIndex` in the loop

``` java Combination Sum II http://oj.leetcode.com/problems/combination-sum-ii/ Leetcode Link
/**
 * Given a collection of candidate numbers (C) and a target number (T),
 * find all unique combinations in C where the candidate numbers sums to T.
 * Each number in C may only be used once in the combination.
 * Note:
 * All numbers (including target) will be positive integers.
 * Elements in a combination (a1, a2, ... , ak) must be in non-descending order.
 * (ie, a1 <= a2 <= ... <= ak).
 * The solution set must not contain duplicate combinations.
 *
 * For example, given candidate set 10,1,2,7,6,1,5 and target 8,
 * A solution set is:
 * [1, 7]
 * [1, 2, 5]
 * [2, 6]
 * [1, 1, 6]
 *
 * Created by lightsaber on 3/30/14.
 */
public class CombinationSumII
{
    public ArrayList<ArrayList<Integer>> combinationSum2(int[] num, int target)
    {
        ArrayList<ArrayList<Integer>> results = new ArrayList<ArrayList<Integer>>();
        ArrayList<Integer> result = new ArrayList<Integer>();

        // sort input array so that the results combination will be in non-descending order
        Arrays.sort(num);

        generate(num, results, result, 0, 0, target);

        return results;
    }

    public void generate(int[] num, ArrayList<ArrayList<Integer>> results,
                         ArrayList<Integer> result, int startIndex, int currSum, int target)
    {
        if(currSum == target)
        {
            // found a valid combination
            results.add(new ArrayList<Integer>(result));
            return;
        }
        else if(currSum > target)
        {
            return;
        }

        for(int i = startIndex; i < num.length; ++i)
        {
            // in this loop, we are taking one of the numbers after startIndex (inclusive)
            // skip duplicates after startIndex
            if(i > startIndex && num[i] == num[i - 1])
            {
                continue;
            }

            result.add(num[i]);
            generate(num, results, result, i + 1, currSum + num[i], target);
            result.remove(result.size() - 1);
        }
    }
}
```
