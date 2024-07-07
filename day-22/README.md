# 100 Days Verification Challenge - Day 22 - Cache coherence

## 1. What is the Cache Coherency Problem?

The cache coherency problem arises in multiprocessor systems where multiple caches are used. Each processor may have its own cache, and if they all store a copy of the same memory location, inconsistencies can occur. When one processor updates its cached copy of a memory location, the other processors' caches may still contain the old value, leading to data inconsistency. The cache coherency problem refers to ensuring that all caches have a consistent view of the memory.

## 2. Explain snooping mechanism.

The snooping mechanism is a cache coherency technique used in multiprocessor systems. It involves each cache monitoring (or "snooping" on) a common bus to observe the memory operations of other processors. When a processor performs a read or write operation, it broadcasts this operation on the bus. All caches then check if they have a copy of the affected memory location and update or invalidate their copies accordingly.

## 3. What is cache coherency protocol. Explain below protocols:

Cache coherency protocols are sets of rules and mechanisms to maintain consistency across caches in a multiprocessor system. Two primary types are write-invalidate and write-update protocols.

### i. Write-Invalidate Protocol

In the write-invalidate protocol, when a processor writes to a memory location, it invalidates that memory location in all other caches. This means that other caches must fetch the updated value from memory before they can use it again.

**Example**:
- Processor 1 writes to memory location X.
- A message is sent on the bus to invalidate memory location X in all other caches.
- Other processors invalidate their copy of X.
- When another processor needs X, it must read it from the memory again.

**Pros**:
- Reduces the frequency of bus transactions for write operations.
- Ensures only one processor modifies the memory location at a time.

**Cons**:
- Other processors must fetch the memory location again after invalidation.

### ii. Write-Update Protocol

In the write-update protocol, when a processor writes to a memory location, it updates that memory location in all other caches. This means that all caches keep their copies of the memory location updated.

**Example**:
- Processor 1 writes to memory location X.
- A message is sent on the bus to update memory location X in all other caches.
- Other processors update their copy of X.

**Pros**:
- Ensures all caches have the most recent value of the memory location.
- Reduces the need to fetch data from memory again.

**Cons**:
- Increases the frequency of bus transactions for write operations.

## 4. Explain operation of MESI Protocol (Cache Coherency).

The MESI protocol (Modified, Exclusive, Shared, Invalid) is a widely used cache coherency protocol that ensures a consistent view of memory across multiple caches. Each cache line can be in one of four states:

- **Modified (M)**: The cache line has been modified and is different from main memory. This cache has the only valid copy.
- **Exclusive (E)**: The cache line is the same as in main memory, and this cache has the only valid copy.
- **Shared (S)**: The cache line is the same as in main memory, and multiple caches may have this copy.
- **Invalid (I)**: The cache line is not valid and must be fetched from memory or another cache.

**Operation of MESI Protocol**:

1. **Read Miss**:
   - If a processor reads a memory location not in its cache, it broadcasts a read request.
   - If another cache has the data in Modified or Exclusive state, it supplies the data and changes its state to Shared.
   - If the data is not in any cache, it is fetched from memory, and the cache line state is set to Shared.

2. **Write Miss**:
   - If a processor writes to a memory location not in its cache, it broadcasts an invalidate request.
   - All other caches invalidate their copy of the data.
   - The writing processor fetches the data from memory or another cache, updates it, and sets the cache line state to Modified.

3. **Read Hit**:
   - If a processor reads a memory location in its cache and the state is Modified, Exclusive, or Shared, it simply uses the data without any bus transaction.

4. **Write Hit**:
   - If a processor writes to a memory location in its cache and the state is Shared, it broadcasts an invalidate request.
   - The cache line state is set to Modified.
   - If the state is Exclusive, it writes the data and changes the state to Modified.
   - If the state is Modified, it writes the data directly.

**Example**:
- Processor 1 reads memory location X (miss), fetches it, and sets it to Shared.
- Processor 2 writes to memory location X (invalidate), sets it to Modified.
- Processor 1 reads memory location X (invalidate), fetches it from Processor 2, and sets it to Shared.

**Pros**:
- Ensures consistency across caches.
- Efficient use of the bus.

**Cons**:
- More complex hardware implementation.
