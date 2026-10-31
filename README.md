# HackerRank Java Practice – PC#1 ICT 21 Batch

This repository documents two solved HackerRank Java (Basic) problems from the **PC#1 – ICT 21 Batch** contest.

## Contest Status

Both problems are marked as **Solved** in the HackerRank contest page.

![HackerRank contest leaderboard showing both problems solved](assets/leaderboard.png)

## 1. Prime Checker

- **Difficulty:** Medium
- **Language:** Java 7
- **Maximum Score:** 3
- **Concepts:** Varargs, methods, prime-number checking

### Problem Summary

Create a class named `Prime` with one method named `checkPrime`. The method must accept one or more integer arguments and print only the prime numbers. The method must not be overloaded.

### Solution Code

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;
import java.lang.reflect.*;
import static java.lang.System.in;

class Prime {
    public void checkPrime(int... numbers) {
        for (int n : numbers) {
            boolean prime = true;

            if (n <= 1) {
                prime = false;
            } else {
                for (int i = 2; i <= Math.sqrt(n); i++) {
                    if (n % i == 0) {
                        prime = false;
                        break;
                    }
                }
            }

            if (prime) {
                System.out.print(n + " ");
            }
        }
        System.out.println();
    }
}

public class Solution {
    public static void main(String[] args) {
        try {
            BufferedReader br = new BufferedReader(new InputStreamReader(in));

            int n1 = Integer.parseInt(br.readLine());
            int n2 = Integer.parseInt(br.readLine());
            int n3 = Integer.parseInt(br.readLine());
            int n4 = Integer.parseInt(br.readLine());
            int n5 = Integer.parseInt(br.readLine());

            Prime ob = new Prime();
            ob.checkPrime(n1);
            ob.checkPrime(n1, n2);
            ob.checkPrime(n1, n2, n3);
            ob.checkPrime(n1, n2, n3, n4, n5);

            Method[] methods = Prime.class.getDeclaredMethods();
            Set<String> set = new HashSet<>();
            boolean overload = false;

            for (int i = 0; i < methods.length; i++) {
                if (set.contains(methods[i].getName())) {
                    overload = true;
                    break;
                }
                set.add(methods[i].getName());
            }

            if (overload) {
                throw new Exception("Overloading not allowed");
            }
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}
```

### Sample Input

```text
2
1
3
4
5
```

### Expected Output

```text
2
2
2 3
2 3 5
```

### Explanation

- `int... numbers` is Java **varargs**, so one method can receive different numbers of integer arguments.
- A number less than or equal to `1` is not prime.
- For each number greater than `1`, the loop checks whether it is divisible by any integer from `2` through its square root.
- If a divisor is found, the number is not prime. Otherwise, it is printed.
- Only one `checkPrime` method is declared, so method overloading is avoided.
- `import static java.lang.System.in;` makes the locked code's `in` identifier refer to `System.in`.

### Submission Result

![Prime Checker successful HackerRank submission](assets/prime_checker_result.png)

**Status: Successfully solved.**

---

## 2. Java Primality Test

- **Difficulty:** Easy
- **Language:** Java 7
- **Maximum Score:** 2
- **Concepts:** `BigInteger`, `Scanner`, `isProbablePrime()`

### Problem Summary

Read one potentially large integer and determine whether it is prime using the Java `BigInteger` class's `isProbablePrime()` method.

Print:
- `prime` if the number is prime.
- `not prime` otherwise.

### Solution Code

```java
import java.io.*;
import java.math.*;
import java.util.*;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        BigInteger n = sc.nextBigInteger();

        if (n.isProbablePrime(1)) {
            System.out.println("prime");
        } else {
            System.out.println("not prime");
        }

        sc.close();
    }
}
```

### Sample Input

```text
13
```

### Expected Output

```text
prime
```

### Explanation

The only positive divisors of `13` are `1` and `13`, so it is a prime number.

- `BigInteger` stores integers larger than the range of primitive types such as `int` and `long`.
- `nextBigInteger()` reads the input as a `BigInteger`.
- `isProbablePrime(1)` performs a probabilistic primality test. The argument `1` is the certainty parameter; a higher value gives a stronger confidence that a reported prime is actually prime.
- The `if-else` statement prints the required result.

### Submission Result

![Java Primality Test successful HackerRank submission](assets/java_primality_test_result.png)

**Status: Successfully solved.**

---

## Summary

| Problem | Main Java Concept | Status |
|---|---|---|
| Prime Checker | Varargs and prime checking | Solved |
| Java Primality Test | BigInteger and `isProbablePrime()` | Solved |

## Technologies

- Java 7
- HackerRank
- Java Standard Library

