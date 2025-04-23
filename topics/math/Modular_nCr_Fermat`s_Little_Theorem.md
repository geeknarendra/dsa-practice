# Math Topic

## Basic Arithmetic
- Example: `16 / 4 = 4` (Normal division)

## Modular Arithmetic
- Modular arithmetic focuses on the **remainder** when a number is divided by another.
  - Example: `100 % 3` gives the remainder `1`

---

## nCr Formula  
```
nCr = n! / (r! * (n - r)!)
```

- Since `nCr` can be very large, we calculate it under a modulo.
- Typically:
  ```
  (nCr) % MOD
  ```
  where `MOD = 10^9 + 7` (a large prime number)

---

## Why Modular Arithmetic is Tricky with Fractions

- Example:
  ```
  (3 / 2) % 7
  ```
  This results in `1.5 % 7`, which is not valid in modular arithmetic.

- Instead, we use the **modular inverse**:
  ```
  (3 * pow(2, -1)) % 7
  ```

---

## Modular Inverse

We want to find `P` such that:
```
(2 * P) % 7 = 1
```
Try values until it fits:
- `P = 4` → `2 * 4 % 7 = 8 % 7 = 1` ✅

So,
```
(3 * 4) % 7 = 12 % 7 = 5
```

---

## Fermat’s Little Theorem

To compute the modular inverse efficiently when `MOD` is prime:
```
pow(a, MOD - 2, MOD)
```

This is because:
```
a^(MOD - 1) ≡ 1 (% MOD)
```

So,
```
a^(-1) ≡ a^(MOD - 2) (% MOD)
```

---

## Applying Fermat’s Theorem to Modular nCr

We want to compute:
```
nCr % MOD = (n! * inverse(r!) * inverse((n - r)!)) % MOD
```

Using Fermat's:
- Compute `a = fact(n) % MOD`
- Compute `b = (fact(r) * fact(n - r)) % MOD`
- Final Result:
  ```
  (a * pow(b, MOD - 2, MOD)) % MOD
  ```

---

## Python Code

```python
def fact(num, MOD):
    res = 1
    for i in range(2, num + 1):
        res = (res * i) % MOD
    return res

def findPower(a, b, MOD):
    res = 1
    a %= MOD
    while b > 0:
        if b % 2 == 1:
            res = (res * a) % MOD
        a = (a * a) % MOD
        b //= 2
    return res

def findModularnCr(n, r, MOD):
    if r < 0 or r > n:
        return 0
    a = fact(n, MOD)
    b = (fact(r, MOD) * fact(n - r, MOD)) % MOD
    return (a * findPower(b, MOD - 2, MOD)) % MOD
```

---

## Key Concepts

1. **Modular Arithmetic** handles remainders.
2. **Modular Inverse** is required for division in modular arithmetic.
3. **Fermat’s Little Theorem** helps compute modular inverses efficiently.

---

## Related Questions

- 🔗 [LeetCode: Count the Number of Ideal Arrays](https://leetcode.com/problems/count-the-number-of-ideal-arrays/description/)
- 📄 [Solution File](../../daily/2338_Count_The_Number_Of_Ideal_Arrays_2025_04_22.md)

---

## Resources

- 📹 [Modular nCr using Fermat’s Little Theorem – YouTube](https://www.youtube.com/watch?v=FMBW7m1Wap0)
