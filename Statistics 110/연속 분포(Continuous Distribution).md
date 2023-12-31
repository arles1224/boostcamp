# 연속 분포

## 이산 분포 VS 연속 분포

|이산분포|연속분포|
|:---:|:---:|
|PMF(확률질량함수) $P(X=x)$|PDF(확률밀도함수)$f_X(x)$ <br>($P(X=x)=0$)|
|CDF(누적분포함수) $F_X(x)=P(X \leqq x)$|CDF(누적분포함수) $F_X(x)=P(X \leqq x)$|
|$E(X)= \sum_{}{}xP(X=x)$|$E(X)=\int_{-\infty}^{\infty}{f_X(x)dx}$|
|$Var(X) = E(X^2) - \{E(X)\}^2$|$Var(X) = E(X^2) - \{E(X)\}^2$|


> **확률밀도함수에서 특정 값에 대한 확률이 0인 이유**
> 연속분포에서는 확률변수가 어떤 실수 범위를 가질 때, 그 안에 무한한 실수가 존재한다.   
> 따라서 어떤 특정 값에 대한 확률은 0이 된다. 이런 이유로 연속 분포에서는 PMF 대신 PDF 를 사용한다.


## 확률밀도함수(Probability 'Density' Function)

### 정의

확률 변수 $X$의 확률밀도함수 $f(x)$라고 하면, $P(a \leqq X \leqq b) = \int_{b}^{a}{f(x)dx}$이다.  
확률밀도함수가 유효하기 위해서는 $f(x) \geqq 0$이고, $\int_{-\infty}^{\infty}{f(x)dx} = 1$이여야 한다.

$f(x)$는 확률이 아니라 확률밀도이다. 이것을 어떻게 확률 차원으로 바꿀 수 있을까?
0보다 큰 매우 작은 수 $\epsilon$이 있을 때,

$$
f(x_0)\cdot \epsilon \approx P(X \in (x_0 - \frac{\epsilon}{2}, x_0+\frac{\epsilon}{2}))
$$

즉 $f(x_0) \cdot \epsilon$, 확률 밀도와 그 범위의 곱은 $X$가 $\epsilon$ 크기의 범위에 위치할 확률로 근사한다.

### 누적분포함수(CDF)

연속확률변수 $X$의 확률밀도함수가 $f$일 때, 누적분포함수(CDF) $F(X)$는  

$$
F(x) = P(X \leqq x) = \int_{-\infty}^{x}{f(t)dt}
$$
이다.  


반대로 연속확률변수 $X$의 누적분포함수 $F(X)$가 주어졌을 때 $X$의 PDF 는

$$
f(x)=F'(X)
$$

이다.

$$
P(a \leqq X \leqq b) = \int_{a}^{b}{f(t)dt} = F(b) - F(a)
$$

또한, $P(a < X < b)$에서 이산 분포일 경우엔 $a$와 $b$가 범위에 포함되는 지가 중요했지만, 연속분포에서는 포함을 시키거나 안 시켜도 같은 결과 값을 갖는다.

$$
{연속확률분포에서},\ P(a < X < b) = P(a \leqq X \leqq b )
$$

## 연속분포의 종류

### 균등분포(Uniform Distribution)

$$Unif(a,b)$$
균등 분포는 특정 범위가 뽑힐 확률이 그 범위의 크기에 비례하는 연속 분포이다.

$a$와 $b$사이에서 완전히 무작위로 한 점을 뽑는다. 
완전히 무작위로 한점을 뽑는다는 것은  $a$와 $b$의 중점을 기준으로 앞에 반이 뽑힐 확률과 뒤의 반이 뽑힐 확률이 같다는 즉, 어느 한 쪽으로 치중되지 않았다는 뜻이다.

이 때 어떤 특정 수가 뽑힐 확률이 0이다.

#### PDF(확률밀도함수)

$$
f(x) = \begin{cases}
c, \ if \ a \leqq x \leqq b\\
0, \ otherwise
\end{cases}
\Rightarrow 1 = \int_{a}^{b}{c\ dx}
\Rightarrow c = \frac{1}{b-a}
$$


균등 분포는 확률이 어느 한 쪽으로 치우치지 않은 균등한 분포이다. 따라서 범위 안에서는 확률밀도가 같아야 한다.

#### CDF(누적분포함수)

$$
F(x) = \int_{a}^{x}{f(t)dt}=
\begin{cases}
0 \ (x < a) \\
\frac{\displaystyle x-a}{\displaystyle b-a} \ (a \leqq x \leqq b)\\
1 \ (x > b) 
\end{cases}
$$

#### 기댓값 $E(X)$

$$
E(X) = \int_{a}^{b} \frac{x}{b-a}dx \\
= \left[ \frac{x^2}{2(b-a)}\right]_a^b = \frac{1}{2(b-a)}(b+a)(b-a) \\
= \frac{a+b}{2}
$$

균등분포는 말 그대로 균등분포이기 때문에 평균이 그 중간값이다.

#### 분산(Variance)

LOTUS 에 의해서 $E(X^2)$은 

$$
E(X^2) = E(Y) = \int_{-\infty}^{\infty}{x^2f_X(x)dx}
$$

이다.  

##### 모수가 (0, 1)인 경우

균등분포 $U \sim Unif(0,1)$에서 $E(U) = \frac{1}{2}$이고 $E(U^2)=\int_{0}^{1}{u^2\cdot f_U(u)du}$이다.  

