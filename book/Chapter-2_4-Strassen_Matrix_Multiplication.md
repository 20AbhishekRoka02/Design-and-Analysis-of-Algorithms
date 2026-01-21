# Strassen's Matrix Multiplication

1. Suppose we have two $2 \times 2$ matrices

    $$
    A =
    \begin{bmatrix}
    a_{11} & a_{12} \\
    a_{21} & a_{22}
    \end{bmatrix}
    \;\&\;
    B =
    \begin{bmatrix}
    b_{11} & b_{12} \\
    b_{21} & b_{22}
    \end{bmatrix}
    $$

    Now, 

    $$
    A \times B =
    \begin{bmatrix}
    a_{11}b_{11}+a_{12}b_{21} & a_{11}b_{12} + a_{12}b_{22} \\
    a_{21}b_{11} + a_{22}b_{21} & a_{21}b_{12} + a_{22}b_{22}
    \end{bmatrix}
    $$

2. Here, we have total 8 multiplications to perform.
3. It generally takes Time Complexity of $O(n^3)$.
4. Strassen matrix multiplication makes the number of multiplications to $7$.
5. It reduces time complexity to $O(n^{\log_2 7}) \approx O(n^{2.81})$
6. Steps of Strassen's Matrix Multiplication:
    1. **Divide**
        - If size of both martices are $ 1 \times 1 $, then we return the multiplication of them.
        - Otherwise, we breakdown it to 4 matrices of size $ \frac{n}{2} \times \frac{n}{2} $
    2. **Conquer**
        - For $ \frac{n}{2} \times \frac{n}{2} $ matrix, we compute Strassen's 7 multiplications, which I will show in few moments.
        - Then, we compute $C_{11}, \space C_{12}, \space C_{21}\space \& \space C_{22}$
    3. **Merge**
         - Once we have computed the output, we return value to previous recursive call.
         - This way we are merging the matrix back to its $ n \times n $ form.
    4. **Base Case**
        - Here, we have base case of $ 2 \times 2 $, where we stop dividing & start conquering.
    
## Formula of Multiplications
1. Strassen Multiplication aims for:

    $$A \times B = 
    \begin{bmatrix} 
    a_{11} & a_{12} \\
    a_{21} & a_{22}
    \end{bmatrix} \times 
    \begin{bmatrix} 
    b_{11} & b_{12} \\
    b_{21} & b_{22}
    \end{bmatrix} =
    \begin{bmatrix} 
    C_{11} & C_{12} \\
    C_{21} & C_{22}
    \end{bmatrix}
    $$

- But with 7 multiplications: $ M_{1},\space M_{2},\space M_{3},\space M_{4},\space M_{5},\space M_{6}\space \& \space M_{7} $, which are:

1. $M_{1} = (a_{11} + a_{22}) \space (b_{11} + b_{22})$
2. $M_{2} = (a_{21} + a_{22}) \space b_{11}$
3. $M_{3} = a_{11} \space (b_{12} - b_{22})$
4. $M_{4} = a_{22} \space (b_{21} - b_{11})$
5. $M_{5} = (a_{11} + a_{12}) \space b_{22}$
6. $M_{6} = (a_{21} - a_{11}) \space (b_{11} + b_{12})$
7. $M_{7} = (a_{12} - a_{22}) \space (b_{21} + b_{22})$

- Then, we calculate $ C_{11},\space C_{12},\space C_{21},\space  \& \space C_{22} $, which are:
1. $C_{11} = M_{1} + M_{4} - M_{5} + M_{7} $
2. $C_{12} = M_{3} + M_{5} $
3. $C_{21} = M_{2} + M_{4} $
4. $C_{22} = M_{1} - M_{2} + M_{3} + M_{6} $

## Working
1. Suppose there are 2 matrices:

$$ A = 
\begin{bmatrix}
2 & 1 \\
3 & 4
\end{bmatrix}
\;\&\;
B =
\begin{bmatrix}
1 & 2 & 3 \\
4 & 5 & 6
\end{bmatrix} $$

2. Now, $A$ is $ 2 \times 2 $ but, $B$ is $ 2 \times 3 $
3. The next power of 2 is 4, so we convert them to $4 \times 4$ matrix, by padding them with Zeros $(0s)$

$$ A = 
\begin{bmatrix}
2 & 1 & 0 & 0 \\
3 & 4 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}
\;\&\;
B =
\begin{bmatrix}
1 & 2 & 3 & 0 \\
4 & 5 & 6 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix} $$

4. Now, our matrix gets divided into 4 parts of size $ \frac{n}{2} \times \frac{n}{2} $.
    ```
    Diagram of dividing the matrices into 4 parts
    ```
5. So, Matrix $A$ has $4$ parts:

$$
\begin{bmatrix}
2 & 1 \\
3 & 4
\end{bmatrix}
\; , \;
\begin{bmatrix}
0 & 0 \\
0 & 0
\end{bmatrix}
\; , \;
\begin{bmatrix}
0 & 0 \\
0 & 0
\end{bmatrix}
\; \& \;
\begin{bmatrix}
0 & 0 \\
0 & 0
\end{bmatrix}
$$

