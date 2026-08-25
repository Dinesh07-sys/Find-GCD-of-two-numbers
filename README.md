# Find GCD Using the Euclidean Algorithm

A compact implementation of the Euclidean algorithm for finding the Greatest Common Divisor of two integers.

The algorithm repeatedly calculates remainders and reduces the problem until one of the numbers becomes zero. The remaining non-zero value is the GCD.

## Example

For:

```text
n1 = 20
n2 = 15
```

The program produces:

```text
GCD of 20 and 15 is: 5
```

## How the Algorithm Works

The Euclidean algorithm is based on the relationship:

```text
GCD(a, b) = GCD(b, a % b)
```

The larger value is repeatedly replaced by the remainder.

For `20` and `15`:

```text
20 % 15 = 5
15 % 5  = 0
```

Once the remainder becomes zero, the other value is the GCD:

```text
GCD = 5
```

## Implementation

```python
def find_gcd(a, b):
    while a > 0 and b > 0:
        if a > b:
            a = a % b
        else:
            b = b % a

    if a == 0:
        return b

    return a


def main():
    n1 = 20
    n2 = 15

    gcd = find_gcd(n1, n2)

    print(f"GCD of {n1} and {n2} is: {gcd}")


if __name__ == "__main__":
    main()
```

## Step-by-Step Example

Take:

```text
a = 20
b = 15
```

Since `a > b`:

```text
a = 20 % 15
a = 5
```

Now:

```text
a = 5
b = 15
```

Since `b > a`:

```text
b = 15 % 5
b = 0
```

The loop stops because `b` is zero.

The remaining non-zero value is:

```text
5
```

Therefore:

```text
GCD(20, 15) = 5
```

## Why the Euclidean Algorithm?

A naive approach could test every number from `1` up to the smaller input and find the largest common divisor.

The Euclidean algorithm is much more efficient because every iteration reduces the size of the problem significantly.

Instead of:

```text
Check 1
Check 2
Check 3
...
```

it works through remainders:

```text
20 → 15 → 5 → 0
```

## Complexity Analysis

Let `a` and `b` be the two input values.

| Metric | Complexity |
|---|---|
| Time Complexity | `O(log(min(a, b)))` |
| Auxiliary Space | `O(1)` |

The Euclidean algorithm has logarithmic time complexity because the values shrink rapidly through repeated remainder operations.

## Concepts Covered

- Functions
- `while` loops
- Conditional statements
- Modulo operator `%`
- Euclidean algorithm
- Greatest Common Divisor
- Mathematical problem solving

## Test Cases

### Example 1

```text
Input:
20 15

Output:
5
```

### Example 2

```text
Input:
48 18

Output:
6
```

### Example 3

```text
Input:
100 25

Output:
25
```

## Important Note

The current implementation assumes positive integers because the loop condition is:

```python
while a > 0 and b > 0:
```

Handling zero and negative inputs would require additional input normalization.

---

The important takeaway is the reduction rule:

```text
GCD(a, b) = GCD(b, a % b)
```
