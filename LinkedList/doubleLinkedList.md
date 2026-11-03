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
## Delete in Doubly Linked list (Geeks For Geeks): 

<P>
  Difficulty: Easy 

  Given the head of a doubly linked list and an integer k, delete the node at the kth position (1-based indexing) and return the head of the modified list.

Examples:

Input: k = 3,
<img width="590" height="136" alt="image" src="https://github.com/user-attachments/assets/63866ee2-2ba7-4f0d-af21-941895014f87" />


Output: 1 <-> 3
Explanation: After deleting the node at position 3 (position starts from 1), the updated linked list is 1 <-> 3.
<img width="442" height="136" alt="image" src="https://github.com/user-attachments/assets/98d0dbaf-cb4c-4d45-90c7-01dc6365decf" />

Input: k = 1,
<img width="714" height="136" alt="image" src="https://github.com/user-attachments/assets/4f19f33e-a71e-4221-8edf-730884cf1e79" />

Output: 5 <-> 2 <-> 9
Explanation: After deleting the node at position 1, the updated linked list is 5 <-> 2 <-> 9.
<img width="590" height="136" alt="image" src="https://github.com/user-attachments/assets/06e1201d-3285-489e-ab84-15fc418437d6" />

Constraints:

1 ≤ size of linked list ≤ 106
0 ≤ Node.data ≤ 104
1 ≤ k ≤ head.size()

</P>

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
		this->next = this->prev = nullptr;
	}
};*/

class Solution {
public:
    Node* delPos(Node* head, int k) {

        if (head == nullptr) return nullptr;

        // Case 1: Delete head node
        if (k == 1) {
            Node* temp = head;
            head = head->next;

            if (head != nullptr) {
                head->prev = nullptr;
            }

            delete temp;
            return head;
        }

        // Case 2: Traverse to Kth node
        Node* temp = head;

        for (int i = 1; i < k && temp != nullptr; i++) {
            temp = temp->next;
        }

        // Invalid position
        if (temp == nullptr) return head;

        // Update previous node
        temp->prev->next = temp->next;

        // Update next node
        if (temp->next != nullptr) {
            temp->next->prev = temp->prev;
        }

        delete temp;

        return head;
    }
};
```
---
## Doubly Linked List From an Array (Geeks For Geeks): 

<P>
  Difficulty: Easy 

  Given an array arr[] of integers, the goal is to create a Doubly Linked List (DLL) where each element of the array is represented as a node. The nodes must be linked in the same sequence as the array, maintaining both forward (next) and backward (prev) connections. Return the head of the constructed doubly linked list.

Examples:

Input: arr[] = [1, 2, 3, 4]
Output: 1 <-> 2 <-> 3 <-> 4
Explanation: Each array element becomes a node in the doubly linked list. Node 1 connects forward to 2, and node 2 connects back to 1, and so on.
<img width="756" height="136" alt="image" src="https://github.com/user-attachments/assets/94b58d4f-a366-4429-85d6-a0d0cbacd708" />

Input: arr[] = [10, 20]
Output: 10 <-> 20
Explanation: The list has two nodes. Node 10 points to 20, and node 20 points back to 10.
<img width="438" height="136" alt="image" src="https://github.com/user-attachments/assets/14902a8f-8218-48c6-ad6f-3cdf5249ed74" />

Constraints:
1 ≤ arr.size() ≤ 104
0 ≤ arr[i] ≤ 104


</P>

### Solution: 

```
/* class Node {
  public:
    int data;
    Node* next;
    Node* prev;
    Node(int d) {
        data = d;
        next = nullptr;
        prev = nullptr;
    }
}; */

