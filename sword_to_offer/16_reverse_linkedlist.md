# source
[16 翻转链表](https://github.com/gatieme/CodingInterviews/tree/master/016-%E5%8F%8D%E8%BD%AC%E9%93%BE%E8%A1%A8)

# solution
## 三指针法

```cpp
    ListNode* ReverseList(ListNode* pHead) {
		if (pHead == NULL || pHead->next == NULL)
            return pHead;
        ListNode *pre = pHead;
        ListNode *cur = pHead->next;
        pre->next = NULL;
        while (cur->next!=NULL)
        {
            ListNode *tmp = cur->next;
            cur->next=pre;
            pre = cur;
            cur = tmp;
        }
        cur->next = pre;
        pHead = cur;
        return pHead;
    }

```

## 头插法
```cpp
    ListNode* ReverseList(ListNode* pHead) {
		if (pHead == NULL || pHead->next == NULL)
            return pHead;
        ListNode *cur = pHead->next;
        ListNode *pre = pHead;
        while (cur!=NULL){
            pHead->next = cur->next;
            cur->next = pre;
            pre = cur;
            cur = pHead->next;
        }
        pHead = pre;
        return pHead;
    }
```
