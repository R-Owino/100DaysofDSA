## Search Algorithms

### What are search algorithms?
<p>
In Computer Science, a search algorithm is a technique for finding a specific item or group of items among a collection of data. Basically, they are developed to solve search problems.
Search algorithms work to retrieve information stored within a particular data structure, or calculated in the search space of a problem domain, with either discrete or continuous values.
Search algorithms operate by checking each element in the dataset in order to locate the target selection. 
</p>

### Terminologies used with search algorthims
1. Target element
<p>
Specific element or group of elements that is being looked for within the data collection. The target could be a value, a record, a key or something else.
</p>

2. Search space
<p>
The entire collection of data where the target element is being looked for. It varies in size and organization depending on the data structure used.
</p>

3. Complexity
<p>
Measured in terms of time and space requirements, searching has different levels of complexity depending on the data structure and algorithm used.
</p>

3. Deterministic vs non-deterministic
<p>
Binary search algorthms are deterministic i.e they follow a clear systematic approach.
Linear search algorithms are non-deterministic i.e they need to examine the entire search space in the worst case.
</p>

### Types of search algorithms

1. Linear Search
<p>
Also called sequential search, it starts from one end and goes through the entire list until the target element is found, else it goes through to the end of the list.

It works on both sorted and unsorted lists, and does not need any preconditioned list for the operation. However, its efficiency is lesser as compared to other search algorithms since it checks all elements one by one.

Time complexity for linear search is O(n) on the worst and average cases and O(1) on the best case.
</p>

2. Sentinel Linear Search
<p>
Just like linear search, sentinel search is an algorithm for a list of items stored in a sequential manner.

<details>
  <summary><strong>Recap 🔄</strong></summary>

  - Linear search works by going through each item of the list in a linear fashion, comparing it to the target. This results to either finding the required item or not.

  - It does this by making two comparisons in every iteration
        - First iteration: check if the we're at the end of the list
        - Second iteration: check if current item matches the target or not
</details>

Linear search does comparisons twice. What if there was a way to make the search faster? This is where sentinel search comes in.

Sentinel search works by first inserting the target element at the end of the list, then comparisons are done with each item of the list until the required item is found. In this case, either the required item is in the list, in which case it will be found before we reach the end of the list. Or the list didn’t have the target, so the algorithm will reach the end of the list and find the target item that we have inserted.

This way, we only need to check if the item matches the target, not if the list is empty. This is because one way or another, we'll find the target and break out of the loop.

Lastly, we check if the item found was already there or manually added. This check will happen only once and the entire runtime of the algorithm will be cut down significantly because we have one less comparison to do in every iteration of the loop.

The time complexity of sentinel search is O(n) in the worst case and O(1) in the best case, when the key is found in the first iteration.
</p>

3. Binary Search
<p>
Binary search algorithm follows the divide and conquer strategy to find an element. It works on a sorted array by repeatedly dividing the search interval in half. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(log N).

It works perfectly under the following conditions:
- The data structure must be sorted.
- Access to any element of the data structure takes constant time.

This is how it operates:
- Initially, the search space is the entire array and the target is compared with the middle element of the array.
- If they are not equal, the half in which the target cannot lie is eliminated and the search continues on the remaining half, again taking the middle element to compare to the target, and repeating this until the target is found.
- If the search ends with the remaining half being empty, the target is not in the array.
</p>

4. Ternary binary search
<p>
A binary search algorithm, but instead of dividing the list into 2 parts, the list is divided into 3 parts - we now have 2 mid points. This also means it is a divide and conquer algorithm. The mid points are used to determine which part the target element is because at each iteration, the algorithm ignores ⅓ of the list and proceeds to search in the remaining ⅔.

The time complexity of ternary search is O(log<sub>3</sub>n).

The operations is just the same as in normal binary search, only that instead of dividing into 2 parts, it divides the array into 3 parts.

Also, like in binary search, the list must be sorted first before searching an element, and searching for an element that is duplicated returns the position of the first occurance of that element.
</p>

5. Jump Search
<p>
Also called block search algorithm, jump search lies between linear search and binary search. Recall, linear search works well with small arrays and binary search works well with larger sorted arrays. For this reason, jump search is also applied to sorted arrays.

The main idea in jump search is to search fewer elements than in linear search at the speed of binary search.

Here's how it works:
As the name suggests, it skips a predetermined block of elements until it gets to the block who's last element is greater than the target element.
Predetermined because the size of the block to be skipped is the squareroot of the length of the array.
When the block that possibly contains the target element is found, the target element is searched for linearly.
This makes the time complexity of jump search between O(n) and O(log n) i.e O(? n)
</p>

