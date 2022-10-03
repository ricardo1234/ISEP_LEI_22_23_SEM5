# PL 1

### Exercise 1

Create file [Knowledge Base](bd.pl).

### Exercise 2

França faz fronteira com Espanha?

```prolog	
fronteira(franca,espanha).
false.
```

Espanha faz fronteira com França?

```prolog	
fronteira(espanha,franca).
true.
```

Qual a população do México em milhões?

```prolog
    pais(mexico, X, Y).
    X = america,
    Y = 129.2.
```

Qual a população do Brasil em milhões?

```prolog
    pais(brasil, X, Y).
    X = america,
    Y = 209.3.
```

### Exercise 3

#### a)

Predicado 'vizinho' que verifica se dois países são vizinhos.

```prolog
    vizinho(P1,P2):- fronteira(P1,P2);fronteira(P2,P1).
```

Teste:

```prolog
    vizinho(franca,espanha).
    true.
```

```prolog
    vizinho(espanha,franca).
    true.
```

#### b)

Predicado 'contSemPaises' que verifica continetes sem paises.

```prolog
    contSemPaises(C):- not(pais(_,C,_)).
```

Teste:

```prolog
    contSemPaises(africa).
    true.
```

```prolog
    contSemPaises(america).
    false.
```

#### c)

Predicado 'semVizinhos' verifica países sem vizinhos.

```prolog
    semVizinhos(P):- not(vizinho(P,_)).
```

Testes:

```prolog
    semVizinhos(F).
        F = cuba ;
        F = mexico ;
        F = estadosunidos ;
        F = canada ;
        F = chipre ;
        F = islandia ;
        F = malta ;
        false.
```

```prolog
    semVizinhos(cuba).
        true.
```

#### d)

Predicado 'chegoLaFacil' se é possível chegar de P1 a P2,
diretamente ou atravessando unicamente um outro país.


```prolog
    chegoLaFacil(P1,P2):-pais(P1,_,_),pais(P2,_,_),(vizinho(P1,P2);(vizinho(P1,P3),vizinho(P2,P3))).
```

Testes:

```prolog
    chegoLaFacil(potugal,franca).
    true.
```

```prolog
    chegoLaFacil(potugal,cuba).
    flase.
```

### Exercise 4

#### a)

Fazer predicado recursivo para calcular a potência positiva e negativa.

```prolog
    potenciaPos(_,0,1):-!.

    potenciaPos(N,P,R):- P>0, P1 is P-1, potenciaPos(N,P1,R1), R is N*R1.

    potenciaNeg(_,0,1):-!.

    potenciaNeg(N,P,R):- P<0, P1 is P+1, potenciaNeg(N,P1,R1), R is R1/N.

    potencia(N,P,R):- (potenciaPos(N,P,R));(potenciaNeg(N,P,R)).
```

Testes:

```prolog
    potencia(2,3,R).
    R = 8.
```

```prolog
    potencia(2,-3,R).
    R = 0.125.
```

#### b)

Fazer predicado recursivo para calcular fatorial de um numero.

```prolog
    fatorial(1,1):-!.
    fatorial(N,R):- N>1, N1 is N-1, fatorial(N1,R1), R is N*R1.
```

Testes:

```prolog
    fatorial(1,X).
    X = 1.
```

```prolog
    fatorial(4,X).
    X = 24.
```
#### c)

Fazer predicado recursivo para calcular somatorio entre dois numeros.

```prolog
    somatorio(J,J,J):-!.
    somatorio(J,K,N):- J<K, J1 is J+1, somatorio(J1,K,N1), N is N1+J.
```

Testes:

```prolog
    somatorio(5,5,X).
    X = 5.
```

```prolog
    somatorio(5,9,X).
    X = 35.
```

#### b)

Fazer predicado recursivo para calcular fatorial de um numero.

```prolog
    fatorial(1,1):-!.
    fatorial(N,R):- N>1, N1 is N-1, fatorial(N1,R1), R is N*R1.
```

Testes:

```prolog
    fatorial(1,X).
    X = 1.
```

```prolog
    fatorial(4,X).
    X = 24.
```
#### c)

Fazer predicado recursivo para calcular a divisão inteira e resto entre dois numeros.

```prolog
    divide(X, X, 1, 0):-!.
    divide(X, Y, I, R):- X<Y, I is 0, R is X.
    divide(X, Y, I, R):- X1 is X-Y, divide(X1, Y, I1, R), I is I1+1.
```

Testes:

```prolog
    divide(2,2,I,R).
    I = 1,
    X = 0
```

```prolog
    divide(5,2,I,R).
    I = 2,
    X = 1
```
