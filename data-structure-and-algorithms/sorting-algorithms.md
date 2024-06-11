# 📖 Sorting Algorithms
A **sort** is formally defined as a rearrangement of a sequence of elements that puts all elements into a non-decreasing order based on the ordering relation.

#### Ordering Relation
 1. Law of Trichotomy : `a<b, a=b, or a>b`
 2. Law of Transitivity : `a<b and b<c, then a<c`
#### **Stability** : Stable sorting algorithm preserve the order of equal elements
### Bubble Sort
```java
public class Solution {
    public void bubbleSort(int[] arr) {
        // Mutates arr so that it is sorted via swapping adjacent elements until
        // the arr is sorted.
        boolean hasSwapped = true;
        while (hasSwapped) {
            hasSwapped = false;
            for (int i = 0; i < arr.length - 1; i++) {
                if (arr[i] > arr[i + 1]) {
                    // Swap adjacent elements
                    int temp = arr[i];
                    arr[i] = arr[i + 1];
                    arr[i + 1] = temp;
                    hasSwapped = true;
                }
            }
        }
    }
}
```
- TC : (O(n^2)
- Stable
### Insertion Sort
### Selection Sort
```java
public class Solution {
    public void selectionSort(int[] arr) {
        // Mutates arr so that it is sorted via selecting the minimum element and
        // swapping it with the corresponding index
        int min_index;
        for (int i = 0; i < arr.length; i++) {
            min_index = i;
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[j] < arr[min_index]) {
                    min_index = j;
                }
            }
            // Swap current index with minimum element in rest of list
            int temp = arr[min_index];
            arr[min_index] = arr[i];
            arr[i] = temp;
        }
    }
}
```
- Time Complexity : O(n^2)
- Not stable
### Merge Sort
### Heap Sort
### Quick Sort
### Counting Sort
### Radix Sort