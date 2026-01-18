---
kernelspec:
  name: python3
  display_name: 'Python 3.14'
---
# Chapter 1: Algorithm

## Algorithm
_"It is a set of well defined steps, which are followed to solve a problem"_

Example:
1. Brushing Teeth
2. Making Tea
3. Determine best profit for thief in a Knapsack
4. Help salesperson travel all cities with minimal cost to meet monthly targets

### Characteristics of an Algorithm
There are 5 key characteristics of an algorithm:-
#### 1. Definiteness
* Every step is meaningful and unambiguous for the reader.
* For example: Increase value of $x$ by $1$, instead of make $x$ bigger.

#### 2. Finiteness
* Every algorithm must have finite number of steps.

#### 3. Input
* An algorithm must accept zero or more inputs.

#### 4. Output
* It must produce atleast one output.

#### 5. Effectiveness 
* It must be followed easily, even with pen and paper.

## Pseudo Code
1. It is the most effective way to represent an algorithm.
2. It is in normal english language.
3. It is written as a sequence of steps.

Example:
### Psuedo code for making a Tea

Steps are as follows:-
1. Get:
    1. A $\frac{3}{4}$ cup of drinking water
    2. A vessel (_patila_)
    3. A $\frac{1}{2}$ tea spoon of tea leaves (_chai patti_)
    4. Ginger (1 gram)
    5. 2 tea spoons of sugar
    6. A $\frac{1}{2}$ cup of milk
    7. Filter (_channi_)
2. Light the stove to medium flame and place vessel.
3. Put $\frac{3}{4}$ cup of water.
4. Add tea leaves, crushed ginger and sugar.
5. Wait till water begins to boil.
6. Add milk
7. Once the solution begins to boil, and comes to the brim of the vessel, turn off the flame.
8. Now, filter the tea from vessel to cup.

This is how we write Pseudo Code of a problem!

## Performance Analysis
1. Actually, we have discussed only way of making a tea.
2. Here, we have allocated our ingredients before, then prepared the tea.
3. So, it make our process faster, but used up too many resources such as:
    1. 2 cups for water and milk
    2. 3 tea spoons for tea leaves and sugar
4. Instead of using 2 cups, we can use just 1 cup to put water first, then, milk.
5. We can solve the same approach the other way, where we will access ingredients and resources when required, no pre-allocations!
6. Now, this will save our resources, but increase time spent to make a tea, because there will be extra time to get resources and ingredients.
7. Similarly, for other approaches, to make the same tea, we analyse their performance based on their:
    1. Time, and
    2. Space
8. And, this is what we study in this subject, when we go for analysis part of an algorithm.
9. We look for their:
    1. Time Complexity
        * It is the time taken by an algorithm to solve our problem.
    2. Space Complexity
        * It is the space taken by algorithm to solve a problem.

### Order of Function
1. Sometimes, we compare bunch of algorithms together, some are slower, some are faster, while other takes almost same time and space.
2. Suppose if we have algorithms $A$, $B$, $C$ and $D$
    1. If we come with a time comparisons of these algorithms, at an instant, for an input size of 8, we have:
        1. $A$ takes 2 milliseconds
        2. $B$ takes 4 milliseconds
        3. $C$ takes 1 milliseconds
        4. $D$ takes 8 milliseconds
    2. Now, we want to compare it for all input sizes till infinity $\infty$
    3. We will get a vast table for comaprisons among these values, and we plot a graph.

    ```
    [ Show graphs of A, B, C and D] as n, n^2, n and 2^n with label for time
    ```
    4. But, NONE of us wants to REMEMBER THIS!
3. So, we remember the order of their functions, for example, for the graph like this:

    * We say it's graph of $n^2$
    * In algorithm, it has nested loops, like below, in triangle.
    ```{code}
    for(int i=0; i<5; i++) {
        for (int j=0; j<i+1; j++) {
            cout << "*";
        }
        cout << endl;
    }
    ```

    ```{code-cell}
    :tag: remove-input
    for i in range(1, 6):
        print("*"*i)
    ```
4. Similarly, we have other order of functions defined as follows:
    ```{csv-table} 
    :header: "Order of Function", "Their Meaning"

    "$1$", "Constant time to solve for input of any size"
    "n", "rate of growth in time/space same as input size growth"
    "$n^2$", "loop in a loop"
    "$n^3$", "loop in a loop in a loop"
    "$log(n)$", "Problem getting divided into halves, like binary search"
    "$nlog(n)$", "one part grows as $n$, other as $log(n)$, like merge sort"
    "$2^n$", "Time/Space increasing exponentially, like Travelling Salesperson problem"
    ```
