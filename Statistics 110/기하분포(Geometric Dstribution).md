# $Geom(p)$
independent $Bern(p)$ trials, count number of failures before 1st success. Let $X~Geom(p)$

## PMF
$$P(X=k)=q^kp,\ k \in \{0, 1, 2, \cdots\}$$
valid since,
$$ \sum_{k=0}^{\infty}pq^k = \frac{p}{1-q} = 1$$
## Expected Value
### Way 1
$E(X) = \sum_{k=0}^{\infty}kpq^k = p \sum_{k=1}^{\infty}kq^k = \frac{q}{p}$
- $\sum_{k=0}^{\infty}q^k = \frac{1}{1-q}$
- 위의 식을 양 변을 미분하면, $\sum_{k=1}^{\infty}kq^{k-1}=\frac{1}{(1-q)^2}$
- 따라서, $\sum_{k=1}^{\infty}kq^k= \frac{q}{p^2}$
$$ E(X)=\frac{q}{p}$$
#### story proof
Let $c = E(X)$
$c = 0 \cdot p + (1 + c) \cdot q = q +cq \Rightarrow \frac{q}{p}$
