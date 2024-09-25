# Heap Sort

Heap Sort is a comparison-based sorting algorithm that uses a binary heap data structure to sort elements. It divides the input list into two parts: a sorted part and an unsorted part. The algorithm repeatedly removes the largest element from the unsorted part and adds it to the sorted part.

![image](https://upload.wikimedia.org/wikipedia/commons/4/4d/Heapsort-example.gif)

## Complexity

| Best | Average | Worst | Space |
| --- | --- | --- | --- |
| O(n log n) | O(n log n) | O(n log n) | O(1) |

## Implementation

Use a max heap to sort the elements in ascending order.

### Python

```python
class HeapSort:
    def __init__(self, arr):
        self.arr = arr
        self.size = len(arr)

    def heapify(self, i):
        largest = i
        left = 2 * i + 1
        right = 2 * i + 2
        if left < self.size and self.arr[i] < self.arr[left]:
            largest = left
        if right < self.size and self.arr[largest] < self.arr[right]:
            largest = right
        if largest != i:
            self.arr[i], self.arr[largest] = self.arr[largest], self.arr[i]
            self.heapify(largest)

    def sort(self):
        # Build a max heap
        # Start from the last non-leaf node(n // 2 - 1)
        for i in range(self.size // 2 - 1, -1, -1):
            self.heapify(i)
        # Extract elements one by one for sorting
        # Move the root element to the end of the array
        # Reduce the size of the heap by 1 for each searching
        # Re heapify the root element without the last element
        for i in range(self.size - 1, 0, -1):
            self.arr[i], self.arr[0] = self.arr[0], self.arr[i]
            self.size -= 1
            self.heapify(0)
        return self.arr

# Example
arr = [12, 11, 13, 5, 6, 7]
heap_sort = HeapSort(arr)
print(heap_sort.sort()) # Output: [5, 6, 7, 11, 12, 13]
```

### C++

```cpp
class HeapSort {
    private:
        int *arr;
        int size;
    public:
        HeapSort(int *arr, int size) {
            this->arr = arr;
            this->size = size;
        }

        void heapify(int i) {
            int largest = i;
            int left = 2 * i + 1;
            int right = 2 * i + 2;
            if (left < size && arr[i] < arr[left]) {
                largest = left;
            }
            if (right < size && arr[largest] < arr[right]) {
                largest = right;
            }
            if (largest != i) {
                std::swap(arr[i], arr[largest]);
                heapify(largest);
            }
        }

        void sort() {
            // Build a max heap
            // Start from the last non-leaf node(n / 2 - 1)
            for (int i = size / 2 - 1; i >= 0; i--) {
                heapify(i);
            }
            // Extract elements one by one for sorting
            // Move the root element to the end of the array
            // Reduce the size of the heap by 1 for each searching
            // Re heapify the root element without the last element
            for (int i = size - 1; i > 0; i--) {
                std::swap(arr[i], arr[0]);
                size--;
                heapify(0);
            }
        }
};

// Example
int arr[] = {12, 11, 13, 5, 6, 7};
int size = sizeof(arr) / sizeof(arr[0]);
HeapSort heap_sort(arr, size);
heap_sort.sort();
for (int i = 0; i < size; i++) {
    std::cout << arr[i] << " ";
}
```
