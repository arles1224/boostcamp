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

$$
E(X) = E(X_1+X_2+ \cdots +X_r)=E(X_1)+ \cdots + E(X_r) = \frac{rq}{p}
$$

## 포아송 분포

포아송 분포의 표기는 $X \sim Pois(\lambda)$ 이다.
 
### 확률질량함수(PMF)

$$
P(X=k) = \frac{e^{- \lambda} \lambda^k}{k!}, \ k \in \{0, 1, 2, \cdots \}, \ \lambda {는}\ {양의} \ {실수인} \ {비율모수이다.}
$$

#### 확률질량함수로 알아보는 포아송 분포의 타당성

$$
\sum_{k=0}^{\infty} \frac{ e^{- \lambda} \lambda^k}{k!} = e^{- \lambda} \sum_{k=0}^{\infty} \frac{\lambda^k}{k!}
$$

위의 식에서 $\sum_{k=0}^{\infty} \frac{\lambda^k}{k!}$은 $e^{\lambda}$의 테일러 급수이므로 $e^{\lambda} = \sum_{k=0}^{\infty} \frac{\lambda^k}{k!}$이다.
따라서,

$$
\sum_{k=0}^{\infty} \frac{ e^{- \lambda} \lambda^k}{k!} = e^{- \lambda} \cdot e^{\lambda} = 1
$$

이므로 포아송 분포는 타당하다.

### 기댓값 $E(X)$

기댓값은 값($k$)과 확률($\frac{e^{- \lambda} \lambda^k}{k!}$)의 곱들의 합이다.

$$
E(X) = e^{-\lambda} \sum_{k=0}^{\infty}k\frac{\lambda^k}{k!} = \lambda e^{-\lambda} \sum_{k=1}^{\infty}\frac{\lambda^{(k-1)}}{(k-1)!}
$$

$\sum_{k=1}^{\infty}\frac{\lambda^{(k-1)}}{(k-1)!}$ 역시 $e^{\lambda}$의 테일러 급수이다.

따라서,

$$
E(X) = {\lambda}e^{-\lambda} \cdot e^{\lambda} = \lambda
$$

### 포아송 분포가 중요한 이유

포아송 분포는 실제 이산형 데이터의 모델로서 가장 많이 그리고 널리 쓰이는 모델이다.
- 적은 성공 확률을 가진 시도를 많은 횟수로 반복 할 때 성공의 수를 셀 때 쓰인다.(counting number of successes where there are a large number of trials, each with small probability of success)
	- 한 시간 동안 받는 이메일의 개수
	- 초코칩 쿠키 안에 들어 있는 초코칩의 수
	- 특정 지역에서 1년간 지진이 발생한 수

### 포아송 패러다임

이론에서의 포아송 분포는 무한대까지 가지만, 실제로 적용하는 포아송 분포는 상한이 있다.

사건 $A_1, A_2, \cdots, A_n$이 있을 때, $P(A_j) = p_j$이고 $n$은 충분히 큰 수라고 하자. $n$이 충분히 큰 수이고 $p_j$는 작은 수라고 하자.
많은 사건이 있기 때문에 특정 결과가 나올 기회는 많지만, 사건 당 그 결과가 나올 확률은 작다.  

이 상태에서 사건들이 서로 독립적이거나 '약하게 의존적'일 때 $A_j$의 실행 횟수가 $Pois(\lambda)$에 근접한다고 할 수 있다.

$\lambda$가 포아송 분포의 기대값이기 때문에 사건 $A_j$가 일어날 것이라 기대되는 수가 된다. 사건이 의존적이어도 선형성에 의해서 $A_j$의 발생횟수의 기댓값은 $p_j$의 합이 된다.

$$
\lambda = \sum_{j=1}^{n}p_j
$$


### 이항 분포의 포아송 분포로의 수렴

이항 분포 $Bin(n,p)$의 $n$이 커지고 $p$가 작아질 때 이항 분포는 포아송 분포로 수렴한다.
이항 분포는 $p$가 모두 같아야 하지만 포아송 분포는 $p$가 달라도 되며, 포아송 분포는 의존성이 조금 허용되는 등, 포아송 분포가 이항 분포보다 더 일반적이다.

$X \sim Bin(n,p)$에서 $n \rightarrow \infty$ 로, $p \rightarrow 0$로 즉, $n$과 $p$를 무한대와 0으로 보낸다.

