# T2A1-Workbook
---

## Question 1: Identify and explain the workings of TWO sorting algorithms and discuss and compare their performance/efficiency (i.e. Big O)
---
<br>

### <strong>Bubble Sort Algorithm</strong>
### Overview:
The Bubble Sort algorithm is one of the more basic of the common sorting algorithms. It takes the iterative approach and loops through the array while comparing the adjacent elements within the array. Through each iteration it swaps adjacent elements up until the last sorted element from the previous iteration. It will iterate through the array as many times as it takes for nothing to be changed, which means that the elements have been sorted into the intended order.  

```
def bubble_sort(array):
        n = len(array)
        for i in range(n):
        # allows the function to end if there is nothing left to sort
            already_sorted = True
            # searches through each item in the list and compares it with the adjacent value.  
            for j in range(n - i - 1):
                if array[j] > array[j + 1]:
                    # Swap if the item is larger than the adjacent value
                    array[j], array[j + 1] = array[j + 1], array[j]
                    # if elements are swapped set to false so it continues sorting.
                    already_sorted = False
            # if there were no swaps, the loop is stopped.
            if already_sorted:
                break
        return array
```

<br> 

### Example:

*Goal: Sort the array in ascending order.*

*Array: ``[12, 4 ,6 , 2, 8]``*

<br>

<strong>First iteration:</strong>

The first iteration will start from the first index and proceed to the last. 

1. The first two elements are compared. If the first element is larger than the second element, they will be swapped.  If the first element is smaller than the second element, it will move on to the next comparison. In this case, the first is greater and they were swapped. 

    Result: ``[4, 12 ,6 , 2, 8]``

2. Now, the second and the third elements are compared. The second is larger than the third, so they are swapped. 

    Result: ``[4, 6, 12, 2, 8]``

3. This process repeats until the last element. The largest element (12) has now been placed at the end of the array. 

    Result: ``[4, 6, 2, 8, 12]``

<br>

<strong>Second iteration:</strong>

The process repeats, placing the next largest element at the end.

1. The second and third elements are the only ones swapped during this iteration.

    Result: ``[4, 2, 6, 8, 12]``

<br>

<strong>Remaining Iterations:</strong>

The process repeats until the elements are in ascending order.

<br>

<strong>*Final Result: ``[2, 4, 6, 8, 12]``*</strong>

<br>
<br>

### <strong>Selection Sort Algorithm:</strong>       

### Overview:
The Selection Sort Algorithm is another basic sorting algorithm.  Like the Bubble Sort Algorithm, it too takes the iterative approach.  Through each iteration, it moves the smallest element to the beginning of the list. It starts by setting the first element in the list as the ``minimum``. It then compares the ``minimum`` to each element in the list until it finds one smaller.  When it finds a smaller element, that element is considered the new ``minimum``, and it continues this process until it has compared all of the elements.  Once the iteration is complete, the final ``minimum`` will be the smallest number in the array, and that number will be moved to the front. This process repeats until the numbers are in the desired order. 

```
def selectionSort(array, size):
    for step in range(size):
        min_idx = step
        for i in range(step + 1, size):
            # select the minimum element
            if array[i] < array[min_idx]:
                min_idx = i
        # put the minimum at the correct position
        (array[step], array[min_idx]) = (array[min_idx], array[step])
# set size equal to length of the data        
size = len(data)
```
### Example:

*Goal: Sort the array in ascending order.*

*Array: ``[12, 4, 6, 2, 8]``*

<strong>First Iteration:</strong>
The first iteration will set the ``minimum`` as the first element and compare it until it finds a smaller element. Every time it finds a smaller element, it sets that as the new ``minimum`` until it has finished the iteration.  The final ``minimum`` for the iteration is then swapped with the first element in the set.

*``Minimum`` in white.*

1. The first two elements are compared. The second element (4) is smaller than the previous ``minimum(12)``, so it is now assigned as the ``minimum``.

    Result: ``[12, ``4``, 6, 2, 8]``

<br>

2. Now, the ``minimum(4)``  and the third element are compared. The current ``minimum(4)`` is still smaller, so it remains ``minimum``.

    Result: ``[12, ``4``, 6, 2, 8]``

<br>

