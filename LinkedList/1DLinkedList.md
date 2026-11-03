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
## Print Linked List(Geeks For Geeks): 

<P>
  Difficulty: Easy

  Given a linked list that contains integer elements. Iterate through the given list and print its elements separated by a space.

Examples:

Input:
<img width="447" height="95" alt="image" src="https://github.com/user-attachments/assets/c797a515-a9d1-48e9-8843-6f695cefc86f" />

Output: 1 2 3 4
Explanation: Iterating through the linked list prints 1, 2, 3, and 4.
Input:
<img width="515" height="95" alt="image" src="https://github.com/user-attachments/assets/12b1f5da-dc30-4300-a6bb-45cb69fe925f" />

Output: 2 7 10 9 8 
Explanation: Iterating through the linked list prints 2, 7, 10, 9 and 8.
Constraints:

1 ≤ list.size(), list[i] ≤ 1000
</P>

### Solution: 

```
/*
class Node {
  public:
    int data;
    Node* next;

    Node(int val) {
        data = val;
        next = nullptr;
    }
};
*/

class Solution {
  public:
    void printList(Node* head) {
        // code here
        Node* temp = head;
        while(temp != NULL){
            cout << temp->data << " ";
            temp = temp->next;
        }
    }
};
```
---
## Linked List Delete at Position(Geeks For Geeks): 

<P>
  Difficulty: Easy

  Given the head of a linked list and an integer x, delete the node at position x and return the updated head of the linked list.

Note: Positions use 1-based indexing.

Examples:

Input: x = 4,
<img width="519" height="95" alt="image" src="https://github.com/user-attachments/assets/040eb770-c27e-4574-bdda-45d60dd38b15" />

Output: 1 -> 2 -> 3 -> 5
Explanation: After deleting the node at the 4th position, the linked list is as
<img width="443" height="95" alt="image" src="https://github.com/user-attachments/assets/728f4c49-b837-411d-9e3e-ee4dbb1eec94" />

Input: x = 6,
<img width="632" height="95" alt="image" src="https://github.com/user-attachments/assets/72b34b66-40ab-466c-8fe5-32b8a59911b5" />

Output: 2 -> 5 -> 7 -> 8 -> 99
Explanation: After deleting the node at 6th position, the linked list is as
<img width="520" height="95" alt="image" src="https://github.com/user-attachments/assets/378764b3-e69c-48f8-8fc4-4fe41c436079" />


</P>

### Solution: 

```
/* Structure of Linked List Node
class Node {
public:
    int data;
    Node* next;
    Node(int data) {
        this->data = data;
        this->next = nullptr;
    }
};
*/
class Solution {
  public:
    Node* deleteNode(Node* head, int x) {
        // code here
        if (x == 1) {
            Node* temp = head;
            head = head->next;
            delete temp;
            return head;
        }
        Node* current = head;
        for (int i = 1; i < x - 1 && current != nullptr; i++) {
            current = current->next;
        }

        if (current == nullptr || current->next == nullptr) {
            return head;
        }

        Node* temp = current->next;
        current->next = current->next->next;
        delete temp;

        return head;
    }
};
```
---

## Insertion in singly Linked List(Geeks For Geeks): 

<P>
  Difficulty: Easy 

  Given the head of a Singly Linked List, a position pos and value val. Insert the val data at the given position (1-based index) of the Linked List and return the head of the modified Linked List.

Examples:

Input: head[] = [1, 3], pos = 3, val = 4
<img width="439" height="98" alt="image" src="https://github.com/user-attachments/assets/7a29e5c4-d898-4b41-bd6b-116215bd4252" />


Output: 1 -> 3 -> 4
Explanation: After inserting 4 at position 3 we'll get our linked list as - 
<img width="551" height="98" alt="image" src="https://github.com/user-attachments/assets/645130d7-068c-4551-b90a-e4c2ff49a132" />

Input: head[] = [1, 2, 9], pos = 2, val = 5
<img width="551" height="98" alt="image" src="https://github.com/user-attachments/assets/e4ebe0c0-2972-47fc-9994-39ae838fb477" />

Output: 1 -> 5 -> 2 -> 9
Explanation: After inserting 5 at position 2 we'll get our linked list as -
<img width="641" height="98" alt="image" src="https://github.com/user-attachments/assets/377d78a5-d32c-4d85-a570-1c0af194144f" />

Constraints:
1 ≤ number of nodes ≤ 104 
1 ≤ pos ≤ number of nodes + 1
1 ≤ val ≤ 104


</P>

### Solution: 

