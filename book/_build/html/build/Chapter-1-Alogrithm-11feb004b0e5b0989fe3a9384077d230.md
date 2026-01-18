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

### Asymptotic Notation
1. Sometimes, we compare bunch of algorithms together, some are slower, some are faster, while other takes almost same time and space.
2. Suppose if we have algorithms $A$, $B$, $C$ and $D$
    1. If we come with a time comparisons of these algorithms, at an instant, for an input size of 8, we have:
        1. $A$ takes 2 milliseconds
        2. $B$ takes 4 milliseconds
        3. $C$ takes 1 milliseconds
        4. $D$ takes 8 milliseconds
    2. Now, we want to compare it for all input sizes till infinity $\infty$
    3. We will get a vast table for comaprisons among these values, and we plot a graph.
    [ Show graphs of A, B, C and D]
    4. But, NONE of us wants to REMEMBER THIS!
3. So, we remember the order of their functions, for example, for the graph like this:

    * We say it's graph of $n^2$
    * In algorithm, it must have nested iteration, like below, in triangle.
    ```{code-cell}
    for(int i=0; i<5; i++) {
        for (int j=0; j<i+1; j++) {
            cout << "*";
        }
        cout << endl;
    }
    ```

    ```{code-cell}
    :tags: [hide-input]

    for i in range(1, 6):
        print("*"*i)
    ```