# Basic on Doubly Linked List 
---

## Delete Head of Doubly Linked List(Geeks For Geeks): 

<P>
  Difficulty: Easy 

  Given the head of a doubly linked list, delete the head node and return the new head of the list.

Examples :



Input:
<img width="602" height="81" alt="image" src="https://github.com/user-attachments/assets/662927dd-c0ad-47c3-9fac-7799c15a5d2b" />


Output: 2 <-> 3

<img width="443" height="81" alt="image" src="https://github.com/user-attachments/assets/f3746d92-6adc-4b5e-b405-c6accc40bf46" />


Explanation: The first node [1] is removed, and the next node [2] becomes the new head.


Input: 
<img width="800" height="81" alt="image" src="https://github.com/user-attachments/assets/411243f4-8cfb-49ee-b501-a9f33dda5695" />


head = [2, 5, 7, 8, 99, 100]
 
Output: 
<img width="741" height="81" alt="image" src="https://github.com/user-attachments/assets/63722e51-a9d9-455f-84f1-8c2619a25d68" />


5 <-> 7 <-> 8 <-> 99 <-> 100

Explanation: The head node [2] is deleted, and the remaining list starts from node 5.
Constraints:
2 ≤ number of nodes ≤ 105
1 ≤ node->data ≤ 109
</P>

### Solution: 

```
/* Structure of doubly linked list Node
class Node {
public:
    int data;
    Node* next;
    Node* prev;

    Node(int x) {
        data = x;
        next = nullptr;
        prev = nullptr;
    }
};*/
class Solution {
  public:
    Node* deleteHead(Node* head) {
        // code here
        if(head == NULL){
            return NULL;
        }
        
        if(head->next == NULL){
            delete head;
            return NULL;
        }
        
        Node* back = head; 
        head = head->next;
        
        head->prev = nullptr;
        back->next = nullptr;
        
        delete back;
        
        return head;
    }
};

```
---

##  Insert At The Front of a Doubly Linked List (Code 360):

<p>
  Problem statement
You are given a doubly-linked list of length ‘n’.



You must insert a node having the value ‘k’ in the front of the doubly linked list.



Note:
A doubly-linked list is a data structure that consists of sequentially linked records, and the nodes have reference to both the previous and the next nodes in the sequence of nodes.
For Example:
Input: Linked List: 4 <-> 10 <-> 3 <-> 5 and ‘k’ = 20

Output: Modified Linked List: 20 <-> 4 <-> 10 <-> 3 <-> 5

Explanation: A new node having value ‘k’ = 20 is inserted at the front of the linked list.


Detailed explanation ( Input/output format, Notes, Images )
Sample Input 1:
4
4 10 3 5
20
Sample Output 1:
20 4 10 3 5
Explanation of sample input 1:-
Explanation: A new node having value ‘k’ = 20 is inserted at the front of the linked list.
Sample Input 2:
0

5
Sample Output 2:
5
Explanation Of Sample Input 2:
The linked list was empty. So the new node is the only node in the modified linked list.
Expected time complexity:
The expected time complexity is O(1).
Constraints:-
0 <= ‘n’ <= 10^5
1 <= Value in linked list node <= 10^9
1 <= ‘k’ <= 10^9

Time Limit: 1 sec

</p>

### Solution:

```
/**
 * Definition of doubly linked list:
 *
 * struct Node {
 *      int value;
 *      Node *prev;
 *      Node *next;
 *      Node() : value(0), prev(nullptr), next(nullptr) {}
 *      Node(int val) : value(val), prev(nullptr), next(nullptr) {}
 *      Node(int val, Node *p, Node *n) : value(val), prev(p), next(n) {}
 * };
 *
 *************************************************************************/

Node* insertAtFront(Node *head, int k) {
    Node* newHead = new Node(k, nullptr, head);

    if (head != nullptr) {
        head->prev = newHead;
    }

    return newHead;
}
```
---
## Reverse a Doubly Linked List: (Geeks For Geeks): 

<p>
  Diffculty: Easy 

  Given the head of a doubly linked list, reverse the list and return the head of the reversed doubly linked list.

Note: Driver code will print the returned list in both forward and backward directions.

Examples:

Input:
<img width="578" height="136" alt="image" src="https://github.com/user-attachments/assets/693f69d3-27c3-4448-aa9b-9a3ad98a5a9a" />

Output: 

<img width="578" height="136" alt="image" src="https://github.com/user-attachments/assets/b97f08fc-4cee-466e-a763-5e3ebafb10e7" />

5 <-> 4 <-> 3
3 <-> 4 <-> 5
Explanation: After reversing the given doubly linked list the new list will be 5 <-> 4 <-> 3.

Input: 
<img width="844" height="136" alt="image" src="https://github.com/user-attachments/assets/32793d59-8ee4-4d58-963b-ac88725f4235" />

Output: 

<img width="844" height="136" alt="image" src="https://github.com/user-attachments/assets/9083f4b4-9359-4534-8509-94725961be4f" />

196 <-> 59 <-> 122 <-> 75
75 <-> 122 <-> 59 <-> 196
Explanation: After reversing the given doubly linked list the new list will be 196 <-> 59 <-> 122 <-> 75.

Constraints:

1 ≤ size of linked list ≤ 106
0 ≤ node.data ≤ 104
</p>

### Solution:

```
/* Structure of Doubly Linked List Node
class Node {
  public:
    int data;
    Node *next;
    Node *prev;

    Node(int val) {
        data = val;
        next = nullptr;
        prev = nullptr;
    }
};

*/
class Solution {
  public:
    Node *reverse(Node *head) {
        // code here
        if(head == NULL || head->next == NULL){
            return head;
        }
        
        Node* prev = NULL;
        Node* current = head;
        while(current != NULL){
            prev = current->prev;
            
            current->prev = current->next;
            current->next = prev;
            
            current = current->prev;
        }
        return prev->prev;
    }
};
```
---
