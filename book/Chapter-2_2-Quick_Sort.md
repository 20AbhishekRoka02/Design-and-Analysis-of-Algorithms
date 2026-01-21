# Quick Sort
1. A Divide and Conquer algorithm where we will sort a given array by picking a **Pivot element** & a **Partitioning function** to rearrange elements around pivot.
2. It has 2 main components:
    1. **Pivot** - an element of given array
    2. **Partitioning algorithm** - to re-arrange elements around pivot.

3. Steps are:
    1. Choose a Pivot
        - An element is selected around which Partitioning algorithm will re-arrange elements of given array or sub-array.
        - It is selected by using any of the method given below:
            1. First / Last element selection
            2. Random element selection
            3. Calculate the median
    2. Partitioning the array / sub array
        - This algorithm will re-arrange elements around Pivot.
        - There are 2 famous Partitioning:
            1. Naive Partition
            2. Loumuto Partition
    3. Recursive Call
        - This will make recursive call to Quick Sort algorithm on both sides of Pivot.
    4. Base Case
        - The recursion halts when we have only one element left in the array
## Working
1. Suppose we have an unsorted array
    ```
    Place image of unsorted array here
    ```
2. Now, we choose a Pivot element, in our case, we will choose _"The Last Element"_, (here index 4)
3. So, let's highlight it.
    ```
    Unsorted array with highlighted element at index 4 goes here
    ```
4. Now, we set i = j = 0, and iterate j from 0 to 3 (i.e. high - 1)
    - if arr[j] < pivot, we will swap elements at i and j & increment i by 1
        ```
        arr[i], arr[j] = arr[j], arr[i]

        // increment i by 1
        i++
        ```
    Here is the iteration:
    ```{csv-table}
    :header: "j", "i", "arr[j]", "Pivot", "arr[j] < Pivot", "Action"
    0,0,3,0,False,"-"
    1,0,8,0,False,"-"
    2,0,2,0,False,"-"
    3,0,4,0,False,"-"
    ```
5. At the end of loop, we swap arr[high] (pivot) and arr[i]
    ```
    // arr[high] is Pivot element
    arr[high], arr[i] = arr[i], arr[high] 
    ```
    Now our looks like this:
    ```
    Place diagram of Pivot i.e. 0 in the array
    0,8,2,4,3
    ```
6. Now, we will partition array into left and right half
    ```
    Show the right halft and left half
    ```
    - Left half - There is no array
    - Right half - we have [8,2,4,3]
7. Choose Last element as Pivot (i.e. arr[4] = 3)
8. We set
    - low = 1
    - high = 4
    - i = 1
    - j = 1
    - Pivot = arr[high] (i.e. 3)
5. As we did in step 5,
    - Set i = j = low (i.e. 1)
    - Iterate j from low to high - 1
    - If arr[j] < Pivot, swap arr[i] and arr[j]
    ```{csv-table}
    :header:"j","i","arr[j]","Pivot","arr[j] < Pivot", "Action"
    1,1,8,3,False,"-"
    2,1,2,3,True, Swap arr[i] and arr[j]
    ```
    - Now sub array will be:
        ```
        Picture of 2,8,4,3
        ```
    - Now, i = 2
6. Now, let's get back to the table
    ```{csv-table}
    :header: "j","i","arr[j]", "Pivot", "arr[j] < Pivot", "Action"
    3,2,4,3,False,"-"
    ```
    - Now, we swap arr[j] with arr[high], & our array.
    ```
    Pivot of [2,3,4,8]
    ```
7. Now, we divide it to left half and right half
    ```
    Picture of [2,3,4,8] -> 2 and -> [4,8]
    ```
8. AS there is only one element on left, we will not perform sorting there.
9. On the right, we have
    ```
    Picture of [4, 8v(highlighted)]
    ```
    - Pick Pivot as hight = 4
    - Again, 
        - low = 3 
        - high = 4 
        - i = j = low (i.e. 3)
        - Pivot = 8 (i.e. arr[high])
    - We iterate j for 3 only

    ```{csv-table}
    :header: "j", "i","arr[j]","Pivot","arr[j] < Pivot", "Action"
    3,3,4,8 False,"-"
    ```
10. Now, when we divide this array now,
    ```
    Picture of [4,8] -> 4 and -> 8
    ```

We will not perform sorting on left, and right.

11. Let's see our array now
    ```
    Picture of [0,2,3,4,8]
    ```

We have sorted it in the steps, we have discussed till now.
```
Picture of complete Quick Sort array view divide and conquer and merge
```

## Algorithm
This algorithm is divided into 2 parts:
1. Quick Sort
    - which will recursive call itself.
2. Partition Function
    - which will re-arrange around the Pivot

```{code}
QuickSort(arr, low, high):
    if low < high:
        p = partition(arr, low, high)

        // Quick Sort left sub array
        QuickSort(arr, low, p - 1) 

        // Quick Sort right sub array
        QuickSort(arr, p + 1, high)

partition(arr, low, high):
    i = low - 1

    // Picking last element as Pivot
    pivot = arr[high]

    for j from low to high - 1:
         if arr[j] < pivot:
            i++

            // Swapping elements at arr[i] and arr[j]
            arr[i], arr[j] = arr[j], arr[i]
    i++
    arr[i], arr[high] = arr[high], arr[i]
    return i
```

## Time Complexity
1. Worst Case is $O(n^2)$ because of following cases:-
    - Array may be already sorted or reverse sorted
    - Picking smallest or largest element by value as a Pivot
    - Picking First/Last element as Pivot (I want to say something about this)
        - Some suggest picking Median value as Pivot can solve a problem, but calculating median each time will create an overhead which will make it $O(n^2)$ again
        - So, $O(n^2)$ is not a case of Pivot only, but type of input we got i.e. how elements are arranged in a given array.
2. Best Case is $\Omega(n \log n)$, and Average Case is $\Theta(n \log n)$, let discuss how:
    - $n$, because at every level, there is a sub array which will sum to n elements of the original array.
    - $\log n$, because there will be roughly $\log n$ recursion calls
        - like, we have 5 elements, then $\log_{2} 5 = 2.3219$, which is between 2 & 3, and we have 3 recursion calls, in above example
    
## Space Complexity (Auxillary Space)
1. $O(n)$ - when there is **imbalanced partitioning**, i.e. pivot is the smallest/largest element of the given sub array, like shown below
    ```
    Picture of imbalanced partitioning examples
    ```
2. $O(\log n)$ - when there is **balanced partitioning** i.e. pivot is roughly the median element of the array.