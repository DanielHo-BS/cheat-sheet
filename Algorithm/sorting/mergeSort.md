# Merge Sort

Merge Sort is a divide-and-conquer algorithm that divides the input list into two halves, recursively sorts the two halves, and then merges the sorted halves. The merge sort algorithm is stable.

![image](https://upload.wikimedia.org/wikipedia/commons/c/cc/Merge-sort-example-300px.gif)

## Complexity

| Best | Average | Worst | Space |
| --- | --- | --- | --- |
| O(n log n) | O(n log n) | O(n log n) | O(n) |

## Implementation

### Python

```python
class MergeSort:
    def __init__(self, arr):
        self.arr = arr

    def mergeSort(self):
        if len(self.arr) <= 1:
            return self.arr
        # Divide the list into two halves
        mid = len(self.arr) // 2
        left = MergeSort(self.arr[:mid])
        right = MergeSort(self.arr[mid:])
        # Merge the two halves
        return self.merge(left.mergeSort(), right.mergeSort())

    def merge(self, left, right):
        # Merge two sorted lists
        result = []
        i = j = 0
        # Compare elements from left and right
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                result.append(left[i])
                i += 1
            else:
                result.append(right[j])
                j += 1
        # Append the remaining elements
        result.extend(left[i:])
        result.extend(right[j:])
        return result

# Example
if __name__ == "__main__":
    arr = [12, 11, 13, 5, 6, 7]
    mergeSort = MergeSort(arr)
    print(mergeSort.mergeSort())
```


### c++

```cpp

class MergeSort {
    public:
        MergeSort(vector<int>arr) {
            this->arr = arr;
        }

        vector<int> mergeSort() {
            if (arr.size() <= 1) {
                return arr;
            }
            // Divide the list into two halves
            int mid = arr.size() / 2;
            vector<int> left(arr.begin(), arr.begin() + mid);
            vector<int> right(arr.begin() + mid, arr.end());
            // Merge the two halves
            return merge(mergeSort(left), mergeSort(right));
        }

        vector<int> merge(vector<int> left, vector<int> right) {
            // Merge two sorted lists
            vector<int> result;
            int i = 0, j = 0;
            // Compare elements from left and right
            while (i < left.size() && j < right.size()) {
                if (left[i] < right[j]) {
                    result.push_back(left[i]);
                    i++;
                } else {
                    result.push_back(right[j]);
                    j++;
                }
            }
            // Append the remaining elements
            while (i < left.size()) {
                result.push_back(left[i]);
                i++;
            }
            while (j < right.size()) {
                result.push_back(right[j]);
                j++;
            }
            return result;
        }
};

// Example
int main() {
    vector<int> arr = {12, 11, 13, 5, 6, 7};
    MergeSort mergeSort(arr);
    vector<int> result = mergeSort.mergeSort();
    for (int i = 0; i < result.size(); i++) {
        cout << result[i] << " ";
    }
    return 0;
}
```