$f_U(u) = \frac{1}{1-0} = 1$이므로 $E(U^2)=\frac{1}{3}$이다.

따라서 $V(U) = \frac{1}{12}$이다.

#### 균등분포의 대칭성

$U \sim Unif(0,1)$일 때, $1-U \sim Unif(0,1)$이다.

#### 균등분포의 보편성

$(x_0, \frac{1}{3}),\ (1,1)$을 지나고, $x \geqq 1$일 때 $y=1$인 $x \geqq 0$에서 정의된 함수 $y=F(x)$가 있다고 하자.
$X \sim F$에 대해서 $P(F(X) \leqq \frac{1}{3})$은 얼마일까?

$P(F(X) \leqq \frac{1}{3}) = P(X \leqq x_0)$이고, 누적분포함수의 정의에 따라 $P(X \leqq x_0) = F(x_0) = \frac{1}{3}$이다.

균등분포는 확률이 길이와 비례하는 확률이고, $F(X)$는 $(0,1)$에서는 확률이 길이와 같기 때문에 균등분포를 따른다.

### 지수분포(Exponential Distribution)

$\lambda$라고 부르는 비율 모수(rate parameter)가 있다. $\lambda$는 특정한 사건이 발생할 비율을 의미하기 때문에 비율 모수라고 부른다.

$$
X \sim Expo(\lambda)
$$

#### PDF(확률밀도함수)

$$
\lambda e^{-\lambda x}, \ x > 0 \ (0 \ otherwise)
$$

#### CDF(누적분포함수)

$$
F(x) = \int_{0}^{x}{\lambda e^{-\lambda t}dt} = 1-e^{-\lambda x}, \ x > 0
$$

#### $E(X)$와 $E(Y)$

$Y = \lambda X$라고 하면, $Y \sim Expo(1)$이다.


$Y$의 CDF 는 다음과 같다.

$$
P(Y \leqq y) = P(X \leqq \frac{y}{\lambda}) = 1 - e^{-y}
$$

$Y \sim Expo(1)$일 때의 $E(Y)$와 $Var(Y)$

$$
E(Y) = \int_{0}^{\infty}{ye^{-y}dy} = 1
$$

$$
Var(Y) = E(Y^2) - \{E(Y)\}^2 = \int_{0}^{\infty}{y^2e^{-y}dy} - 1 = 1
$$

따라서,

$$
E(X) = \frac{1}{\lambda}, \ Var(X) = \frac{1}{\lambda^2}
$$

이다.

#### 무기억성

지수분포는 연속확률 분포 중에 유일하게 무기억성을 가지는 분포이기 때문에 중요하다. 이산확률 분표중에는 기하분포가 무기억성을 가진다. 기하분포는 지수분포의 이산 유사 형태이고, 지수분포는 기하분포의 연속 유사 형태이다. 기하분포와 지수분포는 밀접하게 관련되어있다.
무기억성이란 얼마나 오래 기다리건 간에 새로 시작하는 것과 같다는 의미이다.

예를 들어, 전화를 기다린다고 하고 현재 시간은 $t_0$라고 하자. 얼마나 오래 기다리든 기다린 시간은 고려하지 않는다. 즉, 전화가 오는 사건으로 향하는 과정이라 볼 수 없다. 매 시간 새롭게 시작하는 것이다.

이것이 무기억성이다.

$$
P(X \geqq s+t \vert X \geqq s)=P(X \geqq t)
$$

예를 들어 사람의 수평이 무기억성이고 평균 수명이 80세라면, 얼마나 오래 살았던지간에 무기억성에 의해 매번 새롭게 시작하기 때문에 추가로 평균 80년을 더 살 수 있다. 만약 $T$가 얼마나 오래 살지를 나타낸다면, $E(T|T>20) = 20 + E(T)$ 이다. 

#### 무기억성이 지수분포에만 성립한다는 증명

0부터 $\infty$까지의 값을 갖는 양의 연속확률변수 $X$가 무기억성을 가진다면, $X$는 **반드시** 지수분포($X \sim Expo(\lambda)$)이다.

$F$를 $X$의 누적분포함수(CDF)라고 할 때,

$$
G(x) = P(X>x) = 1 - F(x)
$$

이고, 무기억성에 의해서

$$
G(s+t) = G(s)G(t)
$$

이다.

$s=t$이면 $G(2t)=G(t)^2$이고, $s=2t$이면 $G(3t)=G(2t)G(t)=G(t)^3$이다.

따라서 $G(kt)=G(t)^k$이다.

또한, $G(\frac{t}{2}) = G(t)^{\frac{1}{2}}, \ G(\frac{t}{3}) = G(t)^{\frac{1}{3}} \Rightarrow G(\frac{t}{k}) = G(t)^{\frac{1}{k}}$이다.

위의 두 성질을 합하면 $k$가 양의 유리수일 때도 성립함을 알 수 있으며, 양의 유리수에 극한을 씌워 모든 양의 실수에도 성립함을 알 수 있다.

따라서,

$$
G(xt) = G(t)^x, \ x > 0, x \in \mathbb{R}
$$

이고,

$t=1$일 때, $G(x) = G(1)^x = e^{x \cdot ln(G(1))}$인데 $G(1)$은 확률이므로 $ln(G(1))$은 어떤 음의 실수이며 이것을 $-\lambda$라고 놓을 수 있다. 그러면 $G(x) = e^{-x\lambda}$이며 이것은 1에 지수분포의 CDF를 뺀 것이다.
