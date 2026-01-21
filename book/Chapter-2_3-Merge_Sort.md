# Merge Sort
1. It is a Divide and Conquer algorithm which first divides given array into 2 halves, until only single element left & then, begin merging them into sorted array.

2. It have following steps:-
    1. **Divide**
        1. Here, we divide array into 2 halves by calculating the mid element.
        2. So, one array is from low to mid, and other is from mid + 1 to high.
        3. We stop dividing further, when only 1 element left in the array.
    2. **Conquer**
        1. Here, we sort the 2 sub arrays, by compariing them, elements by elements.
        2. Smaller element gets inserted to the end of the sorted array. (i.e. we have to create another empty array, where we will place elements in sorted manner)
        3. When one array ends, the remaining part of the other array gets merged directly to the end of sorted array
    3. **Merge**
        1. Once we reach the level, where only 1 element is left in both arrays, we begin to merge them, upto the 1st recursive call of the Merge Sort function.
    

## Working
Let me explain it with example, so the things will make sense. Then, you can define merge sort in your words.

1. Suppose we have given an array
    ```
    Place image of unsorted array
    ```
2. Here, low = 0, high = 4, we calculate mid
    $$ mid = \frac{low + high}{2} $$
    * It will be a floor division
    So, 
    $$ mid = \frac{0 + 4}{2} = \frac{4}{2} = 2 $$

3. Now, we got:
    ```
    Picture of left and right part of the array
    ```

4. Now, we calculate mid & divide them independently:
    ```
    Place rest of the diagram
    ```
5. Now, it will look like 
    ```
    Show complete diagram of Merge Sort
    ```
6. Let's start merging from Level 3
    So, we have:
    ```
    Place picture of 3 and 8
    ```
    On compare & merge, we have
    ```
    image of sorted array
    ```
7. Now, in Level 2, we first work on left part
    - Let's compare & merge
    - is 3 < 2 ? False
        ```
        Picture of sorted array
        ```
    - Now only left array is remaining. So we merge it directly.
    - We get:
        ```
        Place picture here
        ```
8. On right half of Level 2, we have:
    ```
    Picture of 4 and 0
    ```
9. On level 1, we have:
    ```
    Place picture of arrays
    ```

    - Let's compare and merge:
    ```{csv-table}
    :header: "i", "j", "arr[i]", "arr[j]", "arr[i] < arr[j]", "sorted_array"
    0,0,2,0,False,0
    0,1,2,4,True,"0 2"
    1,1,3,4,True,"0 2 3"
    2,1,8,4,False,"0 2 3 4"
    ```
    ```
    Sorted array
    ```
10. At Level 0, we have our sorted array now,
    ```
    Image of sorted array
    ```

## Algorithm
1. It is divided into 2 parts:
    1. **Merge Sort Function** which will make recursive call.
    2. **Merge Function** which will merge the sorted halves.

```{code}
MergeSort(arr, low, high):
    if low < high:
        mid = (low + high) / 2

        // Merge Sort on Left half
        MergeSort(arr, low, mid)

        // Merge Sort on Right half
        MergeSort(arr, mid + 1, high)

        // Merging both halves
        Merge(arr, low, mid, high)

Merge(arr, low, mid, high):
    size_of_left_array = (mid - low) + 1
    size_of_right_array = (high - mid) + 1
    total_size = size_of_left_array + size_of_right_array

    // Create Sorted array of total_size, fill with 0s
    Create sorted_array [ 0 ... total_size - 1]

    while i <= mid & j <= high; do

        if arr[i] <= arr[j]; then
            sorted_array[k] = arr[i]
            k++
            i++
        else:
            sorted_array[k] = arr[j]
            k++
            j++
    
    if i == mid + 1; then
        while j <= high; do
            sorted_array[k] = arr[j]
            k++
            j++
    else:
        sorted_array[k] = arr[i]
        k++
        i++
```

## Time Complexity
- For Best, Worst and Average cases, it is $n \log n$
    1. $\log n$ - as each time we are dividing array into $\frac{n}{2}$
    2. $n$ - for merging 2 sorted halves

## Space Compelxity
It is $O(n)$, as there are $n$ elements in the array.

## Recurrence Relation
$$
T(n) =
\begin{cases}
\Theta(1); & n = 1 \\
2T\left(\frac{n}{2}\right) + \Theta(n); & n > 1
\end{cases}
$$














