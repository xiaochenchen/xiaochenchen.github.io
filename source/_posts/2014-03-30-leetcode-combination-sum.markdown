---
layout: post
title: "[leetcode] Combination Sum"
date: 2014-03-30 14:51:10 -0400
comments: true
categories:
- leetcode
- coding
- sum
---
###Algorithm:
Recursive solution.
``` java Combination Sum http://oj.leetcode.com/problems/combination-sum Leetcode Link
/**
 * Given a set of candidate numbers (C) and a target number (T),
 * find all unique combinations in C where the candidate numbers sums to T.
 * The same repeated number may be chosen from C unlimited number of times.
 *
 * Note:
 * All numbers (including target) will be positive integers.
 * Elements in a combination (a1, a2, ... , ak)
 * must be in non-descending order. (ie, a1 <= a2 <= ... <= ak).
 * The solution set must not contain duplicate combinations.
 *
 * For example, given candidate set 2,3,6,7 and target 7,
 *
 * A solution set is:
 * [7]
 * [2, 2, 3]
 *
 * Created by lightsaber on 3/29/14.
 */
public class CombinationSum
{
    public ArrayList<ArrayList<Integer>> combinationSum(int[] candidates, int target)
    {
        ArrayList<ArrayList<Integer>> results = new ArrayList<ArrayList<Integer>>();
        ArrayList<Integer> result = new ArrayList<Integer>();

        Arrays.sort(candidates);

        generate(candidates, results, result, 0, 0, target);

        return results;
    }

    public void generate(int[] candidates, ArrayList<ArrayList<Integer>> results,
                         ArrayList<Integer> result, int startIndex, int currSum, int target)
    {
        // found a valid combination
        if(currSum == target)
        {
            results.add(new ArrayList<Integer>(result));
            return;
        }
        // currSum is greater than target, stop right here
        else if(currSum > target)
        {
            return;
        }

        for(int i = startIndex; i < candidates.length; ++i)
        {
            result.add(candidates[i]);
            generate(candidates, results, result, i, currSum + candidates[i], target);
            result.remove(result.size() - 1);
        }
    }
}
```
