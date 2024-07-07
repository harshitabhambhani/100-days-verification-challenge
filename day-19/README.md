# 100 Days Verification Challenge - Day 19 - DMA, Synchronization & Paging

## 1. Explain DMA (Direct Memory Access) with diagrams.

**Explanation:**
Direct Memory Access (DMA) is a system that allows certain hardware subsystems within a computer to access system memory independently of the CPU. This mechanism improves performance by freeing the CPU from being involved in the data transfer operations between the memory and the peripherals.

**Diagram:**
A basic DMA system consists of the following components:
- **CPU**: Initiates the DMA transfer.
- **DMA Controller**: Manages the data transfer between the memory and the peripheral devices.
- **Memory**: The location where data is stored.
- **Peripheral Devices**: Devices like disk drives, sound cards, network cards, etc., that need to transfer data to/from memory.

![image](https://github.com/harshitabhambhani/100-days-verification-challenge/assets/109619297/9cf68b48-e63a-4e45-a741-954901ae3fb8)

**DMA Operation:**
1. **Setup**: The CPU initializes the DMA controller by providing the memory address, the number of bytes to transfer, and the direction of transfer (read/write).
2. **Execution**: The DMA controller takes control of the system bus to manage the data transfer directly between memory and the peripheral device.
3. **Completion**: Once the transfer is complete, the DMA controller sends an interrupt signal to the CPU to notify it of the completion.

## 2. What are advantages & disadvantages of DMA?

**Advantages:**
1. **Improved CPU Efficiency**: Frees the CPU from managing data transfer, allowing it to perform other tasks.
2. **Faster Data Transfer**: Direct memory access can be faster than CPU-mediated transfers.
3. **Reduced CPU Overhead**: Reduces the number of interrupts and context switches, decreasing CPU overhead.
4. **Parallelism**: Allows simultaneous data processing and data transfer.

**Disadvantages:**
1. **Complexity**: Requires additional hardware (DMA controller) and more complex system design.
2. **Cost**: Increased cost due to additional hardware components.
3. **Resource Contention**: Can lead to bus contention as multiple devices may compete for bus access.
4. **Latency**: DMA setup and interrupt handling add some latency.

## 3. What is meant by Synchronization in computer architecture?

**Synchronization** in computer architecture refers to coordinating the execution of processes or threads to ensure that they operate correctly when accessing shared resources. It prevents race conditions, ensures data consistency, and maintains the correct sequence of operations.

## 4. What are various synchronization techniques?

1. **Mutexes (Mutual Exclusions)**: Prevent multiple threads from accessing a shared resource simultaneously.
2. **Semaphores**: Similar to mutexes but can allow a certain number of threads to access the resource simultaneously.
3. **Spinlocks**: Busy-wait locks that repeatedly check if the lock is available.
4. **Monitors**: High-level synchronization constructs that combine mutual exclusion with the ability to wait for a condition.
5. **Barriers**: Ensure that all threads or processes reach a certain point in the program before continuing.
6. **Condition Variables**: Allow threads to wait for certain conditions to be met before proceeding.

## 5. What is Paging? What is a Page Table?

**Paging** is a memory management scheme that eliminates the need for contiguous allocation of physical memory. It divides the virtual memory into fixed-size pages and the physical memory into blocks of the same size called frames. The operating system maintains a page table to map virtual pages to physical frames.

**Page Table**: A data structure used by the operating system to keep track of the mapping between virtual addresses and physical addresses.

## 6. Find the total number of frames if size of the main memory is 2^30 bytes, the byte size is 4KB and the size of each page table entry is 32-bit. 
(Hint: Size of main memory = Total number of frames x page size.)

Given:
- Main memory size: 2^30 bytes
- Page size: 4 KB = 2^12 bytes

**Formula**:
Total number of frames = Size of main memory/Page size

Total number of frames = 2^30/2^12 = 2^18

Thus, the total number of frames is 2^18

## 7. Consider a system with page table entries of 8 bytes each. If the size of the page table is 256 bytes, what is the number of entries in the page table?
(Hint: Size of page table - Number of entries in the page table x page table entry size)

Given:
- Page table entry size: 8 bytes
- Size of page table: 256 bytes

**Formula**:
Number of entries = Size of page table/Page table entry size

Number of entries = 256/8 = 32

Thus, the number of entries in the page table is 32.

## 8. Consider a machine with 32-bit logical addresses, 4 KB page size and page table entries of 4 bytes each. Find the size of the page table in bytes. Assume the memory is byte addressable.
(Hint: Size of page table = Number of entries in page table x Page table entry size 
Number of entries in page table = Process size / Page size)

Given:
- Logical address size: 32 bits
- Page size: 4 KB = 2^12 bytes
- Page table entry size: 4 bytes

**Number of entries in the page table**:
Number of entries = Logical address space/Page size
Number of entries = 2^32/2^12 = 2^20

**Size of the page table**:
Size of the page table = Number of entries * Page table entry size
Size of the page table = 2^20 * 4 bytes = 2^22 bytes

Thus, the size of the page table is 2^22 bytes, which is 4 MB.
