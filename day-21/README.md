# 100 Days Verification Challenge - Day 21 - Cache replacement algorithms

## 1. Why Does Direct Mapping Not Need Any Replacement Algorithm?

In direct mapping, each block of main memory maps to exactly one possible cache line. This fixed mapping means that when a new block is loaded into the cache, it always goes into a predetermined cache line. There is no choice or decision to make about where the block should go, hence no need for a replacement algorithm. If the cache line is already occupied by a different block, it simply gets overwritten.

## 2. Explain the Cache Replacement Algorithms

### i. Least Recently Used (LRU)
The LRU algorithm replaces the block that has not been used for the longest period of time. It assumes that blocks that have been used recently will likely be used again soon.

**Example**:
If the cache can hold 4 frames and the access sequence is [A, B, C, D, A, E], the cache will contain:
- After A, B, C, D: [A, B, C, D]
- Access A again (A is already in the cache, move it to the most recently used position)
- After E: [E, B, C, D] (A was the least recently used, so it is replaced by E)

### ii. Most Recently Used (MRU)
The MRU algorithm replaces the block that was most recently used. This is less common in practice because it often results in suboptimal cache performance.

**Example**:
Using the same sequence [A, B, C, D, A, E]:
- After A, B, C, D: [A, B, C, D]
- Access A again (A is most recently used)
- After E: [A, E, C, D] (A is replaced by E)

### iii. First In First Out (FIFO)
The FIFO algorithm replaces the oldest block in the cache, regardless of how frequently or recently it was accessed.

**Example**:
Using the same sequence [A, B, C, D, A, E]:
- After A, B, C, D: [A, B, C, D]
- Access A again (A is already in the cache, no replacement)
- After E: [E, B, C, D] (A was the first block in the cache, so it is replaced by E)

## 3. A cache memory can hold 8 frames from RAM. Consider the cache is initially EMPTY. RAM has 128 frames of 1 byte each in a byte addressable system. The processor requested frames in following sequence: 127, 8, 0, 127, 3, 5, 7, 9, 6, 3, 8, 0, 5, 11, 19, 8. Calculate the no. of cache misses for Fully associative cache mapping in  

### i. Least Recently Used (LRU)

Initial cache state: []

1. 127 (miss, add 127): [127]
2. 8 (miss, add 8): [127, 8]
3. 0 (miss, add 0): [127, 8, 0]
4. 127 (hit, move 127 to the end): [8, 0, 127]
5. 3 (miss, add 3): [8, 0, 127, 3]
6. 5 (miss, add 5): [8, 0, 127, 3, 5]
7. 7 (miss, add 7): [8, 0, 127, 3, 5, 7]
8. 9 (miss, add 9): [8, 0, 127, 3, 5, 7, 9]
9. 6 (miss, add 6): [8, 0, 127, 3, 5, 7, 9, 6]
10. 3 (hit, move 3 to the end): [8, 0, 127, 5, 7, 9, 6, 3]
11. 8 (hit, move 8 to the end): [0, 127, 5, 7, 9, 6, 3, 8]
12. 0 (hit, move 0 to the end): [127, 5, 7, 9, 6, 3, 8, 0]
13. 5 (hit, move 5 to the end): [127, 7, 9, 6, 3, 8, 0, 5]
14. 11 (miss, add 11, remove 127): [7, 9, 6, 3, 8, 0, 5, 11]
15. 19 (miss, add 19, remove 7): [9, 6, 3, 8, 0, 5, 11, 19]
16. 8 (hit, move 8 to the end): [9, 6, 3, 0, 5, 11, 19, 8]

**Total cache misses for LRU**: 10

### ii. Most Recently Used (MRU)

Initial cache state: []

1. 127 (miss, add 127): [127]
2. 8 (miss, add 8): [127, 8]
3. 0 (miss, add 0): [127, 8, 0]
4. 127 (hit, remove 127 and add it again): [8, 0, 127]
5. 3 (miss, add 3): [8, 0, 127, 3]
6. 5 (miss, add 5): [8, 0, 127, 3, 5]
7. 7 (miss, add 7): [8, 0, 127, 3, 5, 7]
8. 9 (miss, add 9): [8, 0, 127, 3, 5, 7, 9]
9. 6 (miss, add 6): [8, 0, 127, 3, 5, 7, 9, 6]
10. 3 (hit, remove 3 and add it again): [8, 0, 127, 5, 7, 9, 6, 3]
11. 8 (hit, remove 8 and add it again): [0, 127, 5, 7, 9, 6, 3, 8]
12. 0 (hit, remove 0 and add it again): [127, 5, 7, 9, 6, 3, 8, 0]
13. 5 (hit, remove 5 and add it again): [127, 7, 9, 6, 3, 8, 0, 5]
14. 11 (miss, replace the most recently used which is 5): [127, 7, 9, 6, 3, 8, 0, 11]
15. 19 (miss, replace the most recently used which is 11): [127, 7, 9, 6, 3, 8, 0, 19]
16. 8 (hit, remove 8 and add it again): [127, 7, 9, 6, 3, 0, 19, 8]

**Total cache misses for MRU**: 10

### iii. First In First Out (FIFO)

Initial cache state: []

1. 127 (miss, add 127): [127]
2. 8 (miss, add 8): [127, 8]
3. 0 (miss, add 0): [127, 8, 0]
4. 127 (hit): [127, 8, 0]
5. 3 (miss, add 3): [127, 8, 0, 3]
6. 5 (miss, add 5): [127, 8, 0, 3, 5]
7. 7 (miss, add 7): [127, 8, 0, 3, 5, 7]
8. 9 (miss, add 9): [127, 8, 0, 3, 5, 7, 9]
9. 6 (miss, add 6): [127, 8, 0, 3, 5, 7, 9, 6]
10. 3 (hit): [127, 8, 0, 3, 5, 7, 9, 6]
11. 8 (hit): [127, 8, 0, 3, 5, 7, 9, 6]
12. 0 (hit): [127, 8, 0, 3, 5, 7, 9, 6]
13. 5 (hit): [127, 8, 0, 3, 5, 7, 9, 6]
14. 11 (miss, replace the oldest which is 127): [8, 0, 3, 5, 7, 9, 6, 11]
15. 19 (miss, replace the oldest which is 8): [0, 3, 5, 7, 9, 6, 11, 19]
16. 8 (miss, replace the oldest which is 0): [3, 5, 7, 9,
