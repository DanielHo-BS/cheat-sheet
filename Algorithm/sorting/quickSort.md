# Quick Sort

Quick Sort is a divide-and-conquer algorithm that divides the input list into two parts based on a pivot element, recursively sorts the two parts, and then combines the sorted parts. The quick sort algorithm is not stable.

![image](https://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif)

## Complexity

| Best | Average | Worst | Space |
| --- | --- | --- | --- |
| O(n log n) | O(n log n) | O(n^2) | O(log n) |

## Implementation

### Python

```python
class QuickSort:
    def __init__(self, arr):
        self.arr = arr

    def quickSort(self):
        if len(self.arr) <= 1:
            return self.arr
        # Choose the pivot element
        pivot = self.arr[len(self.arr) // 2]
        # Divide the list into three parts
        left = []
        middle = []
        right = []
        for i in self.arr:
            if i < pivot:
                left.append(i)
            elif i == pivot:
                middle.append(i)
            else:
                right.append(i)
        # Recursively sort the left and right parts
        return self.quickSort(left) + middle + self.quickSort(right)

# Example
if __name__ == "__main__":
    arr = [12, 11, 13, 5, 6, 7]
    quickSort = QuickSort(arr)
    print(quickSort.quickSort())
```

### c++

```cpp
class QuickSort {
    private:
        vector<int> arr;
    public:
        vector<int> quickSort(vector<int> arr) {
            if (arr.size() <= 1) {
                return arr;
            }
            // Choose the pivot element
            int pivot = arr[arr.size() / 2];
            // Divide the list into three parts
            vector<int> left, middle, right;
            for (int i = 0; i < arr.size(); i++) {
                if (arr[i] < pivot) {
                    left.push_back(arr[i]);
                } else if (arr[i] == pivot) {
                    middle.push_back(arr[i]);
                } else {
                    right.push_back(arr[i]);
                }
            }
            // Recursively sort the left and right parts
            vector<int> leftSorted = quickSort(left);
            vector<int> rightSorted = quickSort(right);
            // Combine the sorted parts
            vector<int> sorted;
            sorted.insert(sorted.end(), leftSorted.begin(), leftSorted.end());
            sorted.insert(sorted.end(), middle.begin(), middle.end());
            sorted.insert(sorted.end(), rightSorted.begin(), rightSorted.end());
            return sorted;
        }
};

// Example
int main() {
    vector<int> arr = {12, 11, 13, 5, 6, 7};
    QuickSort quickSort;
    vector<int> sorted = quickSort.quickSort(arr);
    for (int i = 0; i < sorted.size(); i++) {
        cout << sorted[i] << " ";
    }
    return 0;
}
```