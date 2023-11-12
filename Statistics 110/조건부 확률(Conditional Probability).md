# 조건부 확률
How should you upadte probability/beliefs/uncentainty based on new evidence.

## Theorem
1. $P(A \cap B) = P(B)P(A|B) = P(A)P(B|A)$
2. $P(A_1, \cdots, A_n) = P(A_1)P(A_2|A_1)p(A_3|A_1,A_2) \cdots P(A_n|A_1, \cdots A_{n-1})$
3. Bayes' Rule: $P(A|B)= \frac{P(B|A)P(A)}{P(B)}$
## 정의
$P(A|B)=\frac{P(A \cap B)}{P(B)}\;{if},\,P(B) > 0$: probability of A occurs given the B occurs. 

### Intuition 1: Pebble World

There are 9 pebbles whose total mass eqals 1.
$A=\{{pebble}_4, {pebble}_5, {pebble}_6, {pebble}_7\}$
$B=\{{pebble}_1, {pebble}_2, {pebble}_3, {pebble}_4\}$ 

In case of $P(A|B)$, the only part of matter is $A \cap B = \{ {pebble}_4\}$, and pebbles inside $P(B^c)$ are removed. Then, a problem occurs that total mass not equal to 1. So, we divide by $P(B)$ to make total mass 1. This is called _renormalize_.

### Intuition 2: Frequentist World: repeat experiment many times
Circle reps where B occured. Among those, what fraction of time A also occur?
