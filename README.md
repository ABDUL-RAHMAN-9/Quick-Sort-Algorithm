# Quick-Sort-Algorithm

- QuickSort is a sorting algorithm based on the Divide and Conquer that picks an element as a pivot and partitions the given array around the picked pivot by placing the pivot in its correct position in the sorted array.

# How does QuickSort Algorithm work?
QuickSort works on the principle of divide and conquer, breaking down the problem into smaller sub-problems.

There are mainly three steps in the algorithm:

1. Choose a Pivot: Select an element from the array as the pivot. The choice of pivot can vary (e.g., first element, last element, random element, or median).
  
2. Partition the Array: Rearrange the array around the pivot. After partitioning, all elements smaller than the pivot will be on its left, and all elements greater than the pivot will be on its right. The pivot is then in its correct position, and we obtain the index of the pivot.
  
3. Recursively Call: Recursively apply the same process to the two partitioned sub-arrays (left and right of the pivot).
  
4. Base Case: The recursion stops when there is only one element left in the sub-array, as a single element is already sorted.
Here’s a basic overview of how the QuickSort algorithm works.

<div align='center'>
  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240926172924/Heap-Sort-Recursive-Illustration.webp" width="500">
</div>


<div align='center'>
 <h2> Working of Partition Algorithm with Illustration</h2>
  
 The logic is simple, we start from the leftmost element and keep track of the index of smaller (or equal) elements as i . While traversing, if we find a smaller element, we swap the current element with <b>arr[i].</b> Otherwise, we ignore the current element. 

- Let us understand the working of partition algorithm with the help of the following example:

  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20241111171208918304/quick-sort-1.webp" width="400">
    <img src="https://media.geeksforgeeks.org/wp-content/uploads/20241111171209045220/quick-sort-2.webp" width="400">
      <img src="https://media.geeksforgeeks.org/wp-content/uploads/20241220154252629076/quick-sort-3-1.png" width="400">
        <img src="https://media.geeksforgeeks.org/wp-content/uploads/20241111171209255614/quick-sort-4.webp" width="400">
          <img src="https://media.geeksforgeeks.org/wp-content/uploads/20241213175652062597/quick-sort.png" width="400">
            <img src="https://media.geeksforgeeks.org/wp-content/uploads/20241111171209465155/quick-sort-6.webp" width="400">
            
</div>

# Illustration of QuickSort Algorithm

- In the previous step, we looked at how the partitioning process rearranges the array based on the chosen pivot. Next, we apply the same method recursively to the smaller sub-arrays on the left and right of the pivot. Each time, we select new pivots and partition the arrays again. This process continues until only one element is left, which is always sorted. Once every element is in its correct position, the entire array is sorted.

- Below image illustrates, how the recursive method calls for the smaller sub-arrays on the left and right of the pivot:

<div align="center">
  <img src="https://media.geeksforgeeks.org/wp-content/uploads/20240925173636/quick-sort--images.webp" width="500">

</div>

<h2>Quick Sort is a crucial algorithm in the industry, but there are other sorting algorithms that may be more optimal in different cases.</h2>

# Code:

```
#include <bits/stdc++.h>
using namespace std;

int partition(vector<int>& arr, int low, int high) {
  
    // Choose the pivot
    int pivot = arr[high];
  
    // Index of smaller element and indicates 
    // the right position of pivot found so far
    int i = low - 1;

    // Traverse arr[low..high] and move all smaller
    // elements on left side. Elements from low to 
    // i are smaller after every iteration
    for (int j = low; j <= high - 1; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    
    // Move pivot after smaller elements and
    // return its position
    swap(arr[i + 1], arr[high]);  
    return i + 1;
}

// The QuickSort function implementation
void quickSort(vector<int>& arr, int low, int high) {
  
    if (low < high) {
      
        // pi is the partition return index of pivot
        int pi = partition(arr, low, high);

        // Recursion calls for smaller elements
        // and greater or equals elements
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    vector<int> arr = {10, 7, 8, 9, 1, 5};
    int n = arr.size();
    quickSort(arr, 0, n - 1);
  
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
#include <bits/stdc++.h>
using namespace std;

int partition(vector<int>& arr, int low, int high) {
  
    // Choose the pivot
    int pivot = arr[high];
  
    // Index of smaller element and indicates 
    // the right position of pivot found so far
    int i = low - 1;

    // Traverse arr[low..high] and move all smaller
    // elements on left side. Elements from low to 
    // i are smaller after every iteration
    for (int j = low; j <= high - 1; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    
    // Move pivot after smaller elements and
    // return its position
    swap(arr[i + 1], arr[high]);  
    return i + 1;
}

// The QuickSort function implementation
void quickSort(vector<int>& arr, int low, int high) {
  
    if (low < high) {
      
        // pi is the partition return index of pivot
        int pi = partition(arr, low, high);

        // Recursion calls for smaller elements
        // and greater or equals elements
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    vector<int> arr = {10, 7, 8, 9, 1, 5};
    int n = arr.size();
    quickSort(arr, 0, n - 1);
  
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}

```

# Output: 

```
Sorted Array
1 5 7 8 9 10
```
# Time Complexity: (O(n2))
