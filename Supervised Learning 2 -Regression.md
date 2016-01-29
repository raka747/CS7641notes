# Supervise Learning 2 - Regression

## Linear regression and function approximation

Regression is a misused named. Owes to the fact that extremely tall/short peoples' childrens' height regresses (tends toward the average i.e. children of tall people shorter than tall person, taller than avg). (slope of parent height to child height approx. 2/3)

When this relationship was discovered other mathemticians/scientists stole the term regression to mean finding mathematical relationship to describe physical phenomenon.

## Finding the best fit (Loss or Error function)

Use calculus! Typically square is used for error

```
E(c) = sum_i^n (y_i - c)^2
```

Take the derivative and find where derivative = 0 (minimum)

This can be extrapolated to higher orders of polynomials. Typically the higher the order the better the fit because you have more degrees of freedom but you can run into the issue of over-fitting.

## Polynomial regression

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

## Cross validation

Going from linear to a higher order polynomial can allow you to better fit the training data however when testing against the test set this leads to potentially large difference. One way is to train agains the test data, but that's cheating -- This doesn't generalize to the real world... D:

> An assumption here is that the training and test data is representative of real-world data. Statatisticians would say the data is Independent and Identically Distributed (IID) or that there's no inherent difference between training, testing, or realworld data. 

> This isn't necessarily a fundamental assumption of supervised learning. It's a fundamental assumption of many of the discussed algorithms. However there is research into algorithms that still perform well despite breaking this assumption

The ultimate goal is to use a model that is complex enough to fit the data well without causing problems generalizing to the test set. In order to accomplish this use part of the training data as a "test test" set, trial set, or cross validation set. This allows you to test without using the actual test set.

1. Split the training data into folds

2. | Train on    | Test on  | 
| ---------------|----------| 
| Fold 1, 2, 3   | Fold 4   |
| Fold 2, 3, 4   | Fold 1   |
| Fold 1, 3, 4   | Fold 2   |
| Fold 1, 2, 4   | Fold 3   |



## Other input spaces


## Summary
