---
layout: post
title: "[leetcode] Remove Nth Node From End of List"
date: 2014-03-23 16:28:30 -0400
comments: true
categories: 
- leetcode
- coding
- linked list
---
> Assumption:
> Given n will always be valid.

####Two things to pay attention to during implementation:
1. add a dummy head pointer to avoid special processing for the case when head is null
2. keep track of the node (call it B) before the target node, check if B.next is null before removing the target node

Also notice that the index start from 1 from the end of the list.
``` java Remove Nth Node From End of List http://oj.leetcode.com/problems/remove-nth-node-from-end-of-list/ Leetcode Link
/**
 * Given a linked list, remove the nth node from the end of list and return its head.
 * For example,
 *  Given linked list: 1->2->3->4->5, and n = 2.
 *  After removing the second node from the end, the linked list becomes 1->2->3->5.
 *
 * Solution:
 *  Start with a A pointer from the head, once A is pointing to Nth node
 *  introduce pointer start from head, move A and B together until A gets to the end
 *  And now remove the node after B.
 *
 */
public class RemoveNthNodeFromEndOfList {

    // Definition for singly-linked list.
    public class ListNode {
        int val;
        ListNode next;

        ListNode(int x) {
            val = x;
            next = null;
        }
    }

    public ListNode removeNthFromEnd(ListNode head, int n)
    {
        // introduce dummy head to ignore the null list input case
        ListNode dummyHead = new ListNode(Integer.MIN_VALUE);
        dummyHead.next = head;

        // A pointer
        ListNode aNode = dummyHead;
        // index of the A pointer
        int aIndex = 0;

        // advance A pointer to N node away from head
        while(aIndex < n && aNode.next != null)
        {
            aNode = aNode.next;
            aIndex++;
        }

        // B pointer
        ListNode bNode = dummyHead;

        // advance A and B at the same time, until A gets the the end
        while(aNode.next != null)
        {
            aNode = aNode.next;
            bNode = bNode.next;
        }

        // remove the Node after B, which is Nth away from the end
        // only when bNode.next is not NULL
        if(bNode.next != null)
        {
            bNode.next = bNode.next.next;
        }

        return dummyHead.next;
    }

}
```
