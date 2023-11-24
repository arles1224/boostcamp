# Random Variable
## What is random variable?
Random variable is a _function_ from the sample space. Think as numeric "summary" of an aspect of the event.

A function is deterministic. Then where is randomness coming from?
Randomness is coming from random experiment.
## Definition of Bernoulli Distribution
A random variable $X$ is said to have Bernoulli distribution.

If $X$ has only 2 possible values, 0 and 1, $P(X=1)=p, \ P(X=0) = 1-p$.
'$X = 1$' means an event that $X$ actually takes the value 1.

## Binomial (n, p) Distribution
The distribution of the number of succeses $X$ in $n$ independent Bern(p) trials is called Bin(n,p). 
**KEY ASSUMTION**
1. Trials are independent.
2. Probability of success is all same.
### $X$ ~ $Bin(n,p)$, How to figure out it.
- Story: $X$ is number of successes in $n$ **independent** Bern(p) trial. (p is probability of success)
- Sum of indicator random variable.
	- $X = X_1 + X_2 + \cdots +X_n$
	- $X_j$ is 1 if $n_{th}$ trial is success, otherwise is zero.
- PMF(Probability Mass Function): $P(X=k)= _nC_k \ p^k{(1-p)}^{n-k}$ ($0 \leqq k \leqq n$)
	- descrete case.
	- $P(X=a_j) = p_j , \ (p_j \geqq 0,\ \displaystyle\sum_{j}^{}p_j = 1)$ 
### Sum of the two Binomials
$X$ ~ $(n,\ p)$ 

$Y$ ~ $(m, \ p)$

$X$ and $Y$ is independent.

$X + Y$ ~ $(m+n, \ p)$
1. $X = X_1 + \cdots + X_n, \ Y = Y_1 + \cdots + Y_m \Rightarrow X + Y = \sum_{j=1}^{n}X_j + \sum_{i=1}^{m}Y_i$
   
   Sum of $n + m$ i.i.d.(idepentent and identical distribution) Bern(p) $\Rightarrow Bin(n+m, p)$
2. $P(X+Y=k)= \sum_{j=0}^{k} P(X+Y=k|X=j)\cdot P(X=j)$
   
   $= \sum_{j=0}^{k}P(Y=k-j|X=j)\cdot _nC_jp^jq^{n-j}$
   
   $=\sum_{j=0}^{k} \ _mC_{k-j}p^{k-j}q^{m-k+j} \cdot _nC_jp^jq^{n-j}$
   
   $=p^kq^{m+n-k} \cdot _{m+n}C_k$

### $n-X$의 분포 찾기

$X \sim Bin(n,p)$ 일 때, $n-X$의 분포 찾기.

$P(n-X=k)=P(X=n-k)=_nC_{n-k}p^{n-k}q^k = _nC_kq^kp^{n-k}$

따라서, $n-X \sim Bin(n,q)$이다.


## CDF(누적분포함수)
### CDF
- CDF는 이산확률변수(discrete random variable)와 연속확률변수(continuous random variable) 모두에 성립한다.
- CDF: $F(x) = P(X \leqq x),\ x \in \mathbb{R}$
- 이산확률변수의 누적분포함수 그래프


  ![그래프](https://github.com/arles1224/boostcamp/blob/main/Statistics%20110/images/9-1.png)
  > 출처: [네이버 부스트코스](https://www.boostcourse.org/ai152/lecture/30901?isDesc=false)

- 누적분포함수를 사용해 원하는 확률 구하기
	- 예시
	
	  $P(1 < X \leqq 3) = F(3) - F(1)$
- 누적분포함수의 특징
	1. 감소하지 않고 증가만 한다.
	2. 우측에서 접근하는 극한 일때 항상 연속적인 우연속 함수이다.(좌연속은 해당하지 않는다.)
	3. 음의 무한대로 가면 0에, 양의 무한대로 가면 1에 수렴한다.

## Independence of Random Variables
X, Y are independent random variables if
$P(X \leqq x, \ Y \leqq y) = P(X \leqq x)\cdot P(Y \leqq y)$ for all x, y.

- Descrete case:
  
  $P(X=x, Y=y) = P(X=x) \cdot P(Y=y)$

## 확률변수의 독립

확률변수 $X_1, \cdots, X_n$가 독립이면 **모든** $x_1, \cdots x_n$에 대해,

$$
P(X_1 \leqq x_1, \cdots , X_n \leqq x_n) = P(X_1 \leqq x_1)\cdots P(X_n \leqq x_n)
$$

이다.

### 이산분포의 경우

$$
P(X_1=x_1, \cdots , X_n=x_n) = P(X_1=x_1) \cdots P(X_n=x_n)
$$
### Example where pair wise independence doesn't imply independence

$X_1, X_2 \sim Bern(\frac{1}{2})$. $X_1$과 $X_2$를 동전 던지기라고 하자. 

동전을 두 번 던져서 같은 면이 나오면 한 사람이 나오고, 아니면 다른 사람이 이기는 게임을 한다고 하면, 두 개가 같은지 다른지 확인하는 확률변수 $X_3$가 필요하다. $X_1 = X_2$ 이면 $X_3 = 1$이고, 아니면 $X_3 = 0$이다.

$X_1$과 $X_2$는 pair wise independence 이지만 독립은 아니다. $X_1$과 $X_2$를 알면 $X_3$을 알 수 있기 때문이다. 같은 방식으로 $X_2$와 $X_3$도 쌍으로는 독립이지만 완전한 독립은 아니다.
