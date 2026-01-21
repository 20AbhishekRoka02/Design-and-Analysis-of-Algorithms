# Chapter 2: Divide and Conquer
1. It is one of the well known problem solving technique, where we breakdown a given problem and solve it.
2. Suppose we have to find marks of a student from the pile of marksheets (ordered alphabetically), so we can divide the pile into several parts based on starting letter alphabet of the name, like A, B, C ... Z.
3. To find marksheet of a student named Aditya, we will access Part A (containing marks of students name starting with A) only, and not required to access other part of the pile. Then we will find the marksheet of student.

## Working of Divide & Conquer
1. It is a 3 step process
    1. **Divide**
        1. Divide a given problem into separate subproblems
        2. Separate subproblems means, it must be _independent_ from other subproblems.
        3. For example, in pile of marksheets, to find marks of Aditya, we will access only that part of pile which is starting with A.
        4. There will be no benefit to conduct search on rest of the pile.
        5. Similarly, for Gaurav, we will access starting with G part of the pile.
    2. **Conquer**
        * Now, we solve the given subproblems independently and get its solution.
    3. **Merge**
        1. Here, we merge the solution of subproblems.
        2. It is an optional step
        3. Like, for searching Aditya's marksheet, we do not have to perform any merge operation
        4. But we will merge solutions in problems like sorting elements of an array with Merge Sort.

### Advantages
1. **Easy to implement**
    * As we have to divide a problem into subproblems and solve them independently.
    * There is no overlapping of subproblems like we will have in Dynamic Programming problems.
2. **Parallelism**
    * Here, we can compute solution of independent subproblems in parallel.
3. **Easy to design solutions**
    * It's solution can be implemented recursively, which will make designing easy.
### Disadvantages
1. **Overhead**
    * We have to compute solutions for all sub problems independently.
    * As there is no overlapping in sub problems, so solution of one cannot be used in a solution of another sub problem.
2. **Memory Consumption**
    * As we have to compute solutions for every sub problem, and there is no overlapping.
    * This lead to memory consumption for storage of solutions of them, so we can merge them as a single solution, later on.

### Applications
We will discuss following applications of Divide and Conquer approach in this book
1. Binary Search
2. Quick Sort
3. Merge Sort
4. Strassen's Matrix Multiplication Algorithm


