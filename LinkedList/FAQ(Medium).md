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

  
</P>
