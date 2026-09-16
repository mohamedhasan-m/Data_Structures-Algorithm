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
## Delete Head of Linked List (geeks for Geeks): 

<P>
  Difficulty: Easy

Given a Linked List, delete the head of the Linked List and return the new head of the modified Linked List.
Note: Set the original head to NULL.

Examples:

Input:

<img width="737" height="97" alt="image" src="https://github.com/user-attachments/assets/ab260097-fcb6-496c-8db2-53ed6884c500" />

   
Output: 2 -> 3 -> 1 -> 7

<img width="629" height="98" alt="image" src="https://github.com/user-attachments/assets/68428378-5747-4c0d-94ff-8dd63024e69f" />

Explanation: After deleting head from the given linked list, we'll be left with just 2 -> 3 -> 1 -> 7.
    
Input:

<img width="833" height="98" alt="image" src="https://github.com/user-attachments/assets/607d70ca-faea-45b7-aebe-eba65813f53e" />

   
Output: 5 -> 7 -> 8 -> 99 -> 100

<img width="737" height="97" alt="image" src="https://github.com/user-attachments/assets/e072ba2e-b77d-45e9-a957-40bf5482c3bc" />

Explanation: After deleting head from the given linked list, we'll be left with just 5 -> 7 -> 8 -> 99 -> 100.
   
Constraints:
1 ≤ number of nodes ≤ 105
1 ≤ node->data ≤ 105

</P>

### Solution: 

```
/*
class Node {
public:
    int data;
    Node* next;

    Node(int x) {
        data = x;
        next = NULL;
    }
};

*/
class Solution {
  public:
    Node *deleteHead(Node *head) {
        // code here
        if(head == NULL) return head;
        Node* temp = head;
        head = head->next;
        free(temp);
        return head;
    }
};
```
---

## Linked List Insertion at the Beginnning (Geeks For Geeks): 

  <P>
  Difficulty: Easy

  You are given the head of a Singly Linked List and a value x, insert that value x at the beginning of the LinkedList and return the head of the modified Linked List.

Examples :

<img width="413" height="97" alt="image" src="https://github.com/user-attachments/assets/fd67eafd-e0a6-4488-8809-d76689585ae9" />

Input: x = 1,
    
Output: 1 -> 2 -> 10

<img width="507" height="97" alt="image" src="https://github.com/user-attachments/assets/06ff4ee9-d0b1-4def-98da-420d6278ce88" />

Explanation: We can see that 1 is inserted at the beginning of the linked list.


<img width="618" height="97" alt="image" src="https://github.com/user-attachments/assets/ba680e1b-a956-4842-95c7-fdcaed7f572f" />

Input: x = 1,
    
Output: 1 -> 2 -> 3 -> 4 -> 5

<img width="777" height="97" alt="image" src="https://github.com/user-attachments/assets/caff37c8-19f3-46a6-8a52-780dc2d20052" />

Explanation: We can see that 1 is inserted at the beginning of the linked list.
       
Constraints:

1 ≤ size of linked list ≤ 105
1 ≤ node.data, x ≤ 103

</P>

### Solution: 

```
/*
class Node {
  public:
    int data;
    Node *next;

    Node(int x) {
        data = x;
        next = NULL;
    }
};
*/

class Solution {
  public:
    Node *insertAtFront(Node *head, int x) {
        Node* newNode = new Node(x);  
        newNode->next = head;          
        head = newNode;                
        return head;                  
    }
};
```
---