### Asymptotic Notation
1. Our algorithms need not to act the same always.
2. For instance, a Binary Search NOT always takes $log(n)$ time to search an element, sometimes, we find element on first check.
3. In that case, Order of function would be $1$.
4. So, our algorithm have:
    1. Best Case Scenario - best performance
    2. Worst Case Scenario - worst performance
    3. Average Case Scenario - average performance
5. For this, we have a mathematical framework, named Asymptotic Notation.
    #### Defination
    _"It is a mathematical framework which is used to analyse an algorithm for its efficiency as input size $(n)$ grows to infinity $(\infty)$"_
6. There are 3 types of Asymptotic Notations:-
    1. Big O notation (Worst Case)
    2. Big Omega $(\Omega)$ notation (Best Case)
    3. Big Theta $(\Theta)$ notation (Average Case)

#### Big O Notation
```
    Big O graph goes here

    with caption below the graph as:
    Here, n0 -> Threshold size of input (i.e. minimum input size, after which functions (algorithms) show their true behavior)
    f(n) -> Our function (algorithm) which is under analysis.
    g(n) -> Another function (algorithm) having higher rate of growth than our function (algorithm)
```
Due to above graph, it is also known as **Upper Bound**.
##### Defination
_A function $f(n)$ is said to be $O(g(n))$, if there exists positive constants, c & $n_{0}$, such that:_
$$ 0 \leq f(n) \leq c(g(n)); \forall n \geq n_{0}$$

1. It means, how **bad** our algorithm will perform, as input size grows.
2. High rate of growth, is a **bad sign**, for an algorithm.

#### Big Omege $(\Omega)$ Notation
```
    Big Omega graph goes here

    with caption below the graph as:
    Here, n0 -> Threshold size of input (i.e. minimum input size, after which functions (algorithms) show their true behavior)
    f(n) -> Our function (algorithm) which is under analysis.
    g(n) -> Another function (algorithm) having lower rate of growth than our function (algorithm)
```
Due to above graph, it is also known as **Lower Bound**.
##### Defination
_A function $f(n)$ is said to be $\Omega(g(n))$, if there exists positive constants, c & $n_{0}$, such that:_
$$ 0 \leq c(g(n)) \leq f(n); \forall n \geq n_{0}$$

1. It means, how **best** our algorithm will perform, as input size grows.
2. Lower the rate of growth, is **better**.

#### Big Theta $(\Theta)$ Notation
```
    Big Theta graph goes here

    with caption below the graph as:
    Here, n0 -> Threshold size of input (i.e. minimum input size, after which functions (algorithms) show their true behavior)
    f(n) -> Our function (algorithm) which is under analysis.
    g(n) -> Another function (algorithm) having lower rate of growth than our function (algorithm)
```
Due to above graph, it is also known as **Tight Bound**.
##### Defination
_A function $f(n)$ is said to be $\Theta(g(n))$, if there exists positive constants, $c_{1}$, $c_{2}$ & $n_{0}$, such that:_
$$ 0 \leq c_{1}(g(n)) \leq f(n) \leq c_{2}(g(n)); \forall n \geq n_{0}$$

1. It means, **average** performance of an algorithm.
2. Lies between Upper bound and Lower bound.

### Elementary Data Structures
#### Stack
```
    Stack Diagram goes here
```
<!-- Add separation -->
```{figure} ./1.jpg
This is a caption in **Markdown**
```


1. It is a linear data structure, i.e. elements are accessed one after another, like we have place plates one over another in wedding.
2. It has only end for storing (Push) and removing (Pop) an element.
3. It operates on LIFO (Last In First Out) principle.
4. Structure of a stack:
    1. TOP - It is a pointer to the topmost element of the stack.
    2. IN - It is the input direction of an element on the top of the stack.
    3. OUT - It is the output direction of an element from the top of the stack.

##### Operations on stack
1. **Push**
    * It refers to storing element on the top of the stack.
    * During push, TOP get incremented by 1, and we store element at that location, with:
        ```{code} 
        TOP++;
        stack[TOP] = element;
        ```
2. **Pop**
    * It refers to removing element from the top of the stack.
    * During pop, we simply decrement TOP by 1
        ```{code}
        TOP--;
        ```
3. **Peek**
    * It refers to view the TOP element of stack, with:
    ```{code}
    stack[TOP];
    ```

4. **isEmpty**
    * It checks whether stack is empty or not.
    * It returns boolean value: 0 (false) / 1 (true)
    ```{code}
    if (TOP == -1) then
        return 1; // i.e. stack is empty
    else
        return 0; // i.e. stack is not empty
    ```
5. **isFull**
    * It checks whether stack is full or not.
    * It returns boolean value: 0 (false) / 1 (true)
    ```{code}
    if (TOP == MAX) then
        return 1; // i.e. stack is full
    else
        return 0; // i.e. stack is not full
    ```