```
/* Structure of Linked List Node
class Node {
  public:
    int data;
    Node* next;
    Node(int data) {
        this->data = data;
        this->next = nullptr;
    }
}; */

class Solution {
  public:
    Node* insertPos(Node* head, int pos, int val) {
        // code here
        if (pos == 1) {
            Node* newNode = new Node(val);
            newNode->next = head;
            return newNode;
        }

        Node* current = head;
        for (int i = 1; i < pos - 1 && current != nullptr; i++) {
            current = current->next;
        }

        if (current != nullptr) {
            Node* newNode = new Node(val);
            newNode->next = current->next;
            current->next = newNode;
        }

        return head;
    }
};
```
---
## Deletion at End of Linkedlist(Geeks For Geeks): 

<P>
  Difficulty: Easy 

  Given a Linked List, delete the tail (i.e., the last node) of the Linked List and return the new head of the modified Linked List.

Examples:

Input: head[] = [1, 2, 3, 4, 5]
<img width="730" height="97" alt="image" src="https://github.com/user-attachments/assets/99ceb0d4-f241-447b-a524-5fe4a5d35419" />


Output: 1 -> 2 -> 3 -> 4
Explanation: After deleting tail from the given linked list, we'll be left with just 1 -> 2 -> 3 -> 4.
<img width="632" height="97" alt="image" src="https://github.com/user-attachments/assets/3e599a15-5fa7-447b-b1b8-7f222eb411c5" />

Input: head[] = [3, 12, 15]
<img width="520" height="97" alt="image" src="https://github.com/user-attachments/assets/aa3ff084-8b8b-491f-845f-c67290e5a9b3" />

Output: 3 -> 12
Explanation: After deleting tail from the given linked list, we'll be left with just 3 -> 12.
<img width="411" height="97" alt="image" src="https://github.com/user-attachments/assets/b8d174d7-eabf-4720-89d5-b0a8f3a134bb" />

Constraints:

1 ≤ size of linked list, Node.data ≤ 105
</P>

### Solution: 

```
/* Linked List Node Structure
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
    Node* removeLastNode(Node* head) {
        // code here
        if (!head) return nullptr;  
        if (!head->next) {  
            delete head;  
            return nullptr;  
        }  
        Node* temp = head;  
        while (temp->next->next) {  
            temp = temp->next;  
        }  
        delete temp->next;  
        temp->next = nullptr;  
        return head;
    }
};
```
---

## Delete the Kth Element of Linked List (TUF): 

<P>
  Difficulty: Easy

  Given the head of a singly linked list and an integer k, delete the kth node of the linked list and return the head of the modified list.

Example 1:
Input: linkedList = [3, 4, 5], k = 2

Output: linkedList = [3, 5]

Explanation:

The 2nd node with value 4 was removed.

Example 2:
Input: linkedList = [1, 2, 3], k = 1

Output: [2, 3]

Explanation:

The 1st Node was removed, note that the value of the head has changed.

Constraints:
n == number of nodes in the Linked list
1 <= n <= 1000
0 <= ListNode.val <= 100
1 <= k <= n
</P>

### Solution: 
```
/*
Definition of singly linked list:
class ListNode{
  public:
    int data;
    ListNode *next;
    ListNode() : data(0), next(nullptr) {}
    ListNode(int x) : data(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : data(x), next(next) {}
};
*/

class Solution {
    public:
        ListNode* deleteKthNode(ListNode* &head, int k) {
            // Your code goes here
            if (head == nullptr || k <= 0) return head;

if (k == 1) {
    ListNode* temp = head;
    head = head->next;
    delete temp;
    return head;
}

ListNode* current = head;
for (int i = 1; current != nullptr && i < k - 1; i++) {
    current = current->next;
}

if (current == nullptr || current->next == nullptr) return head;

ListNode* nodeToDelete = current->next;
current->next = current->next->next;
delete nodeToDelete;

return head;

        }
};
```
---

## Delete the Element with Value X (TUF):

<P>
  Difficulty: Easy 

  Given the head of a singly linked list and an integer X, delete the node with value X and return the head of the modified list.

Example 1:
Input: linkedList = [3, 4, 5], X = 5

Output: [3, 4]

Explanation:

The node with value 5 was removed.

Example 2:
Input: linkedList = [3, 4, 5], X = 7

Output: [3, 4, 5]

Explanation:

No nodes were removed.

Constraints:
n == number of nodes in the Linked list
1 <= n <= 1000
0 <= ListNode.val <= 100
0 <= X <= 100
Number of nodes with value X is either 0 or 1
</P>

### Solution: 

```
/*
Definition of singly linked list:
class ListNode{
  public:
    int data;
    ListNode *next;
    ListNode() : data(0), next(nullptr) {}
    ListNode(int x) : data(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : data(x), next(next) {}
};
*/

class Solution {
public:
    ListNode* deleteNodeWithValueX(ListNode* &head, int X) {

        if (!head) return nullptr;

        // Case 1: Delete head node
        if (head->data == X) {
            ListNode* temp = head;
            head = head->next;
            delete temp;
            return head;
        }

        // Case 2: Delete a node other than head
        ListNode* current = head;

        while (current->next && current->next->data != X) {
            current = current->next;
        }

        if (current->next) {
            ListNode* temp = current->next;
            current->next = current->next->next;
            delete temp;
        }

        return head;  // Missing in your code!
    }
};
```
---
## Insertion at Tail of Linked List (TUF): 

