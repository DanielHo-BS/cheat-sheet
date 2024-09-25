# Bobble Sort

Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the

![image](https://upload.wikimedia.org/wikipedia/commons/c/c8/Bubble-sort-example-300px.gif)


## Complexity

| Best | Average | Worst | Space |
| --- | --- | --- | --- |
| O(n) | O(n^2) | O(n^2) | O(1) |

## Implementation

### Python

```python
def bubbleSort(arr):
    for i in range(len(arr)):
       for j in range(1, len(arr)-i):
            # Swap if the element found is greater
           if arr[j-1] > arr[j]:
               arr[j-1], arr[j] = arr[j], arr[j-1]

```

### c++

```cpp
void bubbleSort(vector<int>& arr) {
    for (int i = 0; i < arr.size(); i++) {
        for (int j = 1; j < arr.size() - 1; j++) {
            if (arr[j - 1] > arr[j]) {
                swap(arr[j - 1], arr[j]);
            }
        }
    }
}
```
