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
