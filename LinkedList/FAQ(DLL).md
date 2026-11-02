# Frequently Asked Questions on Doubly Linked List:

---
## Delete All Occurrences in DLL(Geeks For Geeks):

<P>
  Difficulty: Medium 

  Given the head of a doubly Linked List and a key x . Delete all occurrences of the given key x if it is present and return the new DLL.

Examples:

<img width="620" height="106" alt="image" src="https://github.com/user-attachments/assets/3b43f098-cd83-4e61-b65c-e78a7c8e5dd7" />


Input: 2<->2<->10<->8<->4<->2<->5<->2, x = 2
<img width="332" height="106" alt="image" src="https://github.com/user-attachments/assets/b9f508bd-1624-4286-9b1f-a9d4918391a2" />


Output:  10<->8<->4<->5

Explanation: 
All Occurrences of 2 have been deleted.

<img width="620" height="106" alt="image" src="https://github.com/user-attachments/assets/085eb875-8fd0-4ab8-8ce2-58f4e9be870d" />

Input: head = 9<->1<->3<->4<->5<->1<->8<->4, x = 9

<img width="553" height="106" alt="image" src="https://github.com/user-attachments/assets/5c2447b0-2e94-4af0-934a-4d2df0dfeb53" />


Output: 1<->3<->4<->5<->1<->8<->4

Explanation: 
All Occurrences of 9 have been deleted.
Constraints:

1 ≤ size of linked list ≤ 105
0 ≤ node.data ≤ 109

</P>

### Solution: 

```
/*Structure of the doubly linked list  Node 
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
    Node* deleteAllOccurOfX(Node* head, int x) {

        Node* temp = head;

        while(temp != NULL) {

            if(temp->data == x) {

                Node* nxtNode = temp->next;
                Node* prevNode = temp->prev;

                // Update head
                if(temp == head) {
                    head = nxtNode;
                }

                // Update previous node
                if(prevNode != NULL) {
                    prevNode->next = nxtNode;
                }

                // Update next node
                if(nxtNode != NULL) {
                    nxtNode->prev = prevNode;
                }

                delete temp;

                temp = nxtNode;
            }
            else {
                temp = temp->next;
            }
        }

        return head;
    }
};
```
---
##  Find pairs with given sum in doubly linked list(Code 360): 

<P>
  Difficulty: Easy 

  Problem statement
A doubly-linked list is a data structure that consists of sequentially linked nodes, and the nodes have reference to both the previous and the next nodes in the sequence of nodes.



You are given a sorted doubly linked list of size 'n', consisting of distinct positive integers, and a number 'k'.



Find out all the pairs in the doubly linked list with sum equal to 'k'.



Example :
Input: Linked List: 1 <-> 2 <-> 3 <-> 4 <-> 9 and 'k' = 5

Output: (1, 4) and (2, 3)

Explanation: There are 2 pairs in the linked list having sum 'k' = 5.
Detailed explanation ( Input/output format, Notes, Images )
Sample input 1:
5
1 2 3 4 9
5


Sample output 1
2
1 4
2 3


Explanation for sample input 1 :
There are 2 pairs in the linked list having sum equal to 'k' (= 5).


Sample input 2:
5
1 10 11 12 27
7


Sample output 2:
0


Explanation for sample output 2
There is no pair in the linked list with sum equal to 'k' (= 7).


Expected time complexity :
The expected time complexity is O('n').


Constraints:
2 <= 'n' <= 10 ^ 4
1 <= 'data' in any node <= 10 ^ 4
1 <= 'k' <= 10 ^ 4

'data' in every node is distinct.

Time limit: 1 second
</P>

### Solution: 

```
/**
 * Definition of doubly linked list:
 * class Node {
 * public:
 *      int data;
 *      Node *prev;
 *      Node *next;
 *      Node() {
 *          this->data = 0;
 *          this->prev = NULL;
 *          this->next = NULL;
 *      }
 *      Node(int data) {
 *          this->data = data;
 *          this->prev = NULL;
 *          this->next = NULL;
 *      }
 *      Node (int data, Node *next, Node *prev) {
 *          this -> data = data;
 *          this -> prev = prev;
 *          this -> next = next;
 *      }
 * };
 *
 *************************************************************************/

Node* findTail(Node* head){
    Node* tail = head;
    while(tail->next != NULL) tail = tail->next;
    return tail;
}
vector<pair<int, int>> findPairs(Node* head, int k)
{
    // Write your code here.
    vector<pair<int,int>> ans;
    if(head == NULL) return ans;
    Node* left = head;
    Node* right = findTail(head);
    while(left->data < right->data){
        if(left-> data + right->data == k){
            ans.push_back({left->data, right->data});
            left = left->next;
            right = right->prev;
        }
        else if(left->data + right->data < k){
            left = left->next;
        }
        else right = right->prev;
    }
    return ans;
}
```
---
## Remove Duplicates From Sorted DLL (Geeks For Geeks): 

<P>
  Difficulty: Medium 

  Given a doubly linked list of n nodes sorted by values, remove duplicate nodes present in the linked list.

Examples:

Input: head: 1<->1<->1<->2<->3<->4
Output: 1<->2<->3<->4
Explanation: Only the first occurance of node with value 1 is retained along with other distinct values. 
Input: head: 1<->2<->2<->3<->3<->4<->4
Output: 1<->2<->3<->4
Explanation:
Only the first occurance of nodes with values 2, 3 and 4 are retained, rest repeating nodes are deleted.
Constraint:
1 ≤ n ≤ 105


</P>

### Solution: 

```
/* Structure of a link list node
class Node {
  public:
    int data;
    Node* next;
    Node* prev;
    Node(int value) {
        data = value;
        next = nullptr;
        prev = nullptr;
    }
};
*/
class Solution {
  public:
    Node* removeDuplicates(Node* headRef) {
        // code here
        Node* temp = headRef;
        while(temp != NULL && temp->next != NULL){
            Node* nextNode = temp->next;
            while(nextNode != NULL && nextNode->data == temp->data){
                Node* duplicate = nextNode;
                nextNode = nextNode->next;
                delete duplicate;
            }
            temp->next = nextNode;
            if(nextNode != NULL) nextNode->prev = temp;
            
            temp = temp->next;
        }
        return headRef;
    }
};
```
---
