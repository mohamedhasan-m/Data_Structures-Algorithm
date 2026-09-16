# Linked List Introduction and Oprations on 1D LinkedList: 
---
## Search in a Linked List (Geeks For Geeks): 

<P>

  Difficulty: Basic

  
  Given a linked list with the head node and a key, the task is to check if the key is present in the linked list or not. 

Example:

<img width="730" height="97" alt="image" src="https://github.com/user-attachments/assets/a540e00b-71f7-4ed5-b0ce-889255f926f3" />


Input: key = 3,
      
Output: true 
Explanation: 3 is present in Linked List.

<img width="641" height="98" alt="image" src="https://github.com/user-attachments/assets/a0068019-302d-499e-8fe0-af6b4dff16ba" />

Input: key = 4,
   
Output: false
Explanation: 4 is not present in Linked List.
Constraints:

1 ≤ size of linked list, key ≤ 105

</P>

### Solution: 

```
/* Structure of Linked List Node
class Node {
  public:
    int data;
    Node* next;

    Node(int x) {
        data = x;
        next = nullptr;
    }
}; */

class Solution {
  public:
    bool searchKey(Node* head, int key) {
        // Code here
        Node* temp = head;
        while(temp){
            if(temp->data == key) return 1;
            temp = temp->next;
        }
        return 0;
    }
};

```
---

## Length of Linked List (Geeks For Geeks): 

<P>
  Difficulty: Easy

  Given head of a singly linked list. Find the length of the linked list, where length is defined as the number of nodes in the linked list.

Examples :

<img width="603" height="91" alt="image" src="https://github.com/user-attachments/assets/ad1d784b-2c45-42fd-b521-44229f8c7793" />


Input: head: 1 -> 2 -> 3 -> 4 -> 5

Output: 5
Explanation: Length of the linked list is 5, as there are 5 nodes present in it.

<img width="778" height="91" alt="image" src="https://github.com/user-attachments/assets/a874f80c-5c77-482a-977c-c77658a72a36" />

Input: head: 2 -> 4 -> 6 -> 7 -> 5 -> 1 -> 0
 
Output: 7
Explanation: Length of the linked list is 7, as there are 7 nodes present in it.
Constraints:

1 ≤ size of linked list ≤ 4*104
1 ≤ node.data ≤ 103
</P>

### Solution

```
/* Structure of linked list Node
class Node {
  public:
    int data;
    Node *next;

    Node(int x) {
        data = x;
        next = nullptr;
    }
};
*/
class Solution {
  public:
    int getCount(Node* head) {
        // Code here
        int cnt = 0;
        Node* temp = head;
        while(temp){
            temp = temp->next;
            cnt++;
        }
        return cnt;
    }
};
```
---
