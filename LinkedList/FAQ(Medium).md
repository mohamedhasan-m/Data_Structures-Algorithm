# Frequentely Asked Questions (Medium): 

---

## Middle of the Linkedlist (876.Leetcode):
<P>
  Difficulty: Easy

  Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.

 

Example 1:
<img width="544" height="65" alt="image" src="https://github.com/user-attachments/assets/cf64b035-4885-4bc2-89dd-1d86c31790b2" />


Input: head = [1,2,3,4,5]
Output: [3,4,5]
Explanation: The middle node of the list is node 3.
Example 2:

<img width="664" height="65" alt="image" src="https://github.com/user-attachments/assets/81cf9445-eac1-4169-aac0-779c5f28ec0a" />

Input: head = [1,2,3,4,5,6]
Output: [4,5,6]
Explanation: Since the list has two middle nodes with values 3 and 4, we return the second one.
 

Constraints:

The number of nodes in the list is in the range [1, 100].
1 <= Node.val <= 100
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
    ListNode* middleNode(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast != NULL && fast->next != NULL){
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;
    }
};
```
---

## Palindrome Linked list(234. Leetcode): 

<P>
  Difficulty: Easy

  Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

 

Example 1:
<img width="422" height="62" alt="image" src="https://github.com/user-attachments/assets/08c58720-fb56-47e6-b2a9-f9938bc8a871" />


Input: head = [1,2,2,1]
Output: true
Example 2:

<img width="182" height="62" alt="image" src="https://github.com/user-attachments/assets/b294e538-d289-4116-a5a6-f7741a5433be" />

Input: head = [1,2]
Output: false
 

Constraints:

The number of nodes in the list is in the range [1, 105].
0 <= Node.val <= 9
 

Follow up: Could you do it in O(n) time and O(1) space?
  
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
    ListNode* reverseLinkedList(ListNode* head){
        if(head == NULL || head->next == NULL) return head;
        ListNode* newHead = reverseLinkedList(head->next);
        ListNode* front = head->next;
        front->next = head;
        head->next = NULL;
        return newHead;
    }
    bool isPalindrome(ListNode* head) {
        if(head == NULL || head->next == NULL) return true;
        ListNode* slow = head;
        ListNode* fast = head;
        while(fast->next != NULL && fast->next->next != NULL){
            slow = slow->next;
            fast = fast->next->next;
        } 
        ListNode* newHead = reverseLinkedList(slow->next);
        ListNode* first = head;
        ListNode* second = newHead;
        while(second != NULL){
            if(first->val != second->val){
                reverseLinkedList(newHead);
                return false;
            }
            first = first->next;
            second = second->next;
        }
        reverseLinkedList(newHead);
        return true;
    }
};
```
---
