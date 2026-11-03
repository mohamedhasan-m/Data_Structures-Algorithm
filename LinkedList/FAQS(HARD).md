# Frequentely Asked Questions (Hard): 

---

## Reverse Nodes in K Group (25. Leetcode): 

<P>
  Difficulty: Hard

  Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.

 

Example 1:
<img width="542" height="222" alt="image" src="https://github.com/user-attachments/assets/a9b76a45-1db7-4db9-8685-527db925f160" />


Input: head = [1,2,3,4,5], k = 2
Output: [2,1,4,3,5]
Example 2:
<img width="542" height="222" alt="image" src="https://github.com/user-attachments/assets/0a44ea84-03ff-451b-a0cd-4a501dd854af" />


Input: head = [1,2,3,4,5], k = 3
Output: [3,2,1,4,5]
 

Constraints:

The number of nodes in the list is n.
1 <= k <= n <= 5000
0 <= Node.val <= 1000
 

Follow-up: Can you solve the problem in O(1) extra memory space?

 

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
    ListNode* reverseLinkedList(ListNode* temp){
        ListNode* prev = nullptr;
        ListNode* current = temp;

        while(current != nullptr){
            ListNode* front = current->next;
            current->next = prev;
            prev = current;
            current = front;
        }

        return prev;
    }
    ListNode* getKthNode(ListNode* temp, int k){
        k -= 1;
        while(temp != NULL && k>0){
            k--;
            temp = temp->next;
        }
        return temp;
    }
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* temp = head;
        ListNode* prevLast = NULL;
        while(temp != NULL){
            ListNode* KthNode = getKthNode(temp,k);
            if(KthNode == NULL){
                if(prevLast) prevLast->next = temp;
                break;
            }

            ListNode* nextNode = KthNode->next;
            KthNode->next = NULL;
            reverseLinkedList(temp);
            if(temp == head) {
                head = KthNode;
            }
            else{
                prevLast->next = KthNode;
            }

            prevLast = temp;
            temp = nextNode;
        }
        return head;
    }
};
```
---
## Rotate List (61.Leetcode): 

<P>
  Difficulty: Medium

  Given the head of a linked list, rotate the list to the right by k places.

 

Example 1:
<img width="712" height="302" alt="image" src="https://github.com/user-attachments/assets/370fd7a6-df80-4b55-8dbf-b47836706e8d" />


Input: head = [1,2,3,4,5], k = 2
Output: [4,5,1,2,3]
Example 2:
<img width="472" height="542" alt="image" src="https://github.com/user-attachments/assets/515f6324-c144-4077-8df8-a6135ab007ae" />


Input: head = [0,1,2], k = 4
Output: [2,0,1]
 

Constraints:

The number of nodes in the list is in the range [0, 500].
-100 <= Node.val <= 100
0 <= k <= 2 * 109
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
    ListNode* findNthNode(ListNode* temp, int k){
        int cnt = 1;
        while(temp != NULL){
            if(cnt == k){
                return temp;
            }
            cnt ++;
            temp = temp->next;
        }
        return temp;
    }
    ListNode* rotateRight(ListNode* head, int k) {
        if(head == NULL || k==0) return head;
        int len = 1;
        ListNode* tail = head;
        while(tail->next != NULL){
            len++;
            tail = tail->next;
        }
        if(k%len == 0) return head;

        k = k%len;

        tail->next = head;

        ListNode* newLastNode = findNthNode(head,len-k);

        head = newLastNode->next;
        newLastNode->next = NULL;

        return head;
    }
};
```
---
## Merge two Sorted Lists (21. Leetcode):

<P>
  Difficulty: Easy

  You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

 

Example 1:

<img width="662" height="302" alt="image" src="https://github.com/user-attachments/assets/44b21c21-fc23-41e8-8a02-ef9b697ed2f2" />

Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
Example 2:

Input: list1 = [], list2 = []
Output: []
Example 3:

Input: list1 = [], list2 = [0]
Output: [0]
 

Constraints:

