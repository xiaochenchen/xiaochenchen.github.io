---
layout: post
title: "[leetcode] Permutations"
date: 2014-03-30 23:07:46 -0400
comments: true
categories:
- leetcode
- coding
- permutation 
---
###Algorithm:
Classic recursion problem. 
Use boolean array `visited[]` to track which element has been visited so far.
``` java Permutations http://oj.leetcode.com/problems/permutations/ Leetcode Link
/**
 * Given a collection of numbers, return all possible permutations.
 *
 *  For example,
 *      [1,2,3] have the following permutations:
 *      [1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], and [3,2,1].
 *
 * Created by lightsaber on 3/30/14.
 */
public class Permutations
{
    public ArrayList<ArrayList<Integer>> permute(int[] num)
    {
        // final results
        ArrayList<ArrayList<Integer>> results = new ArrayList<ArrayList<Integer>>();

        // intermediate result used for recursion
        ArrayList<Integer> result = new ArrayList<Integer>();

        // used to track which number has been visited
        boolean[] visited = new boolean[num.length];

        generate(num, results, result, visited);

        return results;
    }

    public void generate(int[] num, ArrayList<ArrayList<Integer>> results, ArrayList<Integer> result, boolean[] visited)
    {
        if(result.size() == num.length)
        {
            results.add(new ArrayList<Integer>(result));
            return;
        }

        for(int i = 0; i < num.length; ++i)
        {
            if(!visited[i])
            {
                result.add(num[i]);
                visited[i] = true;

                generate(num, results, result, visited);

                result.remove(result.size() - 1);
                visited[i] = false;
            }
        }
    }
}
```