6. Interpolation Search
<p>
Interpolation search is an improvement to the binary search. It searches for an element in a sorted uniformly distributed array i.e the interval between the element should be uniform. It works by probing the position of the target value.

<details>
  <summary><strong>Recap 🔄</strong></summary>

  - Binary search algorithm searches for an element by dividing the sorted array into 2 parts.
  - It does not take advantage of probing for the position of the target element.
</details>

In interpolation search, a formula is used to find the probe position, an index that is close to the target element. If the target element is larger than the element at the probe position, the search moves to the right of the probe position. Otherwise, the item is searched in the sub-array to the left of the middle item. This process continues on the sub-array as well until the size of subarray reduces to zero.

The following formula is used to calculate the probe position:


$$mid\, =\, Lo\, +\, \frac{\left ( Hi\, -\, Lo \right )\ast \left ( X\, -\, A\left [ Lo \right ] \right )}{A\left [ Hi \right ]\, -\, A\left [ Lo \right ]}$$

where:
```math

A = list
Lo = lowest index of the list
Hi = highest index of the list
A[n] = value stored at index n in the list

```

The time complexity of interpolation search is Ο(log (log n))
</p>

7. Exponential search
<p>
First of all, the algorithm is named <i>exponential</i> because it jumps elements with steps equal to exponenets of 2 (we'll see this in the code implementation), and not because of the time complexity.

On a high level, exponential seacrh involves 2 steps:
1. Find the range where the element is present
2. Do a binary search in the found range

Given this, it works on a sorted list by jumping 2^i elements every iteration where i represents the value of loop control variable, and then verifying if the search element is present between last jump and the current jump. 

It is a combination of linear and binary search.

The time complexity for exponential search is O(log n).
</p>

8. Fibonacci search
<p>
A comparison-based technique that uses fibonacci numbers to search for the target element. Like binary search, it uses the divide and conquer strategy to look for elements in a sorted array.

A few differences it has with binary search are:
1. It divides the array into unequal parts.
2. It uses the + and - signs instead of the / sign to divide the array.
3. Useful for when the array is big such that it can't fit in the CPU cache or the RAM because it examines relatively closer elements in the subsequent steps.

It has a time complexity of log n, like binary search.
</p>

4. Depth-first search
<p>
Used more intricately in data structures like trees and graphs. It explores the depth of a branch before breadth.
</p>

5. Breadth-first search
<p>
Also used in tree and graph data structures. It explores all the neighboring nodes before proceeding to the nodes at the next level depth.
</p>

#### References
1. [Search algorithms](https://en.wikipedia.org/wiki/Search_algorithm)
2. [Search Algorithms – Linear Search and Binary Search Code Implementation and Complexity Analysis](https://www.freecodecamp.org/news/search-algorithms-linear-and-binary-search-explained/)
3. [Searching algorithms](https://www.geeksforgeeks.org/searching-algorithms/)
4. [Linear search](https://www.geeksforgeeks.org/linear-search/)
5. [Sentinel linear search](https://www.askpython.com/python/examples/sentinel-search)
6. [Binary search](https://www.geeksforgeeks.org/binary-search/)
7. [Ternary search](https://www.geeksforgeeks.org/ternary-search/)
8. [Ternary search with example](https://www.youtube.com/watch?v=WyWL1PBNvb8)
9. [Jump search](https://www.geeksforgeeks.org/jump-search/)
10. [Jump search visualisation](https://harkishen-singh.github.io/jump-search-visualisation/)
11. [What is a jump search](https://www.educative.io/answers/what-is-a-jump-search)
12. [Interpolation search algorithm](https://www.tutorialspoint.com/data_structures_algorithms/interpolation_search_algorithm.htm)
13. [Interpolation search with example](https://www.youtube.com/watch?v=iMVKo1vXVsw)
14. [Exponential search](https://www.geeksforgeeks.org/exponential-search/)
15. [Exponential search with an example](https://www.youtube.com/watch?v=PaGRX7llaWU)
16. [Exponential Search Explained](https://www.freecodecamp.org/news/search-algorithms-exponential-search-explained/)
17. [Fibonacci search](https://www.geeksforgeeks.org/fibonacci-search/)
18. [Fibonacci search in data structures](https://www.youtube.com/watch?v=q_AVjuzBxoc)
19. [Working of fibonacci search](https://www.youtube.com/watch?v=OLMA_MEqgEA)