<P>
  Difficulty: Easy 

  Given the head of a singly linked list and an integer X, insert a node with value X at the tail of the linked list and return the head of the modified list.

Example 1:
Input: linkedList = [1, 2, 3], X = 7

Output: [1, 2, 3, 7]

Explanation:

7 was added as the last node.

Example 2:
Input: linkedList = [], X = 0

Output: [0]

Explanation:

0 was added as the last/only node.

Constraints:
0 <= number of nodes in the Linked List <= 1000
0 <= ListNode.val <= 100
0 <= X <= 100
</P>

### Solution: 

```
/*
Definition of singly linked list:
class ListNode{
  public:
    int data;
    ListNode *next;
    ListNode() : data(0), next(nullptr) {}
    ListNode(int x) : data(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : data(x), next(next) {}
};
*/

class Solution {
public:
    ListNode* insertAtTail(ListNode* &head, int X) {

        // Create a new node
        ListNode* newNode = new ListNode(X);

        // Case 1: Empty linked list
        if (head == nullptr) {
            head = newNode;
            return head;
        }

        // Case 2: Traverse to the last node
        ListNode* temp = head;

        while (temp->next != nullptr) {
            temp = temp->next;
        }

        // Insert at tail
        temp->next = newNode;

        return head;
    }
};
```
---

## Insertion at the Kth Position of Linked List (TUF): 

<P>
  Difficulty: Easy 

  Given the head of a singly linked list and two integers X and K, insert a node with value X as the kth node of the linked list and return the head of the modified list.

Example 1:
Input: linkedList = [1, 2, 3], X = 5, K = 2

Output: [1, 5, 2, 3]

Example 2:
Input: linkedList = [], X = 7, K = 1

Output: [7]

Explanation:

Note that the value of the head was changed.

Constraints:
n == number of nodes in the Linked List
0 <= n <= 1000
0 <= ListNode.val <= 100
0 <= X <= 100
1 <= K <= n+1
</P>

### Solution: 

```
class Solution {
public:
    ListNode* insertAtKthPosition(ListNode* &head, int X, int K) {

        // Case 1: Insert at the beginning
        if (K == 1) {
            ListNode* newNode = new ListNode(X);
            newNode->next = head;
            head = newNode;
            return head;
        }

        ListNode* temp = head;

        // Traverse to the (K-1)th position
        for (int i = 1; i < K - 1 && temp != nullptr; i++) {
            temp = temp->next;
        }

        // Invalid position
        if (temp == nullptr) return head;

        // Insert new node
        ListNode* newNode = new ListNode(X);

        newNode->next = temp->next;
        temp->next = newNode;

        return head;
    }
};
```
---

## Insert the Before the value X in Linked List (TUF): 

<P>
  Difficulty: Easy 

  Given the head of a singly linked list and two integers X and val.

Insert a node with value val before the node with value X in the linked list and return the head of the modified list.

Example 1:
Input: linkedList = [1, 2, 3], X = 2, val = 5

Output: [1, 5, 2, 3]

Explanation:

The node with value 5 was added before the node with value 2

Example 2:
Input: linkedList = [1, 2, 3], X = 7, val = 5

Output: [1, 2, 3]

Explanation:

No node was added as X was not found in the list.

Constraints:
n == number of nodes in the Linked List
1 <= n <= 1000
0 <= ListNode.val <= 100
0 <= X <= 100
0 <= val <= 100
Number of nodes with value X is 0 or 1
</P>

### Solution: 

```
/*
Definition of singly linked list:
class ListNode{
  public:
    int data;
    ListNode *next;
    ListNode() : data(0), next(nullptr) {}
    ListNode(int x) : data(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : data(x), next(next) {}
};
*/

class Solution {
public:
    ListNode* insertBeforeX(ListNode* &head, int X, int val) {

        // Case 1: Empty list
        if (head == nullptr) return head;

        // Case 2: X is present at head
        if (head->data == X) {
            ListNode* newNode = new ListNode(val);
            newNode->next = head;
            head = newNode;
            return head;
        }

        // Case 3: Find the node before X
        ListNode* temp = head;

        while (temp->next != nullptr && temp->next->data != X) {
            temp = temp->next;
        }

        // X not found
        if (temp->next == nullptr) return head;

        // Insert before X
        ListNode* newNode = new ListNode(val);

        newNode->next = temp->next;
        temp->next = newNode;

        return head;
    }
};
```
---
