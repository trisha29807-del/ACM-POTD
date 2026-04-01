# Problem of the Day - Day 11

## Problem Name:
Merge Two Sorted Lists

## Problem Link:
https://leetcode.com/problems/merge-two-sorted-lists/description/

## Approach:

1. Create a dummy node
    * Acts as a safe starting point before the real head
    * Helps avoid separate handling for the first node
2. Initialize a pointer temp
    * Starts at dummy
    * Used to attach nodes step by step
3. Traverse both lists simultaneously
    * Compare the current nodes of l1 and l2
    * Attach the smaller node to temp->next
    * Move temp and the list pointer you used forward
4. Attach remaining nodes
    * If one list finishes before the other
    * Attach the rest of the non-empty list to temp->next
5. Return the merged list
    * Skip the dummy node
    * Real head = dummy.next
6. Benefits of dummy node
    * Avoids handling head separately
    * Handles edge cases cleanly (empty lists)
    * Shorter and less error-prone code 

## Code:
```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode dummy(0);
        ListNode* temp = &dummy;

        while (l1 && l2) {
            if (l1->val < l2->val) {
                temp->next = l1;
                l1 = l1->next;
            } else {
                temp->next = l2;
                l2 = l2->next;
            }
            temp = temp->next;
        }

        if (l1)
            temp->next = l1;
        else
            temp->next = l2;

        return dummy.next;
    }
};
```
## Screenshot of Accepted Solution:
![Accepted Solution](POTD-Day11.png)

## Complexity:

* Time Complexity: O(n + m)
n = length of first list
m = length of second list

* Space Complexity: O(1)