class Solution {
public:
    Node* createDLL(vector<int>& arr) {

        if (arr.empty()) return nullptr;

        // Create head node
        Node* head = new Node(arr[0]);

        Node* temp = head;

        // Create remaining nodes
        for (int i = 1; i < arr.size(); i++) {

            Node* newNode = new Node(arr[i]);

            temp->next = newNode;
            newNode->prev = temp;

            temp = newNode;
        }

        return head;
    }
};
```
---
## Delete Last Node in a Doubly Linked List (Code 360): 

<P>
  Difficulty: Easy 

  Problem statement
A doubly-linked list is a data structure that consists of sequentially linked nodes, and the nodes have reference to both the previous and the next nodes in the sequence of nodes.



Given a doubly-linked list, delete the node at the end of the doubly linked list.



Note:
You need not print anything. You’re given the head of the linked list, just return the head of the modified list.


Example:
Input: Linked List:  4 <-> 10 <-> 3 <-> 5 <-> 20

Output: Modified Linked List: 4 <-> 10 <-> 3 <-> 5

Explanation: The last node having ‘data’ = 20 is removed from the linked list.
Detailed explanation ( Input/output format, Notes, Images )
Sample Input 1:
5
4 10 3 5 20


Sample Output 1:
4 10 3 5 NULL


Explanation Of Sample Input 1 :
The last node having ‘data’ = 20 is removed from the linked list.


Sample Input 2 :
1
5


Sample Output 2 :
NULL


Explanation Of Sample Input 2 :
The linked list has only one node, so the modified linked list is empty.


Expected time complexity :
The expected time complexity is O(N).


Constraints:
1 <= ‘N’ <= 100000
1 <= Data of a node in linked list <= 10^9

Time limit: 1 second

</P>

### Solution: 

```
/**
 * Definition of doubly linked list:
 *
 * struct Node {
 *      int data;
 *      Node *prev;
 *      Node *next;
 *      Node() : data(0), prev(nullptr), next(nullptr) {}
 *      Node(int val) : data(val), prev(nullptr), next(nullptr) {}
 *      Node(int val, Node *p, Node *n) : data(val), prev(p), next(n) {}
 * };
 *
 *************************************************************************/

Node* deleteLastNode(Node* head) {

    // Case 1: Empty list
    if (head == nullptr) return nullptr;

    // Case 2: Only one node
    if (head->next == nullptr) {
        delete head;
        return nullptr;
    }

    // Traverse to the last node
    Node* temp = head;

    while (temp->next != nullptr) {
        temp = temp->next;
    }

    // Disconnect the last node
    temp->prev->next = nullptr;

    // Delete last node
    delete temp;

    return head;
}
```
---
## Removing Given Node in Doubly Linked List (TUF): 

<P>
  Difficulty: Easy 

  Given a node's reference within a doubly linked list, remove that node from the linked list while preserving the list's integrity.

You will only be given the node's reference, not the head of the list. It is guaranteed that the given node will not be the head of the list.

Example 1:
Input: head = [1, 3, 5], node = 3

Output: [1, 5]

Explanation:

The referenced node with value 3 was removed.
Example 2:
Input: head = [1, 3, 7], node = 7

Output: head = [1, 3]

Explanation:

The referenced node with value 7 was removed.

Constraints:
2 <= Number of nodes in the list <= 100
0 <= ListNode.val <= 100
Node is guaranteed to be a part of the linked list and will not be the head
</P>

### Solution: 

```
/**
class ListNode
{
 * Definition for doubly-linked list.
 *  public:
 *      int data;
 *      ListNode *prev;
 *      ListNode *next;
 *      ListNode() : data(0), prev(nullptr), next(nullptr) {}
 *      ListNode(int x) : data(x), prev(nullptr), next(nullptr) {}
 *      ListNode(int x, ListNode *prev, ListNode *next) : data(x), prev(prev), next(next) {}
};
*/
class Solution {
public:
    void deleteGivenNode(ListNode* node) {

        if (node == nullptr) return;

        // Connect previous node to next node
        if (node->prev != nullptr) {
            node->prev->next = node->next;
        }

        // Connect next node to previous node
        if (node->next != nullptr) {
            node->next->prev = node->prev;
        }

        delete node;
    }
};
```
---
## Insert Before tail in Doubly Linked List (Code 360): 

<P>
  Difficulty: Easy 

  Problem statement
A doubly-linked list is a data structure that consists of sequentially linked nodes, and the nodes have reference to both the previous and the next nodes in the sequence of nodes.



Given a doubly-linked list and a value ‘k’, insert a node having value ‘k’ before the tail of the doubly linked list.



Note:
You need not print anything. You’re given the head of the linked list. Return the head of the modified list.


Example:
Input: Linked List: 4 <-> 10 <-> 3 <-> 5 and ‘k’ = 20

Output: Modified Linked List: 4 <-> 10 <-> 3 <-> 20 <-> 5

Explanation: A new node having value ‘k’ = 20 is inserted before the tail of the linked list.
Detailed explanation ( Input/output format, Notes, Images )
Sample Input 1:
4
4 10 3 5
20


Sample Output 1:
4 10 3 20 5


Explanation Of Sample Input 1 :
A new node having value ‘k’ = 20 is inserted at the end of the linked list.


Sample Input 2 :
0

5


Sample Output 2 :
5


Explanation Of Sample Input 2 :
The linked list was empty. So the new node is the only node in the modified linked list.


Expected time complexity:
The expected time complexity is O(N).


Constraints:
0 <= ‘N’ <= 100000
1 <= Value in linked list <= 10^9
1 <= ‘k’ <= 10^9

Time limit: 1 second
</P>

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

Node* insertBeforeTail(Node* head, int k) {

    // Case 1: Empty list
    if (head == nullptr) {
        return new Node(k);
    }

    // Case 2: Create new node
    Node* newNode = new Node(k);

    // Case 3: Only one node
    if (head->next == nullptr) {
        newNode->next = head;
        head->prev = newNode;
        return newNode;
    }

    // Case 4: Find tail
    Node* tail = head;

    while (tail->next != nullptr) {
        tail = tail->next;
    }

    // Insert before tail
    Node* beforeTail = tail->prev;

    beforeTail->next = newNode;
    newNode->prev = beforeTail;

    newNode->next = tail;
    tail->prev = newNode;

    return head;
}
```
---

