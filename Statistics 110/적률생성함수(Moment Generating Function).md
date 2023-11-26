# 적률생성함수

PDF(확률 밀도 함수)나 CDF(누적 분포 함수)처럼 분포를 설명하는 방법 중 하나이다.

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

## 베르누이 분포와 이항분포의 MGF

$X \sim Bern(p)$라면 MGF $M(t)=E(e^{tX})$이고 $X$는 0 혹은 1이기 때문에 $e^{tX}$는 $e^t$이거나 1이다.

따라서 $X\sim Bern(p) \Rightarrow M(t)=pe^t+q\cdot 1$이다. ($q=1-p$)

위의 식으로 이항분포의 MGF 또한 구할 수 있다.

$X\sim Bin(n,p) \Rightarrow M(t)= (pe^t+q)^n$

## 정규분포의 MGF

$$
Z \sim N(0,1) \Rightarrow M(t)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{tZ-\frac{Z^2}{2}}dz = \frac{e^{\frac{t^2}{2}}}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{-\frac{1}{2}(z-t)^2}dz=e^{\frac{t^2}{2}}
$$



