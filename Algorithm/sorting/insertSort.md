# Insertion Sort

Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort.

![image](https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif)

## Complexity

| Best | Average | Worst | Space |
| --- | --- | --- | --- |
| O(n) | O(n^2) | O(n^2) | O(1) |

## Implementation

### Python

```python
def insertSort(arr):
    for i in range(1, len(arr)):
        val = arr[i]
        j = i - 1
        while j >= 0 and val < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = val
```

### C++

```cpp
void insertSort(vector<int>& arr) {
    for (int i = 1; i < arr.size(); i++) {
        int val = arr[i];
        int j = i - 1;
        while (j >= 0 && val < arr[j]) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = val;
    }
}
```
