
# Time Complexity Analysis of Algorithms

This document explains the time complexities of common algorithms along with example code snippets for each.

---

## 1. **Insertion Sort**
- **Best Case**: \( O(n) \) (Array is already sorted)
- **Average Case**: \( O(n^2) \)
- **Worst Case**: \( O(n^2) \) (Array is sorted in reverse order)

### Code Example:
```c
void insertionSort(int array[], int n) {
    for (int i = 1; i < n; i++) {
        int key = array[i];
        int j = i - 1;
        while (j >= 0 && array[j] > key) {
            array[j + 1] = array[j];
            j--;
        }
        array[j + 1] = key;
    }
}
```

---

## 2. **Bubble Sort**
- **Best Case**: \( O(n) \) (Array is already sorted)
- **Average Case**: \( O(n^2) \)
- **Worst Case**: \( O(n^2) \) (Array is sorted in reverse order)

### Code Example:
```c
void bubbleSort(int array[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (array[j] > array[j + 1]) {
                int temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }
}
```

---

## 3. **Merge Sort**
- **Best Case**: \( O(n \log n) \)
- **Average Case**: \( O(n \log n) \)
- **Worst Case**: \( O(n \log n) \)

### Code Example:
```c
void merge(int array[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;
    int L[n1], R[n2];

    for (int i = 0; i < n1; i++)
        L[i] = array[left + i];
    for (int i = 0; i < n2; i++)
        R[i] = array[mid + 1 + i];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) array[k++] = L[i++];
        else array[k++] = R[j++];
    }

    while (i < n1) array[k++] = L[i++];
    while (j < n2) array[k++] = R[j++];
}

void mergeSort(int array[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(array, left, mid);
        mergeSort(array, mid + 1, right);
        merge(array, left, mid, right);
    }
}
```

---

## 4. **Binary Search**
- **Best Case**: \( O(1) \) (Target found at the middle)
- **Average Case**: \( O(\log n) \)
- **Worst Case**: \( O(\log n) \)

### Code Example:
```c
int binarySearch(int array[], int n, int target) {
    int left = 0, right = n - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (array[mid] == target) return mid;
        else if (array[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```

---

## 5. **Linear Search**
- **Best Case**: \( O(1) \) (Target is the first element)
- **Average Case**: \( O(n) \)
- **Worst Case**: \( O(n) \) (Target is not in the array or at the end)

### Code Example:
```c
int linearSearch(int array[], int n, int target) {
    for (int i = 0; i < n; i++) {
        if (array[i] == target) return i;
    }
    return -1;
}
```

---

## Summary of Time Complexities

| Algorithm              | Best Case  | Average Case | Worst Case   |
|------------------------|------------|--------------|--------------|
| **Insertion Sort**     | \( O(n) \) | \( O(n^2) \) | \( O(n^2) \) |
| **Bubble Sort**        | \( O(n) \) | \( O(n^2) \) | \( O(n^2) \) |
| **Merge Sort**         | \( O(n \log n) \) | \( O(n \log n) \) | \( O(n \log n) \) |
| **Binary Search**      | \( O(1) \) | \( O(\log n) \) | \( O(\log n) \) |
| **Linear Search**      | \( O(1) \) | \( O(n) \) | \( O(n) \) |