The number of nodes in both lists is in the range [0, 50].
-100 <= Node.val <= 100
Both list1 and list2 are sorted in non-decreasing order.
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
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* t1 = list1;
        ListNode* t2 = list2;
        ListNode* dummyNode = new ListNode(-1);
        ListNode* temp = dummyNode;
        while(t1 != NULL && t2 != NULL){
            if(t1->val < t2->val){
                temp->next = t1;
                temp = t1;
                t1 = t1->next;
            }
            else{
                temp->next = t2;
                temp = t2;
                t2 = t2->next;
            }
        }
        if(t1) temp->next = t1;
        else temp->next = t2;
        return dummyNode->next;
    }
};
```
---
## Flattening a Linked List (Geeks For Geeks): 

<P>
  Difficulty: Medium 

  In a linked list, every node has two pointers: next and bottom. The heads of n linked lists are connected using the next pointer, while the bottom pointer points to the next node in the current linked list.

Each linked list is sorted in non-decreasing order of data, and the head nodes are also sorted in non-decreasing order.

Given the head of the first linked list, flatten the linked lists into a single sorted linked list such that every node is connected using only the bottom pointers.

Examples:

Input:
<img width="734" height="396" alt="image" src="https://github.com/user-attachments/assets/2827559e-77d8-4f14-8329-6337b6fc1d5d" />

Output: 5 -> 7 -> 8 -> 10 -> 19 -> 20 -> 22 -> 28 -> 40 -> 45.
Explanation: 
Bottom pointer of 5 is pointing to 7.
Bottom pointer of 7 is pointing to 8.
Bottom pointer of 10 is pointing to 20 and so on.
So, after flattening the linked list the sorted list will be 
5 -> 7 -> 8 -> 10 -> 19 -> 20 -> 22 -> 28 -> 40 -> 45.
Input:
<img width="734" height="334" alt="image" src="https://github.com/user-attachments/assets/617621ad-6e3c-4d7b-ade4-299db8abe916" />

Output: 5 -> 7 -> 8 -> 10 -> 19 -> 22 -> 28 -> 30 -> 50
Explanation:
Bottom pointer of 5 is pointing to 7.
Bottom pointer of 7 is pointing to 8.
Bottom pointer of 8 is pointing to 30 and so on.
So, after flattening the linked list the sorted list will be 
5 -> 7 -> 8 -> 10 -> 19 -> 22 -> 28 -> 30 -> 50.
Constraints:

0 ≤ n ≤ 104
head.size() = n
1 ≤ head[i].size() ≤ 50
1 ≤ head[i][j] ≤ 5*105

</P>

### Solution (Recursive Approcah): 

```
/* Structure of Linked List Node
class Node {
public:
    int data;
    Node* next;
    Node* bottom;

    Node(int x) {
        data = x;
        next = nullptr;
        bottom = nullptr;
    }
};*/

class Solution {
public:

    Node* merge(Node* list1, Node* list2) {

        Node* dummyNode = new Node(-1);
        Node* res = dummyNode;

        while (list1 != NULL && list2 != NULL) {

            if (list1->data < list2->data) {
                res->bottom = list1;
                list1 = list1->bottom;
            }
            else {
                res->bottom = list2;
                list2 = list2->bottom;
            }

            res = res->bottom;
            res->next = NULL;
        }

        if (list1) {
            res->bottom = list1;
        }
        else {
            res->bottom = list2;
        }

        while (res->bottom != NULL) {
            res = res->bottom;
            res->next = NULL;
        }

        Node* ans = dummyNode->bottom;
        delete dummyNode;

        return ans;
    }

    Node* flatten(Node* head) {

        if (head == NULL || head->next == NULL) {
            return head;
        }

        Node* mergedHead = flatten(head->next);

        head = merge(head, mergedHead);

        return head;
    }
};
```

### Solution (Divide and Conquer Approach): 
```
/* Structure of Linked List Node
class Node {
public:
    int data;
    Node* next;
    Node* bottom;

    Node(int x) {
        data = x;
        next = nullptr;
        bottom = nullptr;
    }
};*/

class Solution {
public:

    Node* merge(Node* list1, Node* list2) {

        Node* dummyNode = new Node(-1);
        Node* res = dummyNode;

        while (list1 != NULL && list2 != NULL) {

            if (list1->data < list2->data) {
                res->bottom = list1;
                list1 = list1->bottom;
            }
            else {
                res->bottom = list2;
                list2 = list2->bottom;
            }

            res = res->bottom;
            res->next = NULL;
        }

        if (list1) {
            res->bottom = list1;
        }
        else {
            res->bottom = list2;
        }

        while (res->bottom != NULL) {
            res = res->bottom;
            res->next = NULL;
        }

        Node* ans = dummyNode->bottom;
        delete dummyNode;

        return ans;
    }

    Node* flatten(Node* head) {

        if (head == NULL || head->next == NULL) {
            return head;
        }

        Node* a = head;
        Node* b = head->next;

        // Split the lists into two halves
        Node* prev = NULL;
        Node* slow = head;
        Node* fast = head;

        while (fast != NULL && fast->next != NULL) {
            prev = slow;
            slow = slow->next;
            fast = fast->next->next;
        }

        prev->next = NULL;

        Node* left = flatten(head);
        Node* right = flatten(slow);

        return merge(left, right);
    }
};
```
---
## Merge K Sorted Lists(23. Leetcode): 

<P>
  Difficulty: Hard

  You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

 

Example 1:

Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted linked list:
1->1->2->3->4->4->5->6
Example 2:

Input: lists = []
Output: []
Example 3:

Input: lists = [[]]
Output: []
 

Constraints:

k == lists.length
0 <= k <= 104
0 <= lists[i].length <= 500
-104 <= lists[i][j] <= 104
lists[i] is sorted in ascending order.
The sum of lists[i].length will not exceed 104.
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
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        priority_queue<pair<int,ListNode*>,
        vector<pair<int,ListNode*>>, greater<pair<int,ListNode*>>> pq;
        for (int i = 0; i<lists.size();i++){
            if(lists[i]){
                pq.push({lists[i]->val, lists[i]});
            }
        }
        ListNode* dummyNode = new ListNode(-1);
        ListNode* temp = dummyNode;
        while(!pq.empty()){
            auto it = pq.top();
            pq.pop();
            if(it.second->next){
                pq.push({it.second->next->val, it.second->next});
            }
            temp->next = it.second;
            temp = temp->next;
        }
        return dummyNode->next;
    }
};
```
---
## Sort List (148. Leetcode): 