and, Matix $B$ has 4 parts:

$$
\begin{bmatrix}
1 & 2 \\
4 & 5
\end{bmatrix}
\; , \;
\begin{bmatrix}
3 & 0 \\
6 & 0
\end{bmatrix}
\; , \;
\begin{bmatrix}
0 & 0 \\
0 & 0
\end{bmatrix}
\; \& \;
\begin{bmatrix}
0 & 0 \\
0 & 0
\end{bmatrix}
$$

6. Let's try to calculate Strassen's $M_1$

$$ M_1 = 
\begin{bmatrix}
1 & 2 \\
4 & 5
\end{bmatrix}
\; \times \;
\begin{bmatrix}
3 & 0 \\
6 & 0
\end{bmatrix} $$

7. At this point, we have $ 2 \times 2 $ matrix multiplication, now we will call Strassen again, and there we will have $ 1 \times 1$ matrix multiplication, and return that value this call.

8. Once we get our multiplications done, then we calculate $ Cs $

## Algorithm

```{code}
multiplication(a, b) {
    // Here, a and b are matrices of size p x q and r x s
    // As there is p x q & r x s matrix multiplication, we require a square matrix.
    // So we find maximum of their number of rows & columns, and find new power of 2.

    p -> no. of rows in a
    q -> no. of columns in a
    r -> no. of rows in b
    s -> no. of columns in b

    m <- maximum of p, q, r and s

    // Now we take power of 2 of ceil value of log base 2 of m
    // ceil is opposite of floor
    // n is the n x n size for array
    n = 2 ^ ceil of log base 2 of m 

    // We add padding to Matrix A & B
    resizeA = padding(a, n, p, q)
    resizeB = padding(b, n, r, s)

    result = strassen(resizedA, resizedB, n)

    return result
}

padding(mt, n, row, col){
    // mt is matrix
    // n is size of array (n x n array)
    // row -> no. of rows in mt
    // col -> no. of columns in mt

    Create 2D array, arr, of size n x n filled with 0s

    for i from 0 to row - 1; do
        for j from 0 to col - 1; do
            arr[i][j] = mt[i][j]
    
    return mt
}

strassen(mta, mtb, size) {
    // mta -> first matrix in multiplication
    // mtb -> second matrix in multiplication
    // size -> size of both square martices

    if size == 1; then
        return mta[0][0] * mtb[0][0]
    

    // Otherwise, split matrix into 4 halves
    n = size / 2

    Create 8 2D arrays of size n x n computed above filled with zeroes & name a11, a12, a21, a22, b11, b12, b21 and b22

    Copy values for row 0 to n & column 0 to n in a11 from mta & b11 from mtb
    
    Copy values for row n + 1 to size - 1 & column 0 to n in a21 from mta & b21 from mtb

    Copy values for row 0 to n & column n + 1 to size - 1 in a12 from mta & b12 from mtb

    Copy values for row n + 1 to size - 1 & column n + 1 to size - 1 in a22 from mta & b22 from mtb

    Create 11 2D arrays of size n x n filled with zeros named m1, m2, m3, m4, m5, m6, m7, c11, c12, c21 and c22

    // Compute 7 multiplications
    m1 = strassen( add(a11, a22, n), add(b11, b22, n), n)
    m2 = strassen( add(a11, a22, n), b11, n)
    m3 = strassen( a11, sub(b12, b22, n), n)
    m4 = strassen( a22, sub(b21, b11, n), n)
    m5 = strassen( add(a11, a12, n), b22, n)
    m6 = strassen( sub(a21, a11, n), add(b11, b12, n), n)
    m1 = strassen( sub(a12, a22, n), add(b21, b22, n), n)

    c11 = sub( add( add( m1, m4, n), m7, n), m5, n) 
    c12 = add( m3, m5, n)
    c21 = add( m2, m4, n)
    c22 = add( sub(m1, m2, n), add(m3, m6, n), n)

    Create 2D array result of size n x n

    for i from 0 to n - 1; do
        for j from 0 to n - 1; do
            result[i][j] = arr[i][j]
            result[i][j+n] = arr[i][j+n]
            result[i+n][j] = arr[i+n][j]
            result[i+n][j+n] = arr[i+n][j+n]
}

add( mta, mtb, n) {
    for i from 0 to n - 1; do
        for j from 0 to n - 1; do
            mta[i][j] += mtb[i][j]
    return mta
}

sub(mta, mtb, n) {
    for i from 0 to n - 1; do
        for j from 0 to n - 1; do
            mta[i][j] -= mtb[i][j]
    return mta

}
```

## Few points
1. The Strassen's multiplication is **good choice** for large matrices, because for small it has overhead of recursize calls.

2. It is **bad choice** for Sparse Matrix because it will spend time in addition of zeros.

3. It is a **best choice** for dense matrices & large matrices such as 32 x 32, 64 x 64 etc.