만약 $Bin(n,p)$가 $Pois(\lambda)$로 수렴한다면, $\lambda = np$일 것이다. $n$과 $p$의 곱이 상수라는 것은 $n \rightarrow \infty$의 속도와 $p \rightarrow 0$의 속도가 같다는 의미이다.

이항분포의 확률질량함수(PMF)인 $P(X=k)=_nC_k p^n (1-p)^{n-k}$는 $k$가 상수라고 했을 때,  $n \rightarrow \infty , \ p \rightarrow 0$의 상황에서 어떻게 될까?

$p = \frac{\lambda}{n}$을 이용해서 식을 $n$에 대한 함수로 바꿔보자.

$$
P(X=k) = \frac{n(n-1)(n-2)\cdots(n-k+1)}{k!}\cdot\frac{\lambda^k}{n^k}\cdot(1-\frac{\lambda}{n})^n\cdot(1-\frac{\lambda}{n})^{-k}
$$

위의 식에서 극한을 계산해보자.

$$
P(X=k) = \frac{\lambda^k}{k!} \cdot e^{-\lambda} \cdot 1 = \frac{e^{-\lambda}{\lambda^k}}{k!} \Leftrightarrow Pois PMF
$$

따라서 $n \rightarrow \infty$, $p \rightarrow 0$일 때 이항 분포는 포아송 분포로 수렴한다.

### 생일 예시

$n$명의 사람이 있을 때 3명의 생일이 같을 확률의 근사값을 구해보자.

$n$명의 사람 집단에서 세 사람을 뽑는 경우의 수는 총 $_nC_3$가지이다.

$X$를 세 사람의 생일이 같을 경우의 수라고 했을 때,
이 세 명 집단 $I_{ijk}$($i < j < k$인 사람 세 명을 뜻한다.)의 생일이 모두 같을 기댓값은 다음과 같다.

$$
E(X) = \begin{pmatrix}n \\\\ 3 \end{pmatrix} (\frac{1}{365})^2
$$

위의 식을 $Pois(\lambda)$에 근사시키면 

$$
\lambda = \begin{pmatrix}n \\\\ 3 \end{pmatrix} (\frac{1}{365})^2
$$

이다.
그리고

$$
P(X \geqq 1) = 1 - P(X=0) \approx 1 - \frac{e^{-\lambda}{\lambda}^0}{0!} = 1 - e^{-\lambda}
$$

이다.

### 받은 이메일 개수 문제

일정 시간 $t$ 동안 받은 이메일의 개수가 $Pois(\lambda t)$로 분포한다. 첫 이메일이 오는 시간을 $T$라고 할 때, $T$의 PDF 를 구해보자. $N_t$는 0에서 $t$까지의 시간 동은 온 메일의 수이다.

> 이 문제는 이산(이메일의 수)과 연속(시간)을 연결한다는 점에서 멋진 문제이다.

$P(T>t) = P(N_t=0)=e^{-\lambda t}\frac{(\lambda^t)^0}{0!}=e^{-\lambda t}$

따라서 $T$ 의 CDF 는 $1-e^{-\lambda t}$이고 PDF 는 CDF 를 미분하면 된다.

$T$의 PDF 는 $\lambda e^{-\lambda t}, \ t > 0$가 된다.
### 포아송 분포의 분산

$X \sim Pois(\lambda)$의 경우에서

$$
E(X^2) = \displaystyle\sum_{k=0}^{\infty}k^2\frac{(e^{-\lambda}\lambda^k)}{k!} = \lambda^2 + \lambda, \ E(X) = \lambda
$$

$\displaystyle\sum_{k=0}^{\infty}\frac{\lambda^k}{k!} = e^{\lambda}$

$\lambda\displaystyle\sum_{k=1}^{\infty}\frac{k\lambda^{k-1}}{k!} = \lambda e^{\lambda}$

$\displaystyle\sum_{k=1}^{\infty} \frac{k\lambda^k}{k!} = \lambda e^{\lambda}$

$\displaystyle\sum_{k=1}^{\infty} \frac{k^2 \lambda^{k-1}}{k!} = \lambda e^{\lambda} + e^{\lambda} = e^{\lambda}(\lambda + 1)$

$E(X^2) = \displaystyle\sum_{k=0}^{\infty}k^2\frac{(e^{-\lambda}\lambda^k)}{k!} = e^{-\lambda}e^{\lambda}\lambda (\lambda+1) = \lambda^2 + \lambda$

따라서,

$$
Var(X) = \lambda
$$

포아송 분포는 기댓값과 분산이 $\lambda$로 동일하다.
