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
