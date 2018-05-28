# 一、DeleteNodeInLinkedList

## 1、问题

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function.

## 2、分析

- 单链表无法得到前向信息，所以删除操作通过将欲删除节点后向节点前移实现
- 无法处理无后向节点的情况

## 3、代码

```

class Solution {
public:
    void deleteNode(ListNode* node) {
        if (NULL == node || NULL == node->next)
            return;
        node->val = node->next->val;
        node->next = node->next->next;
    }
};

```

---
