# 10.1 Fibonacci Sequence

## Question link

## Title Description

Find the nth term of the Fibonacci sequence, where n \<= 39.

<!--<div align="center"><img src="https://latex.codecogs.com/gif.latex?f(n)=\left\{\begin{array}{rcl}0&&{n=0}\\1&&{n=1}\\f(n-1)+f(n-2)&&{n>1}\end{array}\right." class="mathjax-pic"/></div> <br> -->

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/45be9587-6069-4ab7-b9ac-840db1a53744.jpg" width="330px"> </div><br>

## Problem Solving Ideas

If recursive solution is used, some sub-problems will be calculated repeatedly. For example, to calculate f(4), it is necessary to calculate f(3) and f(2), and to calculate f(3), it is necessary to calculate f(2) and f(1). It can be seen that f(2) is calculated repeatedly.

<div align="center"> <img src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/c13e2a3d-b01c-4a08-a69b-db2c4e821e09.png" width="350px"/> </div><br>

Recursion is to divide a problem into multiple sub-problems to solve, and the same is true for dynamic programming, but dynamic programming will cache the solutions to the sub-problems to avoid repeatedly solving the sub-problems.

```java
public int Fibonacci(int n) {
    if (n <= 1)
        return n;
    int[] fib = new int[n + 1];
    fib[1] = 1;
    for (int i = 2; i <= n; i++)
        fib[i] = fib[i - 1] + fib[i - 2];
    return fib[n];
}
```

Considering that the i-th item is only related to the i-1-th and i-2-th items, we only need to store the values ​​of the first two items to solve the i-th item, thus reducing the space complexity from O(N) to O(1).

```java
public int Fibonacci(int n) {
    if (n <= 1)
        return n;
    int pre2 = 0, pre1 = 1;
    int fib = 0;
    for (int i = 2; i <= n; i++) {
        fib = pre2 + pre1;
        for2 = for1;
        pre1 = fib;
    }
    return fib;
}
```

Since the number n to be solved is less than 40, the results of the first 40 items can be calculated first, and then the value of the nth item can be obtained with O(1) time complexity.

```java
public class Solution {

    private int[] fib = new int[40];

    public Solution() {
        fib[1] = 1;
        for (int i = 2; i < fib.length; i++)
            fib[i] = fib[i - 1] + fib[i - 2];
    }

    public int Fibonacci(int n) {
        return fib[n];
    }
}
```