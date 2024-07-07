# 100 Days Verification Challenge - Day 20 - Cache memories

## 1. Explain various cache mapping techniques with an example.

### 1. Direct Mapping
In direct mapping, each block of main memory maps to only one possible cache line. The mapping is determined by dividing the main memory address into three parts: tag, index, and block offset.

**Example**:
- Main memory size: 1 MB = 2^20 bytes
- Cache size: 4 KB = 2^12 bytes
- Block size: 16 bytes 4 words of 4 bytes each

**Calculation**:
- Number of cache lines: 2^12 bytes / 16 bytes/line = 2^8 = 256 lines
- Address division 20-bit address:
  - Block offset: 2^4 = 16 bytes 4 bits
  - Index: 2^8 = 256 lines 8 bits
  - Tag: Remaining 20 - 8 - 4 = 8 bits

**Mapping**:
Address (20 bits) -> Tag (8 bits) + Index (8 bits) + Block Offset (4 bits)

### 2. Fully Associative Mapping
In fully associative mapping, any block of main memory can be placed in any cache line. The address is divided into two parts: tag and block offset.

**Example**:
- Same as above

**Calculation**:
- Block offset: 2^4 = 16 bytes (4 bits)
- Tag: Remaining 20 - 4 = 16 bits

**Mapping**:
Address (20 bits) -> Tag (16 bits) + Block Offset (4 bits)

### 3. Set Associative Mapping 4-way
In set associative mapping, the cache is divided into sets, and each set contains multiple lines ways. A block can be placed in any line within a specific set. Here, we have a 4-way set associative cache.

**Example**:
- Same as above

**Calculation**:
- Number of sets: 2^12 bytes / (16 bytes/block * 4 ways) = 2^6 = 64 sets
- Address division 20-bit address:
  - Block offset: 2^4 = 16 bytes (4 bits)
  - Set index: 2^6 = 64 sets (6 bits)
  - Tag: Remaining 20 - 6 - 4 = 10 bits

**Mapping**:
Address (20 bits) -> Tag (10 bits) + Set Index (6 bits) + Block Offset (4 bits)

## 2.  What are pros & cons of every mapping technique?

### Direct Mapping
**Pros**:
- Simple implementation
- Fast access time due to straightforward indexing

**Cons**:
- High conflict miss rate as multiple blocks compete for the same cache line
- Less flexible

### Fully Associative Mapping
**Pros**:
- Low conflict miss rate as any block can go to any cache line
- High flexibility

**Cons**:
- Complex hardware implementation
- Longer access time due to the need to search all cache lines for a match

### Set Associative Mapping
**Pros**:
- Balanced compromise between direct and fully associative mapping
- Lower conflict miss rate compared to direct mapping
- More flexible than direct mapping

**Cons**:
- More complex hardware than direct mapping
- Access time slower than direct mapping but faster than fully associative mapping

## 3. Which mapping technique is most optimized?

**Set Associative Mapping** is generally considered the most optimized technique. It provides a good balance between the simplicity of direct mapping and the flexibility of fully associative mapping, reducing the conflict miss rate while maintaining a reasonable hardware complexity and access time.

## 4. I have a RAM of 1 MB & cache memory of 4 KB a word addressable in a system, where 1 word is 4 bytes. Consider every frame consists of 4 words, which means every frame hał 4*4 bytes = 16 bytes. How are we going to map the frames from RAM in cache memory for each mapping technique? In case of set-associative consider 4-way

Tips to Solve this numerical:

Fully Associative - any frame can be placed in any cache line, so no need to solve. Any block of RAM can be moved to any cache line.

Direct mapping - find out which frame nos. in RAM will be mapped to which cache lines.

Set Associative - first calculate how many bits are for tag, set & frame offset. Now, calculate which frames in RAM can be mapped to which set it can go to any of the 4 ways in the set.

### Direct Mapping

**Calculation**:
- Number of cache lines: 2^12 bytes / 16 bytes = 256 lines
- Address division:
  - Block offset: 4 bits
  - Index: 8 bits
  - Tag: 8 bits

**Mapping**:
Frame number in RAM is divided by the number of cache lines to get the cache line number.

**Example**:
Frame 0 -> Cache line 0
Frame 1 -> Cache line 1
...
Frame 255 -> Cache line 255
Frame 256 -> Cache line 0 (256 % 256)
Frame 257 -> Cache line 1 (257 % 256)
...
Frame 511 -> Cache line 255

### Fully Associative Mapping

As any frame can be placed in any cache line, no specific mapping is required.

### Set Associative Mapping 4-way

**Calculation**:
- Number of sets: 2^12 bytes / 16 bytes times 4 = 64 sets
- Address division:
  - Block offset: 4 bits
  - Set index: 6 bits
  - Tag: 10 bits

**Mapping**:
Frame number (in RAM) is divided by the number of sets to get the set number.

**Example**:
Frame 0 -> Set 0
Frame 1 -> Set 1
...
Frame 63 -> Set 63
Frame 64 -> Set 0 (64 % 64)
Frame 65 -> Set 1 (65 % 64)
...
Frame 127 -> Set 63

Within each set, a frame can be placed in any of the 4 ways (lines) available in that set.
