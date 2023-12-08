# 정규분포

가우시안 분포라고도 부른다.
정규분포는 평균과 분산, 총 두 개의 모수를 가진다.

## 중심극한정리

독립적이고 동일한 많은 확률 변수의 합은 정규분포에 근접한다.

## 표준정규분포
### 표준정규분포의 표기

$$
Z \sim N(0,1)
$$

$N(0,1)$은 평균이 0이고 분산이 1이라는 의미이다.

또한, 대칭성에 의해 $-Z \sim N(0,1)$이다.

### 확률밀도함수(PDF)

$$
f(z) = ce^{\frac{-z^2}{2}}
$$

$c$는 정규화 상수로, 그래프 아래 넓이가 1이 되도록 맞춰준다.

$$
\int_{-\infty}^{\infty}{e^{\frac{-z^2}{2}}dz} \int_{-\infty}^{\infty}{e^{\frac{-z^2}{2}}dz} =  \int_{-\infty}^{\infty}{e^{\frac{-x^2}{2}}dx} \int_{-\infty}^{\infty}{e^{\frac{-y^2}{2}}dy} = \int_{-\infty}^{\infty}\int_{-\infty}^{\infty}{e^{\frac{-(x^2+y^2)}{2}}dxdy}
$$

$$
\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}{e^{\frac{-(x^2+y^2)}{2}}dxdy} = \int_{0}^{2\pi} \int_{0}^{\infty} {e^{\frac{-r^2}{2}}r \ drd\theta} = \int_{0}^{2\pi} \left( \int_{0}^{\infty} e^{-u}du \right)d\theta = 2\pi
$$

$$
\therefore \int_{-\infty}^{\infty}{e^{\frac{-z^2}{2}}dz} = \sqrt{2\pi}, c = \frac{1}{\sqrt{2\pi}}
$$

### 누적분포함수(CDF)

$$
\Phi(Z) = \frac{1}{\sqrt{2\pi}}\int_{-\infty}^{z}e^{\frac{-t^2}{2}}dt
$$ 
$\Phi(-Z) = 1 - \Phi(Z)$

### 평균 $E(Z) = 0$

$Z \sim N(0,1)$일 때, 대칭성에 의해서(기함수)

$$
E(Z) = \frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty} ze^{\frac{-z^2}{2}}dz = 0
$$

이다.

### 분산 $Var(Z) = 1$

$Var(Z) = E(Z^2) - \{E(Z)\}^2 = 1 - 0 = 1$


## 일반정규분포

$X = \mu + \sigma Z,\ \mu \in \mathbb{R}, \ \sigma > 0$

$\mu$는 평균 혹은 위치라고 한다. 밀도를 바꾸지 않고 $\mu$를 더해 위치를 좌우로 이동한다는 뜻이다.

$\sigma$는 표준편차(분산의 제곱근)이며, 척도라고도 불린다. 상수 $\sigma$를 곱함으로서 전체 크기를 조절하기 때문이다. 밀도함수의 모양이 얼마나 넓거나 좁은지에 영향을 미친다. 이 경우에도 PDF 의 적분값은 1이다.

### 일반정규분포의 표기

$$
X \sim N(\mu,\sigma^2)
$$

### 기댓값 $E(X)$

$$
E(X) = \mu
$$

대칭성에 의해 $E(X) = E(\mu + \sigma Z) = \mu + \sigma \times 0$이다.

### 분산 $Var(X)$


$$
Var(X) = \sigma^2
$$

$Var(X) = Var(\mu + \sigma Z) = \sigma^2 \times 1$

### 표준화

$$
Z = \frac{X-\mu}{\sigma}
$$

평균을 빼고 표준편차로 나눈다!

### 누적분포함수(CDF)

$$
\Phi(\frac{X-\mu}{\sigma})
$$

$P(X \leqq x) = P(\frac{X-\mu}{\sigma} \leqq \frac{x-\mu}{\sigma}) = P(Z \leqq \frac{x-\mu}{\sigma}) = \Phi(\frac{X-\mu}{\sigma})$

### 확률밀도함수(PDF)

$$
\frac{1}{\sigma \sqrt{2\pi}}e^{-\frac{(\frac{X-\mu}{\sigma})^2}{2}}
$$

### 68-95-99.7% 규칙

$P(\vert X-\mu \vert \leqq \sigma) \approx 0.68$

$P(\vert X-\mu \vert \leqq 2\sigma) \approx 0.95$

$P(\vert X-\mu \vert \leqq 3\sigma) \approx 0.997$

## 정규분포의 합에 대한 정리

### 정리

**서로 독립**이고 정규 분포를 따르는 확률변수 $X \sim N(\mu_1, \sigma_1^2)$ 과 $Y \sim N(\mu_2, \sigma_2^2)$ 가 있다.

선형성에 의해 이 둘의 합은 $X+Y \sim (\mu_1+\mu_2, \ \sigma_1^2+\sigma_2^2)$ 이다.

### 증명

적률생성함수를 이용해 증명한다. $X$ 와 $Y$ 가 독립이므로 $X$ 의 적률생성함수와 $Y$ 의 적률생성함수의 곱은 $X+Y$ 의 적률생성함수이다.

$X$ 의 적률생성함수는 $e^{\mu_1t + \frac{1}{2}\sigma_1^2t^2}$ 이다.

$Y$ 의 적률생성함수는 $e^{\mu_2t + \frac{1}{2}\sigma_2^2t^2}$ 이다.

따라서 $X+Y$ 의 적률생성함수는

$$
e^{(\mu_1 + \mu_2)t + \frac{t^2}{2}(\sigma_1^2+\sigma_2^2)}
$$

이고, 이것은 $N(\mu_1 + \mu_2, \ \sigma_1^2+\sigma_2^2)$ 의 적률생성함수이다.



