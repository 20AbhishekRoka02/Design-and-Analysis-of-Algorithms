# Binary Search
1. It is a Divide and Conquer algorithm, where we will divide a problem (here, a sorted array) into 2 halves in each iteration.

## Requirements
1. A sorted array
2. Constant access time to any part of array

## Working
1. Suppose we have given an array
    ```
    Place array here
    ```
    and, we have to search element valued 1.
2. So, we have,
    - length of array, $n$ = 7
    - lowest index, low = 0
    - highest index, high = 6
    - element to find, key = 1
3. Now, we calculate mid index as:
$$mid = \frac{0 + 6}{2}$$
    - It will be a floor division i.e., if $\frac{3}{2} = 1.5$, then answer will be $1$
    - here, mid = 3
4. So, element at index mid (i.e. 3) is valued 4.
    ``` 
    arr[mid] = 4
    ```
5. Now, we make comparisons
    ```
    if key < arr[mid]:
        set high = mid - 1 
    else if key > arr[mid]:
        set low = mid + 1
    else:
        return mid
    ```
6. For now, key < arr[mid], so we set high = 2.
7. So, low = 0, high = 2, again calculate mid, now $mid = \frac{0+2}{2} = 1$
8. Now, arr[mid] = 2, and key < 2, therefore high = mid - 1 (i.e. 0)
    - low = 0 & high = 0
9. Calculating mid, $ mid = \frac{0+0}{2} = 0$
    - arr[0] = 1 & key = 1
    - Therefore, element is found at index 0
10. Suppose, instead of 1, if we search for -2.
    - At this point, we will be doing, high = mid - 1 (i.e. -1)
    - Now, high < low, which will be invalid case for this algorithm & we will return -1 i.e. Not Found!

## Algorithm of Binary Search
```
Set low = 0, high = n - 1 and key
while low <= high; do
    Calculate mid = (low + high) / 2

    if key == arr[mid]; then
        return mid
    else if key < arr[mid]; then
        high = mid - 1
    else:
        low = mid + 1

return - 1
```

Above is the Iterative Approach of solving this problem.

## Time Complexity
1. Best Case is $\Omega(1)$ i.e. on first attempt we got arr[mid] == key.
2. Worst Case is $O( \log n)$ i.e. even though an element is not found, but we got $\log n$ comparisons, like for 7 elements above, $log_{2}(7) = 2.807 \approx 3$ comparisons to get our solution
3. And, Average Case is $\Theta(\log n)$ i.e. for an average input size.

## Space Complexity (Auxillary Space)
1. For **iterative approach**, it is $O(1)$, as we are not allocating any new memory space at run time.
2. For **recursive approach**, we got $O(\log n)$, as we push the instance of function on to stack memory for each recursive call.
    - As $\log_{2}(7) = 2.807 \approx 3$, on 3rd push of stack, we have output as either found or not found.