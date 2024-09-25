# Sorting Algroithm

## Introduction

Sorting algorithms are a set of instructions that take an array or list as an input and arrange the items into a particular order. The output can be in non-decreasing, non-increasing, or any other predefined order.

## Time Complexity

| Algorithm | Best | Average | Worst | Space |
| --- | --- | --- | --- | --- |
| [Bubble Sort ](./bubbleSort.md)| O(n) | O(n^2) | O(n^2) | O(1) |
| [Selection Sort](./selectSort.md) | O(n^2) | O(n^2) | O(n^2) | O(1) |
| [Insertion Sort](./insertSort.md) | O(n) | O(n^2) | O(n^2) | O(1) |
| [Merge Sort](./mergeSort.md) | O(n log n) | O(n log n) | O(n log n) | O(n) |
| [Quick Sort](./quickSort.md) | O(n log n) | O(n log n) | O(n^2) | O(log n) |
| [Heap Sort](./heapSort.md) | O(n log n) | O(n log n) | O(n log n) | O(1) |


## Rule of Thumb

```text
10^9 operations per second
```

For example, if the time limit is 1 second, then the maximum size of the array can be sorted using O(n log n) algorithm is 10^8.

## Reference

- [Big-O Complexity Chart](https://www.bigocheatsheet.com/)