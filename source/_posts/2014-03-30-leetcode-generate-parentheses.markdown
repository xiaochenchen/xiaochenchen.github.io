---
layout: post
title: "[leetcode] Generate Parentheses"
date: 2014-03-30 14:46:33 -0400
comments: true
categories:
- leetcode
- coding
- parentheses
---
###Algorithm:
Recursion, keep track of leftCount and rightCount. Decide to only append left or both.
``` java Generate Parentheses http://oj.leetcode.com/problems/generate-parentheses/ Leetcode Link
/**
 *
 * Given n pairs of parentheses,
 * write a function to generate all combinations of well-formed parentheses.
 *
 *      For example, given n = 3, a solution set is:
 *      "((()))", "(()())", "(())()", "()(())", "()()()"
 *
 * Created by lightsaber on 3/29/14.
 */
public class GenerateParentheses
{
    public ArrayList<String> generateParentheses(int n)
    {
        ArrayList<String> results = new ArrayList<String>();
        StringBuilder sb = new StringBuilder();
        generate(results, sb, n, n);
        return results;
    }

    public void generate(ArrayList<String> results, StringBuilder result, int lc, int rc)
    {
        // end of one combination, add to the result set and return
        if(lc == 0 && rc == 0)
        {
            results.add(result.toString());
            return;
        }

        if(lc > 0)
        {
            result.append("(");
            generate(results, result, lc - 1, rc);
            result.deleteCharAt(result.length() - 1);
        }

        if(lc < rc)
        {
            result.append(")");
            generate(results, result, lc, rc - 1);
            result.deleteCharAt(result.length() - 1);
        }
    }
}
```
