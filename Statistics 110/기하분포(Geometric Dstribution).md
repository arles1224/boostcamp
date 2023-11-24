# $Geom(p)$
independent $Bern(p)$ trials, count number of failures before 1st success. Let $X~Geom(p)$

## PMF
$$P(X=k)=q^kp,\ k \in \{0, 1, 2, \cdots\}$$
valid since,

$$ \sum_{k=0}^{\infty}pq^k = \frac{p}{1-q} = 1$$

## 기댓값

$E(X) = \sum_{k=0}^{\infty}kpq^k = p \sum_{k=1}^{\infty}kq^k = \frac{q}{p}$
- $\sum_{k=0}^{\infty}q^k = \frac{1}{1-q}$
- 위의 식을 양 변을 미분하면, $\sum_{k=1}^{\infty}kq^{k-1}=\frac{1}{(1-q)^2}$
- 따라서, $\sum_{k=1}^{\infty}kq^k= \frac{q}{p^2}$

$$ E(X)=\frac{q}{p}$$

### story proof
Let $c = E(X)$
$c = 0 \cdot p + (1 + c) \cdot q = q +cq \Rightarrow \frac{q}{p}$

### 장난감 수집가 문제

$n$ 종류의 장난감이 있고, 각 장난감이 나올 확률은 모두 같다.
모든 종류를 모을 때까지 사야하는 장난감의 개수 $T$를 구해보자.

$T = T_1 + T_2 + + \cdots + T_n$
- $T_1$은 첫 번째 새로운 장난감까지 걸린 개수이다.  $\therefore T_1 = 1$
- $T_2$는 두 번째 새로운 장난감까지 추가로 걸린 개수이다.
	- $T_2-1 \sim Geom(\frac{n-1}{n})$ 
	- 기하분포는 0에서 시작하는데 여기서는 최소한 한 개의 새로운 장난감이 있어야 하므로 그 한 개를 빼서 $T_2 - 1$이다.
- 일반화 하면, $T_j-1 \sim Geom(\frac{n-(j-1)}{n})$이다.

$E(T)=E(T_1)+E(T_2)+ \cdots +E(T_n)$
- $E(T_1)=1$
- 1부터 시작하는 기하분포가 있으면 $E(X) = \frac{1}{p}$이다.
- $n$이 충분히 큰 숫자일 때, $\therefore E(T) = 1 + \frac{n}{n-1} + \frac{n}{n-2} + \cdots + \frac{n}{1} = n(1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n}) \approx nlog_{}{n}$
