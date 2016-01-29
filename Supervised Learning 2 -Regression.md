# Supervise Learning 2 - Regression
linear regression and function approximation

regression misused named. Owes to the fact that extremely tall/short peoples' childrens' height regresses (tends toward the average i.e. children of tall people shorter than tall person, taller than avg). (slope of parent height to child height approx. 2/3)

When this relationship was discovered other mathemticians/scientist stole the term regression to mean finding mathematical relationship to describe physical phenomenon.

Finding the best Fit (Loss or Error function)


typically square is used for error
```
E(c) = sum_i^n (y_i - c)^2
```

Take the derivative and find where derivative = 0 (minimum)

## Polynomial Regression
Have x = (x_1, x_2, ..., x_n) and y = (y_1, y_2, ..., y_n)

Find 

```tex
c_0 + c_1 x + c_2 x^2 + ... + c_m \approx y
```

Arrange constraints in matrix form

```tex
\begin{bmatrix}
 1  & x_1 & x_1^2 & ... & x_1^m\\ 
 1  & x_2 & x_2 & ... & x_2^m\\ 
 ...  &  &  & \\ 
 1  & x_n & x_n^2 & ... & x_n^m
\end{bmatrix}\cdot \begin{bmatrix}
c_0\\ 
c_1\\ 
...\\ 
c_m
\end{bmatrix} \approx \begin{bmatrix}
y_1\\ 
y_2\\ 
...\\ 
y_m
\end{bmatrix}

```
Can't solve exactly (won't be exactly equal) but it can be solved in a least squares sense