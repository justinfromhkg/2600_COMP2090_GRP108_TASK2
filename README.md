1. Introduction to the Min‑Heap Data Structure
A min‑heap is a complete binary tree in which the value of each node is less than or equal to the values of its children. Consequently, the smallest element always resides at the root. This property makes the min‑heap an ideal implementation for a priority queue, where the element with the highest priority (lowest value) is always extracted first.

1.1 Abstract Data Type (ADT) of a Min‑Heap
The essential operations of a min‑heap are:

insert(x) – Add a new element x while maintaining the heap property.
Procedure: Place x at the next available position (end of the array) and then “bubble up” (or “heapify up”) by swapping it with its parent until the heap property is restored. Time complexity: O(log n).

extract_min() – Remove and return the smallest element (the root).
Procedure: Replace the root with the last element, remove the last, and then “bubble down” (or “heapify down”) by swapping the new root with its smaller child until the heap property is restored. Time complexity: O(log n).

peek() – Return the smallest element without removing it. Time complexity: O(1).

heapify() – Convert an arbitrary array into a min‑heap. This can be done in O(n) time using the bottom‑up approach (Floyd’s algorithm).

1.2 Applications of Min‑Heaps
Min‑heaps are widely used in:

Priority queues – e.g., task scheduling in operating systems, Dijkstra’s shortest path algorithm.

Event‑driven simulation – handling events in chronological order.

Huffman coding – building the Huffman tree by repeatedly merging two smallest frequencies.

Selection algorithms – finding the k‑th smallest element efficiently.

2. Introduction to Heap Sort
Heap sort is a comparison‑based sorting algorithm that uses a binary heap data structure. It proceeds in two phases:

Build a heap – Transform the input array into a max‑heap (for ascending order) or a min‑heap (for descending order).

Extract elements repeatedly – Swap the root (largest/smallest) with the last element, reduce the heap size, and restore the heap property. This yields a sorted sequence.

For ascending order, a max‑heap is used. However, the underlying mechanism is identical for a min‑heap; we simply extract the smallest repeatedly to obtain descending order. In this report we illustrate heap sort using a min‑heap to produce a descendingly sorted array.

2.1 Algorithm Steps (using a min‑heap)
Given an array A of length n:

Build a min‑heap from A (using the heapify procedure).

Repeat for i = n‑1 down to 1:

Swap A[0] (the current minimum) with A[i].

Reduce the heap size by 1 (so the extracted element stays in its final position).

Restore the min‑heap property on the reduced heap by calling heapify_down on the root.

After the loop, the array is sorted in descending order.

2.2 Time Complexity Analysis
Building the heap: Using Floyd’s algorithm, building a heap from an unsorted array takes O(n) time.

Extraction phase: Each of the n‑1 extractions requires a heapify_down operation, which costs O(log n). Hence the total for this phase is O(n log n).

Overall: Heap sort runs in O(n log n) in the best, average, and worst cases because the heap structure guarantees logarithmic depth.

Space complexity: Heap sort is in‑place; it uses only a constant amount of extra space (O(1)) besides the input array. However, it is not stable because the swapping operation may change the relative order of equal elements.

2.3 Example Walkthrough
Consider the array [5, 3, 8, 1, 9, 2]. We want to sort it in descending order using a min‑heap.

Step 1 – Build min‑heap:
The array is rearranged into a min‑heap: [1, 3, 2, 5, 9, 8] (see Appendix A for the tree representation and the heapify process).

Step 2 – Extraction and swapping:

Swap root (1) with last element (8) → [8, 3, 2, 5, 9, 1]. Heap size reduced to 5. Restore heap → [2, 3, 8, 5, 9, 1].

Swap root (2) with last element (9) → [9, 3, 8, 5, 2, 1]. Restore heap → [3, 5, 8, 9, 2, 1].

Continue until all elements are extracted. The final descending order is [9, 8, 5, 3, 2, 1].

A detailed step‑by‑step illustration is provided in Appendix A.