3. Now, the ``minimum(4)``  and the fourth element are compared. The current ``minimum(4)`` is larger than the fourth element(2), so the fourth element becomes the new ``minimum``.

    Result: ``[12, 4, 6, ``2``, 8]``

<br>

4. Now, the ``minimum(2)``  and the fifth element are compared. The current ``minimum(2)`` is smaller than the fifth element(8), so it remains the ``minimum``.

<br>

5. Now that we have the ``minimum(2)`` for the set, it is then swapped with the first element in the set.

    Result of First Iteration: ``[2, 4, 6, 12, 8]``

<br>

<strong>Remaining Iterations:</strong>

The process repeats, ignoring the accurately swapped ``minimums`` as they are placed in the sorted sub-array which is ignored. 

<br>

### <strong>Performance/Efficiency Comparison</strong>

<br>

<strong>Bubble Sort:</strong>

Bubble sort  has an inner and an outer loop which both need to iterate through ``n`` (size of list) number of times in the worst case. The outer loop varies as it has an escape that will stop the loop as soon as the array is sorted as intended.  This means that the outer loop has a worst case scenario of running O(n) amount of times and the best case scenario that it only needs to run once because the data was in the proper order to begin with. The inner loop performs O(n) times deterministically, so there is no variation. 

This means that in the worst case scenario, both loops carry the Big-O notation of O(n).  When these are combined they come out to a Big-O of O(n^2) (quadratic complexity).

``O(n x n) = O(n^2)``

This also means that in the best case scenario in which the data is already sorted, the outer loop would run once O(1) and the inner loop would run O(n). When combined, they come out to a run time of O(n)  (linear complexity).

``O(1 x n) = O(n)``

<br>

<strong>Selection Sort:</strong>

Selection sort  has an inner and an outer loop which both need to iterate through ``n`` (size of list) number of times. The outer loop selects an element of the array one by which gives it the run time of O(n).  The inner loop compares the selected element with every other element in the array, giving it a value of O(n) as well. Unlike Bubble sort, there is no variation in either loop giving it a best and worst case complexity of O(n^2).

``O(n x n) = O(n^2)``

<strong>*Conclusion:*</strong>

Bubble Sort and Selection Sort have the same average Big-O complexity, O(n^2).  Despite this, Selection Sort is still more efficient due to the fact that there are far more swapping operations in Bubble Sort.  Selection Sort only swaps once per iteration while Bubble Sort typically swaps multiple times per iteration.


<br>
<br>
<br>
<br>
<br>

## Question 2: Identify and explain the workings of TWO search algorithms and discuss and compare their performance/efficiency (i.e. Big O)
---

### <strong>Linear Search Algorithm:</strong>  
### Overview:
The linear search algorithm is an incredibly simple search algorithm. The linear search algorithm works by traversing an entire array until the desired element is found.  Once it is found, the location of the element is returned.  If no match for the element is found, the algorithm returns -1.  This algorithm does not require the array to be sorted beforehand due to it comparing the desired element to each item one by one.

```
def search(arr, x):
    for i in range(len(arr)):
        # check if any items in the array equal x
        if arr[i] == x:
            # return them if they do
            return i
    # return -1 if they don't
    return -1
```
### Example:
*Goal: Find the index for the value ``6`` in the following array.*

*Array: ``[12, 4, 6, 2, 8]``*

<br>

<strong>First Iteration:</strong>

The value ``6`` is compared to the value ``12``.  These values do not match, so the loop continues.

<br>

<strong>Second Iteration:</strong>

The value ``6`` is compared to the value ``4``.  These values do not match, so the loop continues.

<br>

<strong>Third Iteration:</strong>

The value ``6`` is compared to the value ``6``.  These values do match, so the loop ends and the index value of ``6`` is returned.

<br>

### <strong>Binary Search Algorithm:</strong>  
### Overview:
The Binary Search Algorithm is another simple search algorithm. Unlike the Linear Search algorithm, it requires the list to be sorted beforehand.  It works by immediately disregarding half of the list during the first iteration of the loop. It does so by comparing the desired value with the middle element of the list. First, it creates the variables ``low``, ``high``, and ``mid``, setting them to ``0``, the ``final element value``, and ``0``, respectively. If the middle element matches, it returns the middle element.  If the middle element does not match, it checks to see whether the desired value is larger or smaller than the middle element.  If it is larger, then we know it is in the second half and a new low is created.  If it is smaller, then we know it is in the first half and a new high is created. This process is repeated until the desired value equals ``mid``.  If the desired value is not found, the function returns ``-1``.

