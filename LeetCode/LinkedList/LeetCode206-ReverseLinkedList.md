# 一、ReverseLinkedList

## 1、问题

Reverse a singly linked list.

**Example**:

```
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```

**Follow up**:

A linked list can be reversed either iteratively or recursively. Could you implement both?

## 2、分析

## 3、代码

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if (!head) return head;
        
        ListNode *dummy = new ListNode(-1);
        ListNode *cur = dummy;
        ListNode *tmp = NULL;
        
        while (head)
        {
            tmp = head;
            head = head->next;
            tmp->next = cur;
            cur = tmp;
        }
        
        tmp = cur;
        while (tmp->next->next)
            tmp = tmp->next;
        tmp->next = NULL;
        
        return cur;
        
    }
};
```

## 4、语言相关

---
