# Supervise Learning 2 - Regression

## Linear Regression and Function Approximation

Regression is a misused named. Owes to the fact that extremely tall/short peoples' childrens' height regresses (tends toward the average i.e. children of tall people shorter than tall person, taller than avg). (slope of parent height to child height approx. 2/3)

When this relationship was discovered other mathemticians/scientists stole the term regression to mean finding mathematical relationship to describe physical phenomenon.

## Finding the Best Fit (Loss or Error function)

Use calculus! Typically square is used for error

```
E(c) = sum_i^n (y_i - c)^2
```

Take the derivative and find where derivative = 0 (minimum)

This can be extrapolated to higher orders of polynomials. Typically the higher the order the better the fit because you have more degrees of freedom but you can run into the issue of over-fitting.

## Polynomial Regression

For a set of x = (x_1, x_2, ..., x_n) and y = (y_1, y_2, ..., y_n)

The goal is to find an set of constant weights such that  

```tex
c_0 + c_1 x + c_2 x^2 + ... + c_m \approx y
```

You can arrange constraints in matrix form:

```tex
\begin{bmatrix}
 1  & x_1 & x_1^2 & ... & x_1^m\\ 
 1  & x_2 & x_2 & ... & x_2^m\\ 
 ...  &  &  & \\ 
 1  & x_n & x_n^2 & ... & x_n^m
\end{bmatrix}
\cdot \
begin{bmatrix}
c_0\\ 
c_1\\ 
...\\ 
c_m
\end{bmatrix} 
\approx 
\begin{bmatrix}
y_1\\ 
y_2\\ 
...\\ 
y_m
\end{bmatrix} \linebreak

```

```tex
\begin{align}
X w &\approx Y \\
X^TXw &\approx X^TY \\
(X^T X)^{-1} X^TXw &\approx (X^TX)^{-1}X^TY \\
w &\approx (X^TX)^{-1}X^TY
\end{align}
```

Can't solve exactly (won't be exactly equal) but it can be solved in a least squares sense

Note that you can't solve the equation exactly. There will be outside sources of ** error ** such as sensor error, malicious or bad data, transcription error, or unmoddled influences.