```

def binary_search(arr, x):
    low = 0
    high = len(arr) - 1
    mid = 0
    while low <= high:
        # find the middle index
        mid = (high + low) // 2
        # ignore the first half if x is greater
        if arr[mid] < x:
            low = mid + 1
        # ignore the second half if x is smaller
        elif arr[mid] > x:
            high = mid - 1
        # return the index if x is present at mid
        else:
            return mid
    # return -1 if there is not a match
    return -1
```

### Example:
*Goal: Find the index for the value ``4`` in the following array.*

*Array: ``[2, 4, 6, 8, 12]``*

<br>

<strong>First Iteration:</strong>

The middle number of the array is found through the equation (0+4)//2 = 2, and its value is ``6``. Since the value we are searching for is less than ``6``, the possible location of the desired value must be in the first half of the array. The high is then set to ``mid - 1`` and the loop starts over.

<br>

<strong>Second Iteration:</strong>

The middle number of the first half of the array is found through the equation (0+1)//2 = 0, and its value is ``2``. The value ``2`` is less than the desired value, so the low is set to ``mid + 1`` and the loop starts over.

<strong>Third Iteration:</strong>
The middle number of the remaining values is found through the equation (1+2)//2 = 1, and its value is ``4``. The value ``4`` matches the desired value, so the function returns the index value and the loop ends. 

### <strong>Performance/Efficiency Comparison</strong>

<br>

<strong>Linear Search:</strong>

Linear Search uses a single loop which compares the desired value with the elements within the loop.  The loop stops when the desired value matches one of the elements within the loop.  In the best case scenario, the desired value could match the first element, so that the loop would only have to iterate once. Worst case scenario, the desired value matches the final element in the array, meaning the loop would have to iterate ``n`` (the amount of elements in the array) times. Since Linear Search uses a loop with the possibility of ``n`` iterations, we would say it has the Big-O notation of ``O(n)``  (linear complexity).


<br>

<strong>Binary Search:</strong>
Binary Search uses a single loop which halves the number of elements being searched after each iteration. The length of the array after ``k`` iterations is  ``n/2^k``, where ``n`` represents the length of the array and ``k`` represents the number of iterations.   The length of the array after ``k`` iterations is one, so we can set ``n/2^k=1``.  Now, we must solve for ``n`` by multiplying both sides by ``2^k`` leaving us with ``n=2^k``.  Now that we have them separated, we can apply log to both sides in order to eliminate the ``2`` and solve for ``k``, leaving us with ``k=log(n)``. The Big-O notation for binary search is ``O(log(n))`` (logarithmic complexity).


<br>

<strong>*Conclusion:*</strong>

Linear Search has linear complexity which is less efficient than Binary Search's logarithmic complexity. If the amount of items being searched is doubled, Linear Search would take twice as long to complete since it needs to possibly go through the entire list. However, in Binary Search, the amount being searched is halved after every loop, so it stays efficient even when more data is added.  A major perk to using Linear Search is that the list does not have to be sorted in order for it to work, unlike Binary Search.


 ## Works Cited:

 ### Question 1:

Bubble Sort (With Code in Python/C++/Java/C). www.programiz.com/dsa/bubble-sort. Accessed 4 Sept. 2022. 

Real Python. Sorting Algorithms in Python. 1 Sept. 2022, realpython.com/sorting-algorithms-python. 


Selection Sort (With Code in Python/C++/Java/C). www.programiz.com/dsa/selection-sort. Accessed 4 Sept. 2022.

 ### Question 2:

GeeksforGeeks. “Linear Search Vs Binary Search.” GeeksforGeeks, 4 Aug. 2022, www.geeksforgeeks.org/linear-search-vs-binary-search. 

GeeksforGeeks. “Searching Algorithms.” GeeksforGeeks, www.geeksforgeeks.org/searching-algorithms/?ref=lbp. Accessed 8 Sept. 2022. 

Real Python. How to Do a Binary Search in Python. https://realpython.com/binary-search-python/. Accessed 8 Sept. 2022.