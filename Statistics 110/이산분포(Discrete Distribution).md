# Discrete Distribution

## 음이항분포(Negative Binomial)
음수도 아니고 이항도 아니다. 기하분포의 일반화이다.
$r, p$ 두 개의 파라미터를 갖는다.
### Story #1
독립적인 16번의 Bern(p) 시행이 있을 때 5번($r$)째 성공 전에 11번($n$)의 실패가 있는 경우.
시행은 성공(1)으로 끝날 것이며, 그 앞의 결과들은 어떠한 순서로도 있을 수 있다.
#### PMF
$P(X=n) = _{n+r-1}C_{r-1} p^r(1-p)^n$

#### $E(X)$
$X_j$ 는 $j-1$ 번째 성공과 $j$ 번째 성공 사이의 실패 횟수이다. 따라서 $X_j \sim Geom(p)$이고 독립적이다.
$$E(X) = E(X_1+X_2+ \cdots +X_r)=E(X_1)+ \cdots + E(X_r) = \frac{rq}{p}$$
### Story #2

