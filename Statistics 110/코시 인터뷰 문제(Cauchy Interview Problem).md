# 코시 분포(Cauchy Distribution)

$X$ 와 $Y$ 가 독립이고 같은 표준정규분포를 따를 때 $T=\frac{X}{Y}$ 이다.

코시 분포는 기댓값이 발산한다.

## 누적분포함수(CDF)

$$
P(\frac{X}{Y} \leqq t)=P(\frac{X}{|Y|} \leqq t)=P(X \leqq t|Y|)
$$

$$
P(X \leqq t|Y|)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{\frac{-y^2}{2}}\int_{-\infty}^{t|y|} \frac{1}{\sqrt{2\pi}}e^{\frac{-x^2}{2}}dxdy=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{\frac{-y^2}{2}}\Phi(t|y|)dy
$$

$$
= \sqrt{\frac{2}{\pi}}\int_{0}^{\infty}e^{\frac{-y^2}{2}}\Phi(ty)dy
$$

## 확률질량함수(PDF)

$$
\sqrt{\frac{2}{\pi}}\int_{0}^{\infty}ye^{\frac{-y^2}{2}}\frac{1}{\sqrt{2\pi}}e^{\frac{-t^2y^2}{2}}dy = \frac{1}{\pi}\int_{0}^{\infty}ye^{\frac{-(1+t^2)y^2}{2}}=\frac{1}{\pi(1+t^2)}
$$


