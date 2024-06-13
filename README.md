# 18.AFB-WhileBis

One can assign names (labels) to loops, like this:

```java
LAB1: for (int i = 0; i < size; ++i) {
    // ...
    LAB2: while (cond1) {
        // ...
        if (cond2) break LAB1;
        // ...
        while (cond3) {
            // ...
            if (cond4) continue LAB2;
            // ...
        }
    }
}
```

where `LAB` is any identifier. Named loops may be used with all types of loops (`while`-loop, `do-while`-loop, and `for`-loop). The advantage of naming loops is that we can use the labels in `break` and `continue` instructions inside nested loops. Without them, both `break` and `continue` instructions always apply to the innermost loop only.

## Listing 18 AFB-WhileBis/Prime.java Page 38

```java
import java.util.Scanner;

public class Prime {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        MAIN_LOOP:
        while (true) {
            System.out.print("Enter natural number (0 to exit) -> ");
            int n = scan.nextInt();

            if (n == 0) break;

            if (n == 1) {
                System.out.println("Number 1 is neither prime nor composite");
                continue;
            } else if (n > 2 && n % 2 == 0) {
                System.out.println("Number " + n + ", being even, is composite");
                continue;
            } else {
                int p = 3;
                while (p * p <= n) {
                    if (n % p == 0) {
                        System.out.println("Number " + n + " is composite");
                        continue MAIN_LOOP;
                    }
                    p += 2;
                }
                System.out.println("Number " + n + " is prime");
            }
        }
        scan.close();
    }
}
```
