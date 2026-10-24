# Linked List Problems:

---
## Add Two Numbers(2.Leetcode):

<P>
  Difficulty: Medium 

  You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example 1: 

<img width="483" height="342" alt="image" src="https://github.com/user-attachments/assets/0a538e87-0c8d-42ba-ae8b-8b8ef4bc741c" />

Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

Example 2: 

Input: l1 = [0], l2 = [0]
Output: [0]


Example 3:

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]

 Constraints:

The number of nodes in each linked list is in the range [1, 100].
0 <= Node.val <= 9
It is guaranteed that the list represents a number that does not have leading zeros.

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummyHead = new ListNode(-1);
        ListNode* curr = dummyHead;
        ListNode* temp1 = l1;
        ListNode* temp2 = l2;
        int carry = 0;
        while(temp1 != NULL || temp2 != NULL){
            int sum = carry;
            if(temp1) sum += temp1->val;
            if(temp2) sum += temp2->val;
            ListNode* newNode = new ListNode(sum % 10);
            carry = sum/10;

            curr->next = newNode;
            curr = curr->next;

            if(temp1) temp1 = temp1->next;
            if(temp2) temp2 = temp2->next;
        }

        if(carry){
            ListNode* newNode = new ListNode(carry);
            curr->next = newNode;
        }

        return dummyHead->next;
    }
};
```
---
## Odd Even Linkedlist (328. Leetcode): 

<P>
  Difficulty: Medium 

  Given the head of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return the reordered list.

The first node is considered odd, and the second node is even, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in O(1) extra space complexity and O(n) time complexity.

Example 1:

<img width="542" height="222" alt="image" src="https://github.com/user-attachments/assets/9bdb0db6-42b9-4ca4-9f3a-4632fa67e998" />


Input: head = [1,2,3,4,5]
Output: [1,3,5,2,4]

Example 2:


<img width="782" height="222" alt="image" src="https://github.com/user-attachments/assets/26ec4bde-902d-403f-b5ab-6c964c830cce" />

Input: head = [2,1,3,5,6,4,7]
Output: [2,3,6,7,1,5,4]
 

Constraints:

The number of nodes in the linked list is in the range [0, 104].
-106 <= Node.val <= 106
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
    ListNode* oddEvenList(ListNode* head) {
        if (head == NULL || head->next == NULL) {
            return head;
        }

        ListNode* odd = head;
        ListNode* even = head->next;
        ListNode* evenHead = head->next;

        while (even != NULL && even->next != NULL) {
            odd->next = even->next;
            even->next = even->next->next;

            odd = odd->next;
            even = even->next;
        }

        odd->next = evenHead;

        return head;
    }
};

```
---
## Sort Llinked List of 0s, 1s and 2s (Geeks For Geeks): 

<P>
  Difficulty : Medium 

  Given a linked list where nodes can contain values 0s, 1s, and 2s only. Your task is to rearrange the list so that all 0s appear at the beginning, followed by all 1s, and all 2s are placed at the end.

Examples:


Input: head = 1 → 2 → 2 → 1 → 2 → 0 → 2 → 2

<img width="1000" height="97" alt="image" src="https://github.com/user-attachments/assets/2abb366a-df9c-46e2-9256-8ad361037266" />

   
Output: 0 → 1 → 1 → 2 → 2 → 2 → 2 → 2

<img width="1000" height="97" alt="image" src="https://github.com/user-attachments/assets/c2432e89-cd91-4ebc-8d0b-a623ba9918c9" />

Explanation: All the 0s are segregated to the left end of the linked list, 2s to the right end of the list, and 1s in between. The final list will be:
   
Input: head = 2 → 2 → 0 → 1

<img width="591" height="97" alt="image" src="https://github.com/user-attachments/assets/6ed5efaf-2e41-4dfe-972a-04836b081548" />

   
Output: 0 → 1 → 2 → 2

<img width="591" height="97" alt="image" src="https://github.com/user-attachments/assets/5f19a051-3873-406c-98ec-0a5f7256a720" />

Explanation: After arranging all the 0s, 1s and 2s in the given format, the output will be:
   
Constraints:

1 ≤ size of linked list ≤ 106
0 ≤ node.data ≤ 2

</P>

### Solution: 

```
/* Node is defined as
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
    Node* segregate(Node* head) {
        // code here
        if(head == NULL || head->next == NULL) return head;
        
        Node* zeroHead = new Node(-1);
        Node* oneHead = new Node(-1);
        Node* twoHead = new Node(-1);
        
        Node *zero = zeroHead;
        Node *one = oneHead;
        Node *two = twoHead;
        Node *temp = head;
        
        while(temp){
            if(temp->data == 0){
                zero->next = temp;
                zero = zero->next;
            }
            else if(temp->data == 1){
                one->next = temp;
                one = one->next;
            }
            else{
                two->next = temp;
                two = two->next;
            }
            temp = temp->next;
        }
        
        zero->next = (oneHead->next) ? (oneHead->next) : (twoHead->next);
        one->next = twoHead->next;
        two->next = NULL;
        
        Node* newHead = zeroHead->next;
        
        delete zeroHead;
        delete oneHead;
        delete twoHead;
        
        return newHead;
    }
};
```
---
## Remove Nth Node From End Of Linked List (19. Leetcode): 

<P>
  Difficulty: Medium 

  Given the head of a linked list, remove the nth node from the end of the list and return its head.

 

Example 1:

<img width="542" height="222" alt="image" src="https://github.com/user-attachments/assets/2551065b-e4e0-40c1-9695-a85a8f8e0f09" />

Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
Example 2:

Input: head = [1], n = 1
Output: []
Example 3:

Input: head = [1,2], n = 1
Output: [1]
 

Constraints:

The number of nodes in the list is sz.
1 <= sz <= 30
0 <= Node.val <= 100
1 <= n <= sz
 
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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* fast = head;
        ListNode* slow = head;
        for(int i = 0; i<n; i++){
            fast = fast->next;
        }
        if(fast == NULL){
            ListNode* newHead = head->next;
            delete head;
            return newHead;
        }
        while(fast->next != NULL){ 
            fast = fast->next;
            slow = slow->next;
        }
        ListNode* delNode = slow->next;
        slow->next = slow->next->next;
        delete delNode;
        return head;
    }
};
```
---
## Reverse Linked List (206. Leetcode): 

<P>
  Difficulty: Easy 

  Given the head of a singly linked list, reverse the list, and return the reversed list.

 

Example 1:
<img width="542" height="222" alt="image" src="https://github.com/user-attachments/assets/6a1963a7-a3dc-4426-84c4-874da65a4093" />


Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
Example 2:

<img width="182" height="222" alt="image" src="https://github.com/user-attachments/assets/7662b838-c931-4c0c-be13-e04cec9ea8af" />

Input: head = [1,2]
Output: [2,1]
Example 3:

Input: head = []
Output: []
 

Constraints:

The number of nodes in the list is the range [0, 5000].
-5000 <= Node.val <= 5000
</P>

### Solution (Iterative Solution): 

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
    ListNode* reverseList(ListNode* head) {
        ListNode* temp = head;
        ListNode* prev = NULL;
        while(temp != NULL){
            ListNode* front = temp->next;
            temp->next = prev;
            prev = temp;
            temp = front;
        }
        return prev;
    }
};
```

### Solution(Recursive Solution): 

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
    ListNode* reverseList(ListNode* head) {
        if(head == NULL || head->next == NULL){
            return head;
        }
        ListNode* newHead = reverseList(head->next);
        ListNode* front = head->next;
        front->next = head;
        head->next = NULL;
        return newHead;
    }
};
```
---
