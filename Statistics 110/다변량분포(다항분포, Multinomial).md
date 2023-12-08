# 다변량분포(다항분포)

다항분포는 두 개 이상의 확률변수가 포함된 결합분포함수이다. 앞서 배운 포아송분포, 기하분포 등 확률변수가 한 개만 있는 분포는 일변량분포라고 부른다.

다변량분포는 이항분포(Binomial)가 이항에서 다항으로 일반화된 것이다.

## 다항분포의 정의

$\vec{X} \sim Mult(n,\vec{p})$ 로 표기한다. 

$\vec{p}=(p_1, \cdots, p_k)$ 이고 확률벡터이다.($p_i \geqq 0 \ and \sum_{i=1}^{}p_i=1$)

$\vec{X}=(X_1, \cdots, X_k)$ 이다.

이항분포에서는 사건을 2가지(e.g. 성공, 실패)로 분류했지만, 다항분포에서는 2가지 이상의 사건으로 분류할 수 있다. 또한, 이항분포에서는 $n$ 개의 독립적인 시행이 있었듯이, 다항분포에는 독립적으로 $k$ 개의 분류(사건)로 나눌 수 있는  $n$ 개의 object 가 있다.

$$
p_j=P(category \ j),X_j = \#objects \ in \ category \ j
$$

## 결합 확률질량함수(Joint PMF)

$$
P(X=n_1, \cdots, X_k=n_k) = \frac{n!}{n_1!n_2!\cdots n_k!}p_1^{n1}\cdots p_k^{n_k} \ (n=n_1+n_2+\cdots+n_k)
$$

## 주변분포(Marginal Distribution)

$\vec{X} \sim Mult(n,\vec{p})$ 에서 $\vec{X}$ 의 한 원소인 $X_j$ 의 주변분포는 $X_j \sim Bin(n,p_j)$ 이다.

따라서 $E(X_j)=np_j, \ Var(x_j)=np_j(1-p_j)$  이다.

## Lumping property

$\vec{X}=(X_1, \cdots, X_{10}) \sim Mult(n, (p_1, \cdots, p_{10}))$ 일 때, 예를 들면 10개의 정당이 있고 그중 $n$ 명의 사람을 고른다고 하자. 그러면 $X_j$ 는 $j$ 번째 정당에 속해있는 인원 수가 되고 $p_j$ 는 $j$ 번째 정당에 속할 확률이다.

이때  $X_1,X_2$ 가 주력정당이고 나머지는 비주류 정당이라고 하면, 비주류 정당을 한 덩어리로 묶어서 생각할 수 있다.

$$
\vec{Y}=(X_1,X_2, X_3 + \cdots + X_{10}), \ \vec{Y} \sim Mult_3(n,(p_1,p_2,p_3+\cdots+p_{10}))
$$

## 조건분포(Conditional Distribution)

$\vec{X} \sim Mult(n,\vec{p})$ 이고 $X_1=n_1$ 이 주어졌을 때, 

$(X_2,\cdots,X_k) \sim Mult_{k-1}(n-n_1,(p_2',\cdots,p_k'))$ 이다. $p_2+\cdots p_k \neq 1$ 이므로 $p_j'$ 으로 설정하고 어떤 값인지 구해야 한다.

$p_2'=P(being \ in \ category \ 2|not \ in \ category \ 1) = \frac{p_2}{1-p_1}$ 이라고 할 수 있다.

따라서, $p_j' = \frac{p_j}{p_2+\cdots+p_k}$ 이다.