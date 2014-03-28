---
layout: post
title: "[leetcode] Reverse Nodes in K Group"
date: 2014-03-27 22:03:43 -0400
comments: true
categories: 
- leetcode
- coding
- linked list
---
Algorithm
============
This question is similar to [Swap Nodes in Pairs](http://xiaochenchen.github.io/blog/2014/03/27/leetcode-swap-nodes-in-pairs/) in that we need to keep track of the Node before the K group, we call it `pre` reference. When we are done with the K group, we need to change pre to point to the Begin of this K group.

In order to reverse K group, we keep track of the beginning `kBegin` and ending `kEnd` of currently reversed nodes. When processing for next node, we move `kEnd` to point to its next, insert itself before `kBegin`, and update `kBegin`. Until we reserverd K nodes.
``` java Reverse Nodes in K Group http://oj.leetcode.com/problems/reverse-nodes-in-k-group/ Leetcode Link
/**
 * Given a linked list, reverse the nodes of the
 * linked list k at a time and return its modified list.
 * If the number of nodes is not a multiple of k
 * then left-out nodes in the end should remain as it is.
 * You may not alter the values in the nodes, only nodes itself may be changed.
 *
 * Only constant memory is allowed.
 *
 * For example,
 * Given this linked list: 1->2->3->4->5
 * For k = 2, you should return: 2->1->4->3->5
 * For k = 3, you should return: 3->2->1->4->5
 *
 * Created by lightsaber on 3/27/14.
 */
public class ReverseNodesInKGroup
{
    // Definition for singly-linked list.
    public class ListNode {
        int val;
        ListNode next;

        ListNode(int x) {
            val = x;
            next = null;
        }
    }

    public ListNode reverseKGroup(ListNode head, int k) {

        ListNode dummyHead = new ListNode(Integer.MIN_VALUE);
        dummyHead.next = head;

        ListNode pre = dummyHead;
        ListNode kBegin = head;
        ListNode kEnd = head;

        while(hasAtLeastKNodes(kBegin, k))
        {
            int count = 1;

            while(count < k)
            {
                ListNode temp = kEnd.next.next;
                kEnd.next.next = kBegin;
                kBegin = kEnd.next;
                kEnd.next = temp;
                count++;
            }

            // set the references for next k nodes
            pre.next = kBegin;
            pre = kEnd;
            kBegin = pre.next;
            kEnd = pre.next;
        }

        return dummyHead.next;
    }

    // utility function to check if there are at least k nodes from head
    public boolean hasAtLeastKNodes(ListNode head, int k)
    {
        int count = 0;

        ListNode curr = head;
        while(curr != null)
        {
            count++;
            if(count == k)
            {
                return true;
            }
            curr = curr.next;
        }

        return false;
    }
}
```
