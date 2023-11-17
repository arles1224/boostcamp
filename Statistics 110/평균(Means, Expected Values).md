# Everages(means, expected values)
Everage is telling you one number summary of center of the distribution.

## Everage of arithmetic series

$$\frac{1}{n} \sum_{j=1}^{n}i = \frac{n+1}{2}$$

## Everage of reputitive number
Numbers: ${1, 1, 1, 1, 1, 3, 3, 5}$

- Way 1: add, devide
  $$ \frac{1+1+1+1+1+3+3+5}{8} = 2$$
- Way 2: group numbers, average groups, weight average
$$ \frac{5}{8} \cdot 1 + \frac{2}{8} \cdot 3 + \frac{1}{8} \cdot 5 = 2$$
> **Weighted average** is very crucial to understand what's going on.

## Average of a discrete random variable $X$
$$ E(X)= \sum_{x}^{} x P(X=x)$$
### In case of $X \sim Bern(p)$
$$ E(X) = 1 \cdot P(X=1) + 0 \cdot P(X=0) = p$$
: fundemental bridge
### In case of $X \sim Bin(n,p)$
$$ E(X) = np$$

$E(X) = \sum_{k=0}^{n} k \cdot {_nC_k} p^k q^{n-k} = \sum_{k=0}^{n} n \cdot _{n-1}C_{k-1} p^k q^{n-k} = np \sum_{k=1}^{n}\  _{n-1}C_{k-1}p^{k-1} q^{n-k}$

$=np\sum_{j=0}^{n-1} \ _{n-1}C_{j} p^j q^{n-j-1} = np$

#### **LINEARITY OF EXPECTATION**
$$ E(X+Y) = E(X) + E(Y) $$
$$ E(cX) = cE(X)$$



