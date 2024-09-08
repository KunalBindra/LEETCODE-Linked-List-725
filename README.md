# LEETCODE-Linked-List-725
Let's go through a **dry run** of this `splitListToParts` method with an example:

### Example:

We have a linked list:
```
1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7
```

We are given `k = 3`, which means we need to split this list into 3 parts.

### Step 1: Compute the length of the list
The helper function `getLength` is used to determine the length of the linked list.
- Start with `length = 0`
- Traverse the list: `1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7`
- After traversing, the total length `n = 7`.

### Step 2: Calculate subLength and remainder
We need to split the list into `k = 3` parts.
- `subLength = length / k = 7 / 3 = 2` (each part will have at least 2 nodes)
- `remainder = length % k = 7 % 3 = 1` (the first 1 part will have an extra node)

### Step 3: Initialize variables
- Create an array `ans` of size `k = 3` to store the head of each part.
- `prev = null` and `head` is initialized to the start of the list (`head = 1`).

### Step 4: Loop through each part and split the list
We will now iterate `k = 3` times to split the list.

#### First iteration (i = 0):
- Set `ans[0] = head` (i.e., `ans[0] = 1`).
- For this part, since `remainder > 0`, we need `subLength + 1 = 2 + 1 = 3` nodes.
- Traverse `1 -> 2 -> 3`.
- Set `prev.next = null` to disconnect the first part. Now the list looks like:
  ```
  1 -> 2 -> 3
  4 -> 5 -> 6 -> 7
  ```
- Move `head` to `4` and decrement `remainder` to `0`.

#### Second iteration (i = 1):
- Set `ans[1] = head` (i.e., `ans[1] = 4`).
- Since `remainder = 0`, this part will have `subLength = 2` nodes.
- Traverse `4 -> 5`.
- Set `prev.next = null` to disconnect the second part. Now the list looks like:
  ```
  1 -> 2 -> 3
  4 -> 5
  6 -> 7
  ```
- Move `head` to `6`.

#### Third iteration (i = 2):
- Set `ans[2] = head` (i.e., `ans[2] = 6`).
- This part will have `subLength = 2` nodes.
- Traverse `6 -> 7`.
- Set `prev.next = null`. Now the list looks like:
  ```
  1 -> 2 -> 3
  4 -> 5
  6 -> 7
  ```

### Step 5: Return the result
The final result is an array of linked lists:
```
[
  1 -> 2 -> 3,
  4 -> 5,
  6 -> 7
]
```

### Dry Run Summary:
1. The function correctly splits the linked list into three parts, with the first part containing one extra node due to the remainder.
2. Each part is as equal in size as possible, and the first part contains the extra node from the remainder.

