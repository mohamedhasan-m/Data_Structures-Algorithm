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
