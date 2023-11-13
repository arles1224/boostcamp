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

### Intuition 2: Medical Context
Patient gets tested for disease afflicts 1% of population, tests positive. Suppose test's advertised as "95% accurate".
$D$ : patient has disease
$T$: patient tests positive
$P(T|D) = 0.95 = P(T^c|D^c)$
$P(D|T) =\frac{P(T|D)P(D)}{P(T)} = \frac{P(T|D)P(D)}{P(T|D)P(D)+P(T|D^c)P(D^c)}=\frac{0.95 \times 0.01}{0.95 \times 0.01 + 0.05 \times 0.99} \approx 0.16$

## Monty Hall
There are three doors, door 1, door 2, door 3. One door has a car, the other two doors have goats. Monty knows which one has car. If you pick the door, then Monty always opens up the other door to reveal a goat. If he has a choice, he picks with equal probability. Should you switch?
Note: If Monty opens door 2, we know door 2 has a goat, **and** Monty opened door 2.

### Law of Total Probability: wish we knew where a car is.
Assuming we intially pick door 1.
$S$: succeed(assuming switch)
$D_j$: Door $j$ has a car($j \in \{1, 2, 3\})$
$P(S)=\frac{P(S|D_1)}{3}+\frac{P(S|D_2)}{3}+\frac{P(S|D_3)}{3} = 0+ (1\times\frac{1}{3})+ (1 \times \frac{1}{3}) = \frac{2}{3}$
By symmetry, $P(S|Monty\,opens\,door 2)=\frac{2}{3}$

## Simpson's Paradox: Difference within conditional and unconditional
The weights' change occurs Simpson's Paradox 
Hibbert

| |Heart|Bandage remove|
|---|---|---|
|**success**|70|10|
|**failure**|20|0|
-> Total success rate: 80%

Nick

| |Heart|Bandage remove|
|---|---|---|
|**success**|2|81|
|**failure**|8|9|
-> Total success rate: 83%

**Conditionally**, Dr. Hiddert is better then Dr. Nick for each surgery. **Unconditionally** Dr.Nick has better then Dr. Hibbert(3%). It is very easy for Dr. Nick to get high success rate because he is doing easier surgery.

$A$: successful surgery
$B$: treated by Dr. Nick
$C$: heart surgery <- Confounder(교란요인)
$P(A|B,C) < P(A|B^c,C)$
$P(A|B,C^c) < P(A|B^c,C^c)$
$P(A|B) > P(A|B^c)$

## Thinking Condotionally
### Gambler's Ruin
- Two gamblers, $A$ and $B$
- Sequence of rounds bet 1$
- $p=P(A \, wins\, a\, certain\, round), \, q=1-p$
- Find probability that $A$ wins entire game(so $B$ is "ruined").
- Assuming $A$ starts with $ $i$, $B$ starts with $ $(N-i)$ 