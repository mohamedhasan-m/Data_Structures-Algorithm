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
## Add 1 to a Linked list (Geeks For Geeks): 

<p>
  Difficulty: Medium 

  You are given head of a linked list where each node contains a single digit. The digits together represent a number formed by concatenating the node values in order. Add 1 to this number and return the head of the modified linked list.

Examples :
<img width="400" height="244" alt="image" src="https://github.com/user-attachments/assets/4359765d-7252-4ebd-a607-dfc9d6089080" />

Input: Head: 4->5->6
Output: 457

Explanation: 4->5->6 represents 456 and when 1 is added it becomes 457. 

<img width="400" height="244" alt="image" src="https://github.com/user-attachments/assets/eb061efd-1dfd-42c8-88af-d9dd60e866d5" />


Input: Head: 1->2->3
Output: 124
 
Explanation:  1->2->3 represents 123 and when 1 is added it becomes 124. 


Input: Head: 0->0->1
Output: 002
Constraints:

1 ≤ size of linked list ≤ 105
0 ≤ node.data ≤ 9
</p>

### Solution: 

```
/* Structure of linked list Node
class Node {
public:
    int data;
    Node* next;

    Node(int x) {
        data = x;
        next = nullptr;
    }
};
*/
class Solution {
  public:
    int addHelper(Node* temp){
        if(temp == NULL){
            return 1;
        }
        int carry = addHelper(temp->next);
        temp->data += carry;
        if(temp->data <10) return 0;
        temp->data = 0;
        return 1;
    }
    Node* addOne(Node* head) {
        // code here
        int carry = addHelper(head);
        if(carry == 1){
            Node* newNode = new Node(1);
            newNode->next = head;
            head = newNode;
        }
        return head;
    }
};
```
---
