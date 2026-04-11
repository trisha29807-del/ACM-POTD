# Problem of the Day - Day 20

## Problem Name:
Make the String Great

## Problem Link:
https://leetcode.com/problems/make-the-string-great/description/

## Approach:
1. Traverse the string character by character.
2. Maintain a stack (or a string used as a stack).
3. For each character:
    * If the stack is not empty and 
        abs(top - current) == 32, then pop the top (they cancel).
    * Otherwise, push the current character onto the stack.
4. The final stack content is the required string.

## Code:
```cpp
class Solution {
public:
    string makeGood(string s) {
        string st = ""; // using string as stack

        for (char c : s) {
            if (!st.empty() && abs(st.back() - c) == 32) {
                st.pop_back();
            } else {
                st.push_back(c);
            }
        }
        return st;
    }
};
```
## Screenshot of Accepted Solution:
![Accepted Solution](POTD-Day20.png)

## Complexity:

* Time Complexity: O(n) (each character is processed at most twice)
* Space Complexity: O(n) in worst case (if no characters cancel out)