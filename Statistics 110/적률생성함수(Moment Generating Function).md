# 적률생성함수

PDF(확률 밀도 함수)나 CDF(누적 분포 함수)처럼 분포를 설명하는 방법 중 하나이다.
적률(moment)은 물리학의 관성 모멘트라는 단어에서 유래했다.

## 정의

확률변수 $X$의 MGF는

$$
M(t) = E(e^{tX})
$$

이다.

### 적률 생성 함수라고 부르는 이유(feat. 테일러 급수)

$E(e^{tX})=E(\sum_{n=0}^{\infty}\frac{X^nt^n}{n!})=\sum_{n=0}^{\infty}\frac{E(X^n)t^n}{n!}$이고, $E(X^n)$을 $n$차 적률이라고 한다.

$x$의 모든 차수의 적률들을 테일러 급수에 넣었기 때문에 적률생성함수라고 부른다.

### MGF 가 중요한 이유

1. $n$차 적률 $E(X^n)$은 테일러 급수에서 $\frac{t^n}{n!}$의 계수이다.
	- $n$차 적률 $E(X^n)$을 구하고 싶다면 0을 대입한 MGF를 $n$번 미분하면 된다. $M^{(n)}(0) = E(X^n)$
	- 따라서 MGF 를 한 번 미분하면 평균을, 두 번 미분하면 $E(X^2)$이 나오며 이를 통해 분산을 알 수 있다.
1. MGF 가 분포를 결정한다.
	- 만약 확률변수 $X$와 $Y$가 같은 MGF 를 가지면 같은 분포를 가진다.
2. 만약 $X$의 MGF 인 $M_X$ 와 $Y$의 MGF 인 $M_Y$가 서로 독립이면, $X+Y$ 의 MGF 는 $E(e^{t(X+Y)})=E(e^{tX})E(e^{tY})=M_X(t)M_Y(t)$이다. $X$와 $Y$가 독립일 때만 성립한다.

## 확률분포의 적률과 MGF

### 베르누이 분포와 이항분포의 MGF

$X \sim Bern(p)$라면 MGF $M(t)=E(e^{tX})$이고 $X$는 0 혹은 1이기 때문에 $e^{tX}$는 $e^t$이거나 1이다.

따라서 $X\sim Bern(p) \Rightarrow M(t)=pe^t+q\cdot 1$이다. ($q=1-p$)

위의 식으로 이항분포의 MGF 또한 구할 수 있다.

$X\sim Bin(n,p) \Rightarrow M(t)= (pe^t+q)^n$

### 표준정규분포의 MGF와 적률

표준정규분포의 MGF 는 다음과 같다.

$$
Z \sim N(0,1) \Rightarrow M(t)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{tZ-\frac{Z^2}{2}}dz = \frac{e^{\frac{t^2}{2}}}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{-\frac{1}{2}(z-t)^2}dz=e^{\frac{t^2}{2}}
$$

표준정규분포의 홀수차 적률은 대칭성에 의해,

$$
E(Z^n) = 0 \ for \ n \ is \ odd
$$

이다.

짝수차($2n$) 적률은 적분을 해서 구하는 것은 힘들기 때문에 MGF 를 통해서 구한다.

$e$의 테일러 급수는 언제나 유효하기 때문에 미분을 하지 않고 바로 테일러 급수를 적을 수 있다.

$$
M(t)=e^{\frac{t^2}{2}}=\sum_{n=0}^{\infty}\frac{(\frac{t^2}{n})^n}{n!}=\sum_{n=0}^{\infty}\frac{t^{2n}}{2^nn!}=\sum_{n=0}^{\infty}\frac{(2n)!}{2^nn!}\cdot\frac{t^{2n}}{(2n)!}
$$
따라서

$$
E(Z^{2n})=\frac{(2n)!}{2^nn!}
$$

이고, 다음과 같은 규칙성을 보인다.

$$
\begin{cases}
n=1, \ E(Z^2) = 1 \\\\
n=2, \ E(Z^4) = 1 \times 3 \\\\
n=3, \ E(Z^6) = 1 \times 3 \times 5
\end{cases}
$$


### 지수분포의 MGF 와 적률

$X \sim Expo(1)$의 경우에 MGF 와 적률을 구하고 싶다고 해보자.

LOTUS 에 의해, 

$$
M(t)=E(e^{tx}) = \int_{0}^{\infty}e^{tX}e^{-X}dX=\int_{0}^{\infty}e^{-X(1-t)}dX=\frac{1}{1-t}\ (t < 1)
$$

$M'(0)=E(X), \ M''(0)=E(X^2), \cdots$이고 $\frac{1}{1-t}$는 기하급수와 관련이 있다.

$$
when \ |t|<1, \ \frac{1}{1-t}=\sum_{n=0}^{\infty}t^n=\sum_{n=0}^{\infty}n!\frac{t^n}{n!}
$$

$n$차 적률 $E(X^n)$은 $\frac{t^n}{n!}$의 계수이므로 $E(X^n)=n!$이다. 여러번 미분 할 필요 이런 식으로 없이 적률을 구할 수 있다.

따라서, $X \sim Expo(1)$의 MGF 와 적률은

$$
MGF = \frac{1}{1-t} \ (t<1), \ E(X^n)=n!
$$

이다.

그렇다면 $Y \sim Expo(\lambda)$ 일 때 $X=\lambda Y \sim Expo(1)$이다.

$E(Y)=\frac{1}{\lambda}$이고 $E(X)=1$이기 때문에 $X=\lambda Y$이다. 그렇다면 $Y^n = (\frac{X}{\lambda})^n$이기 때문에 $Y^n$의 적률을 구할 수 있다.

$$
E(Y^n)= \frac{{\lambda}^n}{n!}
$$

### 포아송 분포의 MGF 와 적률

$X \sim Pois(\lambda)$일 때 LOTUS 에 의하여 포아송 분포의 MGF 는 다음과 같다.


$$
M(t) = E(e^{tX})=\sum_{k=0}^{\infty}e^{tk}\frac{e^{-\lambda}\lambda^k}{k!}=e^{-\lambda}\sum_{k=0}^{\infty}\frac{{(\lambda e^t)}^k}{k!}=e^{-\lambda}e^{\lambda e^t}=e^{\lambda(e^t-1)}
$$

포아송 분포 $Y \sim Pois(\mu)$ 가 추가로 있고, $X$와 $Y$는 독립적이라고 할 때, $X+Y$ 의 분포를 구해보자.

$X+Y$ 의 MGF 는 $E(e^{t(X+Y)})=E(e^{tX})E(e^{tY})=M_X(t)M_Y(t)$ 이다.

$M_X(t)=e^{\lambda(e^t-1)}$ 이고, $M_Y(t)=e^{\mu(e^t-1)}$ 이다. 따라서, $M_X(t)M_Y(t)=e^{{(\lambda + \mu)(e^t-1)}}$ 이다.

즉, $X+Y \sim Pois(\lambda + \mu)$ 이다.