<P>
  Difficulty: Medium 

  Given the head of a linked list, return the list after sorting it in ascending order.

 

Example 1:
<img width="562" height="242" alt="image" src="https://github.com/user-attachments/assets/1d655ac1-ff35-49d7-984f-524ca13c482c" />


Input: head = [4,2,1,3]
Output: [1,2,3,4]
Example 2:

<img width="722" height="242" alt="image" src="https://github.com/user-attachments/assets/39f1f536-88c0-4d92-a032-9b2d001ed99e" />

Input: head = [-1,5,3,4,0]
Output: [-1,0,3,4,5]
Example 3:

Input: head = []
Output: []
 

Constraints:

The number of nodes in the list is in the range [0, 5 * 104].
-105 <= Node.val <= 105
 

Follow up: Can you sort the linked list in O(n logn) time and O(1) memory (i.e. constant space)?
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
    ListNode* findMiddle(ListNode* head){
        ListNode* slow = head;
        ListNode* fast = head->next;
        while(fast != NULL && fast->next != NULL){
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;
    }
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* t1 = list1;
        ListNode* t2 = list2;
        ListNode* dummyNode = new ListNode(-1);
        ListNode* temp = dummyNode;
        while(t1 != NULL && t2 != NULL){
            if(t1->val < t2->val){
                temp->next = t1;
                temp = t1;
                t1 = t1->next;
            }
            else{
                temp->next = t2;
                temp = t2;
                t2 = t2->next;
            }
        }
        if(t1) temp->next = t1;
        else temp->next = t2;
        return dummyNode->next;
    }
    ListNode* sortList(ListNode* head) {
        if(head == NULL || head->next == NULL){
            return head;
        }
        ListNode* middle = findMiddle(head);
        ListNode* right = middle->next;
        middle->next = nullptr;
        ListNode* left = head;

        left = sortList(left);
        right = sortList(right);
        return mergeTwoLists(left, right);
    }
};
```
---
## Copy List With Random Pointer(138. Leetcode): 

<P>
  Difficulty: Medium 

  A linked list of length n is given such that each node contains an additional random pointer, which could point to any node in the list, or null.

Construct a deep copy of the list. The deep copy should consist of exactly n brand new nodes, where each new node has its value set to the value of its corresponding original node. Both the next and random pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. None of the pointers in the new list should point to nodes in the original list.

For example, if there are two nodes X and Y in the original list, where X.random --> Y, then for the corresponding two nodes x and y in the copied list, x.random --> y.

Return the head of the copied linked list.

The linked list is represented in the input/output as a list of n nodes. Each node is represented as a pair of [val, random_index] where:

val: an integer representing Node.val
random_index: the index of the node (range from 0 to n-1) that the random pointer points to, or null if it does not point to any node.
Your code will only be given the head of the original linked list.

 

Example 1:
<img width="1900" height="386" alt="image" src="https://github.com/user-attachments/assets/369a7b35-d23c-4399-bf88-214ffcfc7601" />


Input: head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
Output: [[7,null],[13,0],[11,4],[10,2],[1,0]]
Example 2:

<img width="1670" height="272" alt="image" src="https://github.com/user-attachments/assets/b8af7163-fab2-4ee8-ab68-500d41a19752" />

Input: head = [[1,1],[2,1]]
Output: [[1,1],[2,1]]
Example 3:

<img width="1890" height="330" alt="image" src="https://github.com/user-attachments/assets/b2d5e07b-42d3-4ffb-99dc-13a43b671b0e" />


Input: head = [[3,null],[3,0],[3,null]]
Output: [[3,null],[3,0],[3,null]]
 

Constraints:

0 <= n <= 1000
-104 <= Node.val <= 104
Node.random is null or is pointing to some node in the linked list.
</P>

### Solution: 

```
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/

class Solution {
public:
    void insertCopyInBetween(Node* head){
        Node* temp = head;
        while(temp != NULL){
            Node* nextElement = temp->next;
            Node* copy = new Node(temp->val);

            copy->next = nextElement;
            temp->next = copy;

            temp = nextElement;
        }
    }
    void connectRandomPointers(Node* head){
        Node* temp = head;
        while(temp != NULL){
            Node* copyNode = temp->next;

            if(temp->random){
                copyNode->random = temp->random->next;
            }
            else{
                copyNode->random = nullptr;
            }
            temp = temp->next->next;
        }
    }
    Node* getDeepCopyList(Node* head){
        Node* temp = head;
        Node* dummyNode = new Node(-1);
        Node* res = dummyNode;

        while(temp != NULL){
            res->next = temp->next;
            res = res->next;

            temp->next = temp->next->next;
            temp = temp->next;
        }
        return dummyNode->next;
    }
    Node* copyRandomList(Node* head) {
        insertCopyInBetween(head);
        connectRandomPointers(head);
        return getDeepCopyList(head);
    }
};
```
---
