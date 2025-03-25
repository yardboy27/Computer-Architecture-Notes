# Review of Memory Hierarchy
These are notes from Appendix B: Review of Memory Hierarchy in the book Computer Architecture: A Quantitative Approach

## Introduction

### Cache
**Cache** is the name given to the highest or first level of the memory hierarchy encountered once the address leaves the processor. A **cache hit** is when the processor finds a requested data item in the cache. A **cache miss** is when the processor does not find the data item it needs in the cache. A cache miss is typically handled by hardware and causes the processors using in-order execution to pause, or stall, until the data are available. (pg. B-2)

### Block (or line run)
A **block** is a fixed-size collection of data containing the requested word and is retrieved from the main memory and placed into the **cache**.

### Temporal Locality
**Temporal locality** tells us that we are likely to need the word again in teh near future, so it is useful to place it in the cache where it can be accessed quickly. When you hear of temporal locality, think time.

### Spatial Locality
**Spacial locality** tells us that there is a high probability that the other data in teh block will be needed soon. When you hear of spatial locality, think of space or distance; things that are close together have a higher probability of being related and possibly needed together.

### Latency
**Latency** determines the time to retrieve the first word of the block. The time required for the cache miss depends on both the latency and bandwidth of memory.

### Bandwidth
**Bandwidth** determines the time to retrieve the rest of the word of the block. The time required for the cache miss depends on both the latency and bandwidth of memory.

### Virtual Memory
**Virtual memory** means some objects may reside on disk. Not all objects referenced by a program need to reside in main memory. The address space is usually broken into fixed-size blocks, called pages.

### Pages
**Pages** are fixed-size blocks; virtual memory address space is typically broken up into pages. At any time, each page resides either in main memory or on disk. When the processor references an item within a page that is not present in the cache or main memory, a palt occurs, and the entire page is moved from the disk to main memory. Page faults take a long time, so they are typically handled in software and the processor is not stalled. 

### CPU Execution Time Formula
With our knowledge of the cache, and the existence of memory stall cycles, we can edit our CPU execution time formula to the following:
\[
\text{CPU execution time} = (\text{CPU clock cycles} + \text{Memory stall cycles} \times \text{Clock cycle time}
\]

### Memory Stall Cycles Equation
This formula is simplified, as we combine the reads and writes and find the average miss rate and miss penalty for reads and writes.
\[
\text{Memory stall cycles} = \text{Number of misses} \times \text{Miss penalty}
\]

\[
\text{Memory stall cycles} = \text{IC} \times \frac{Misses}{Instruction} \times \text{Miss penalty}
\]

\[
\text{Memory stall cycles} = \text{IC} \times \frac{Memory accesses}{Instruction} \times \text{Miss rate} \times \text{Miss penalty}
\]

### Memory Stall Cycles Equation (unsimplified)
//TODO

### Four Memory Hierarchy Questions
These questions help us understand the different trade-offs of memory at different levels of a hierarchy; hence we ask these four questions on every example.
Q1: Where can a block be placed in the upper level? (block placement)
Q2: How is a block found if it is in the upper level? (block identification)
Q3: Which block should be replaced on a miss? (block replacement)
Q4: What happens on a write? (write strategy)
