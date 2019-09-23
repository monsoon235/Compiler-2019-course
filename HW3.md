# Compiler 2019 Homework 3

## 3.1

### (a)

- `(a,(a,a))`:

![](pics/3.1(a)-1.png)

- `(a,((a,a),(a,a)))`:

![](pics/3.1(a)-2.png)

### (b)

- `(a,(a,a))`: $S \implies (L) \implies (L,S) \implies (S,S) \implies (a,S) \implies (a,(L)) \implies (a,(L,S)) \implies (a,(S,S)) \implies (a,(a,S)) \implies (a,(a,a))$

- `(a,((a,a),(a,a)))`: $S \implies (L) \implies (L,S) \implies (S,S) \implies (a,S) \implies(a,(L)) \implies (a,(L,S)) \implies (a,(S,S)) \implies (a,((L),S)) \implies (a,((L,S),S)) \implies (a,((S,S),S)) \implies (a,((a,S),S) \implies (a,((a,a),S)) \implies (a,((a,a),(L))) \implies (a,((a,a),(L,S))) \implies (a,((a,a),(S,S))) \implies (a,((a,a),(a,S))) \implies (a,((a,a),(a,a)))$

## 3.6

### (b)

$$S \to abS \mid baS \mid aSb \mid bSa \mid Sab \mid Sba \mid \varepsilon$$

不是正规的。

### (c)

$$\begin{aligned}
    S &\to A \mid B \\
    T &\to abS \mid baS \mid aSb \mid bSa \mid Sab \mid Sba \mid \varepsilon \\
    A &\to aT \mid Ta \mid aA \mid Aa \\
    B &\to bT \mid Tb \mid bB \mid Bb
\end{aligned}$$

不是正规的。

## 3.8

### (a)

$$\begin{aligned}
    S &\to (L) \mid a \\
    L &\to S L' \\
    L' &\to , S L' \mid \varepsilon
\end{aligned}$$

### (b)

First(S) = {`(`, `a`}

First(L) = First(S) = {`(`, `a`}

First(L') = {`,`, $\varepsilon$}

Follow(L) = {`)`}

Follow(L') = Follow(L) = {`)`}

Follow(S) = {\$} + ( First(L') - {$\varepsilon$} ) + Follow(L) + Follow(L') = {`,`, `)`, \$}

| 非终结符 | First()            | Follow()     |
| -------- | ------------------ | ------------ |
| S        | `(`, `a`           | `,`, `)`, \$ |
| L        | `(`, `a`           | `)`          |
| L'       | `,`, $\varepsilon$ | `)`          |

分析表如下：

| 非终结符 | `a`          | `(`          | `)`                  | `,`           | \$  |
| -------- | ------------ | ------------ | -------------------- | ------------- | --- |
| S        | $S \to a$    | $S \to (L)$  |                      |               |     |
| L        | $L \to S L'$ | $L \to S L'$ |                      |               |     |
| L'       |              |              | $L' \to \varepsilon$ | $L' \to ,SL'$ |     |

## 3.10

First(D) = {`int`}

First(T) = {`int`, `real`}

First(L) = {`id`}

First(R) = {`,`, $\varepsilon$}

Follow(D) = {\$}

Follow(T) = First(L) - {$\varepsilon$} = {`id`}

Follow(L) = Follow(A) = {\$}

Follow(R) = Follow(L) = {\$}

| 非终结符 | First()            | Follow() |
| -------- | ------------------ | -------- |
| D        | `int`              | \$       |
| T        | `int`, `real`      | `id`     |
| L        | `id`               | \$       |
| R        | `,`, $\varepsilon$ | \$       |

分析表如下：

| 非终结符 | `int`      | `real`      | `id`         | `,`             | \$                |
| -------- | ---------- | ----------- | ------------ | --------------- | ----------------- |
| D        | $D\to TL$  | $D\to TL$   |              |                 |                   |
| T        | $T\to int$ | $T\to real$ |              |                 |                   |
| L        |            |             | $L\to id\ R$ |                 |                   |
| R        |            |             |              | $R\to ,\ id\ R$ | $R\to\varepsilon$ |

## 3.11

First(S) = {`a`, `b`, $\varepsilon$}

First(A) = {`a`, `b`}

First(B) = {`a`, `b`}

Follow(S) = {\$}

Follow(A) = ( First(S) - {$\varepsilon$} ) + Follow(S) + First(A) = {`a`, `b`, \$}

Follow(B) = ( First(S) - {$\varepsilon$} ) + Follow(S) + First(B) = (`a`, `b`, \$)

| 非终结符 | First()                 | Follow()     |
| -------- | ----------------------- | ------------ |
| S        | `a`, `b`, $\varepsilon$ | \$           |
| A        | `a`, `b`                | `a`, `b`, \$ |
| B        | `a`, `b`                | `a`, `b`, \$ |

分析表如下：

| 非终结符 | `a`        | `b`        | \$                |
| -------- | ---------- | ---------- | ----------------- |
| S        | $S\to aBS$ | $S\to bAS$ | $S\to\varepsilon$ |
| A        | $A\to a$   | $A\to bAA$ |                   |
| B        | $B\to aBB$ | $B\to b$   |                   |

## 3.12

$First(AB)=\lbrace x \rbrace$

$First(PQx)=\lbrace a,d,x \rbrace$

$First(AB) \bigcap First(PQx) = \lbrace x \rbrace \neq \emptyset$

所以不是 LL(1) 文法
