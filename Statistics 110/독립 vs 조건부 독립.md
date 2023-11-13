# 독립 vs 조건부 독립

## 조건부 독립의 정의
Event $A,\, B$ are conditionally independent given $C$.
$P(A\cap B|C) = P(A|C)P(B|C)$

## 독립과 조건부 독립
Q: Dose conditional independence given $C$ imply unconditional independence?
A: **NO**. If conditionally independent, They may or may not be independent.

Q: Does inpedendence imply conditional independece iven $C$?
A: **NO**.
    Ex.
    $A$: firealram goes off
    $F$: fire
    $C$: popcorn
    Suppose $F,C$ are independence. But, what's the porbability that $P(F|A,C^c)$?
    $P(F|A,C^c) = 1$. $F,C$ is independent but not conditional inpedendence given alarm goes off.