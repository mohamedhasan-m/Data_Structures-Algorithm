# Frequentely Asked Questions (Hard): 

---

## Reverse Nodes in K Group (25. Leetcode): 

<P>
  Difficulty: Hard

  Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.

 

Example 1:
<img width="542" height="222" alt="image" src="https://github.com/user-attachments/assets/a9b76a45-1db7-4db9-8685-527db925f160" />


Input: head = [1,2,3,4,5], k = 2
Output: [2,1,4,3,5]
Example 2:
<img width="542" height="222" alt="image" src="https://github.com/user-attachments/assets/0a44ea84-03ff-451b-a0cd-4a501dd854af" />


Input: head = [1,2,3,4,5], k = 3
Output: [3,2,1,4,5]
 

Constraints:

The number of nodes in the list is n.
1 <= k <= n <= 5000
0 <= Node.val <= 1000
 

Follow-up: Can you solve the problem in O(1) extra memory space?

 

</P>

### Solution: 

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseLinkedList(ListNode* temp){
        ListNode* prev = nullptr;
        ListNode* current = temp;

        while(current != nullptr){
            ListNode* front = current->next;
            current->next = prev;
            prev = current;
            current = front;
        }

        return prev;
    }
    ListNode* getKthNode(ListNode* temp, int k){
        k -= 1;
        while(temp != NULL && k>0){
            k--;
            temp = temp->next;
        }
        return temp;
    }
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* temp = head;
        ListNode* prevLast = NULL;
        while(temp != NULL){
            ListNode* KthNode = getKthNode(temp,k);
            if(KthNode == NULL){
                if(prevLast) prevLast->next = temp;
                break;
            }

            ListNode* nextNode = KthNode->next;
            KthNode->next = NULL;
            reverseLinkedList(temp);
            if(temp == head) {
                head = KthNode;
            }
            else{
                prevLast->next = KthNode;
            }

            prevLast = temp;
            temp = nextNode;
        }
        return head;
    }
};
```
---
## Rotate List (61.Leetcode): 

<P>
  Difficulty: Medium

  Given the head of a linked list, rotate the list to the right by k places.

 

Example 1:
<img width="712" height="302" alt="image" src="https://github.com/user-attachments/assets/370fd7a6-df80-4b55-8dbf-b47836706e8d" />


Input: head = [1,2,3,4,5], k = 2
Output: [4,5,1,2,3]
Example 2:
<img width="472" height="542" alt="image" src="https://github.com/user-attachments/assets/515f6324-c144-4077-8df8-a6135ab007ae" />


Input: head = [0,1,2], k = 4
Output: [2,0,1]
 

Constraints:

The number of nodes in the list is in the range [0, 500].
-100 <= Node.val <= 100
0 <= k <= 2 * 109
</P>

### Solution: 

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* findNthNode(ListNode* temp, int k){
        int cnt = 1;
        while(temp != NULL){
            if(cnt == k){
                return temp;
            }
            cnt ++;
            temp = temp->next;
        }
        return temp;
    }
    ListNode* rotateRight(ListNode* head, int k) {
        if(head == NULL || k==0) return head;
        int len = 1;
        ListNode* tail = head;
        while(tail->next != NULL){
            len++;
            tail = tail->next;
        }
        if(k%len == 0) return head;

        k = k%len;

        tail->next = head;

        ListNode* newLastNode = findNthNode(head,len-k);

        head = newLastNode->next;
        newLastNode->next = NULL;

        return head;
    }
};
```
---
## Merge two Sorted Lists (21. Leetcode):

<P>
  Difficulty: Easy

  You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

 

Example 1:

<img width="662" height="302" alt="image" src="https://github.com/user-attachments/assets/44b21c21-fc23-41e8-8a02-ef9b697ed2f2" />

Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
Example 2:

Input: list1 = [], list2 = []
Output: []
Example 3:

Input: list1 = [], list2 = [0]
Output: [0]
 

Constraints:

The number of nodes in both lists is in the range [0, 50].
-100 <= Node.val <= 100
Both list1 and list2 are sorted in non-decreasing order.
</P>

### Solution: 

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* t1 = list1;
        ListNode* t2 = list2;
        ListNode* dummyNode = new ListNode(-1);
        ListNode* temp = dummyNode;
        while(t1 != NULL && t2 != NULL){
            if(t1->val < t2->val){
                temp->next = t1;
                temp = t1;
                t1 = t1->next;
            }
            else{
                temp->next = t2;
                temp = t2;
                t2 = t2->next;
            }
        }
        if(t1) temp->next = t1;
        else temp->next = t2;
        return dummyNode->next;
    }
};
```
---