## Insert node before (kth node) in Doubly Linked List(TUF): 

<P>
  Difficulty: Easy 

  Given the head of a doubly linked list and two integers X and K, insert a new node with value X, before the Kth node of the linked list and return the head of the modified linked list.

Example 1:
Input: head = [1, 3, 5], X = 7, K = 2

Output: head = [1, 7, 3, 5]

Explanation: A node with value 7 was added before the 2nd node.

Example 2:
Input: head = [5], X = 7, K = 1

Output: head = [7, 5]

Explanation: A node with value 7 was added, note that the head was changed

Constraints:
n == Number of nodes in the linked list
1 <= n <= 100
0 <= ListNode.val <= 100
0 <= X <= 100
1 <= K <= n
</P>

### Solution: 
```
/**
class ListNode
{
 * Definition for doubly-linked list.
 *  public:
 *      int data;
 *      ListNode *prev;
 *      ListNode *next;
 *      ListNode() : data(0), prev(nullptr), next(nullptr) {}
 *      ListNode(int x) : data(x), prev(nullptr), next(nullptr) {}
 *      ListNode(int x, ListNode *prev, ListNode *next) : data(x), prev(prev), next(next) {}
};
*/

class Solution {
public:
    ListNode* insertBeforeKthPosition(ListNode* head, int X, int K) {

        ListNode* newNode = new ListNode(X);

        // Case 1: Insert before the first node
        if (K == 1) {
            newNode->next = head;

            if (head != nullptr) {
                head->prev = newNode;
            }

            return newNode;
        }

        // Case 2: Traverse to Kth node
        ListNode* temp = head;

        for (int i = 1; i < K && temp != nullptr; i++) {
            temp = temp->next;
        }

        // Invalid position
        if (temp == nullptr) {
            delete newNode;
            return head;
        }

        // Insert before temp
        ListNode* previous = temp->prev;

        previous->next = newNode;
        newNode->prev = previous;

        newNode->next = temp;
        temp->prev = newNode;

        return head;
    }
};
```
---

## Insert before given node in Doubly Linked List(TUF): 

<P>
  Difficulty: Easy 

  Given a node's reference within a doubly linked list and an integer X, insert a node with value X before the given node in the linked list while preserving the list's integrity.

You will only be given the node's reference, not the head of the list. It is guaranteed that the given node will not be the head of the list.

Example 1:
Input: head = [1, 2, 6], node = 6, X = 7

Output: head = [1, 2, 7, 6]

Explanation: Note that the head was not given to the function.

Example 2:
Input: head = [7, 5, 15], node = 5, X = 10

Output: head = [7, 10, 5, 15]

Explanation: The node with value 5 was referenced, thus the new node was added before the given node.

Constraints:
n == Number of nodes in the Linked List
2 <= n <= 100
0 <= ListNode.val <= 100
0 <= X <= 100
It is guaranteed the given node will be a part of a doubly linked list and will not be its head.
</P>

### Solution: 

```
/**
class ListNode
{
 * Definition for doubly-linked list.
 *  public:
 *      int data;
 *      ListNode *prev;
 *      ListNode *next;
 *      ListNode() : data(0), prev(nullptr), next(nullptr) {}
 *      ListNode(int x) : data(x), prev(nullptr), next(nullptr) {}
 *      ListNode(int x, ListNode *prev, ListNode *next) : data(x), prev(prev), next(next) {}
};
*/
class Solution {
public:
    void insertBeforeGivenNode(ListNode* node, int X) {

        if (node == nullptr) return;

        ListNode* newNode = new ListNode(X);

        // Connect new node with previous node
        newNode->prev = node->prev;
        newNode->next = node;

        // Update previous node's next
        if (node->prev != nullptr) {
            node->prev->next = newNode;
        }

        // Update given node's previous
        node->prev = newNode;
    }
};

```
---
