# Selection Sort

Selection Sort is a simple sorting algorithm that divides the input list into two parts: the sublist of items already sorted and the sublist of items remaining to be sorted. The algorithm selects the smallest element from the unsorted sublist and swaps it with the leftmost unsorted element. The selection sort algorithm is not stable.

![image](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)

## Complexity

| Best | Average | Worst | Space |
| --- | --- | --- | --- |
| O(n^2) | O(n^2) | O(n^2) | O(1) |

## Implementation

### Python

```python
def selectionSort(arr):
    for i in range(len(arr)):
        min_index = i
        for j in range(i+1, len(arr)):
            if arr[j] < arr[min_index]:
                min_index = j
        arr[i], arr[min_index] = arr[min_index], arr[i]
```

### C++

```cpp
void selectionSort(int arr[], int n) {
    for (int i = 0; i < n-1; i++) {
        int min_index = i;
        for (int j = i+1; j < n; j++) {
            if (arr[j] < arr[min_index]) {
                min_index = j;
            }
        }
        swap(arr[i], arr[min_index]);
    }
}
```
