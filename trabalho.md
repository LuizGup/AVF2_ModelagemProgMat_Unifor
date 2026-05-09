# Modelagem em Programa ̧c ̃ao Matem ́atica

## Trabalho - AV

Software utilizado:
OR-Tools.

Exemplos e documenta ̧c ̃ao:
https://developers.google.com/optimization/

Proposta de projeto:
(i) formar equipes de at ́e 3 pessoas;
(ii) implementar um modelo gen ́erico de Programa ̧c ̃ao Linear Inteira para
resolver o problema de corte unidimensional.

Demais informa ̧c ̃oes:
(i) as apresenta ̧c ̃oes ocorrer ̃ao nas datas previstas no plano de ensino, em
sala de aula ou laborat ́orio, sendo a ordem dada por um sorteio nos dias das
apresenta ̧c ̃oes;
(ii) o professor da disciplina conduzir ́a a apresenta ̧c ̃ao, determinando o que
cada integrante da equipe ir ́a apresentar;
(iii) a nota do trabalho comp ̃oe 20% da AV2;
(iv) a c ́opias, ser ́a atribu ́ıda a nota 0 `as equipes envolvidas;
(v) a ́unica biblioteca a ser utilizada para a realiza ̧c ̃ao do projeto ́e a
do OR-Tools; do contr ́ario, sua implementa ̧c ̃ao ser ́a desconsiderada;
(vi) deve ser utilizada a mesma sintaxe do OR-Tools usada nas
aulas; do contr ́ario, sua implementa ̧c ̃ao ser ́a desconsiderada.

## Problema de corte unidimensional

O problema de corte unidimensional foi visto durante a disciplina. Um enun-
ciado para o problema segue abaixo:

“Considere o problema de corte unidimensional onde barras de ferro de 150m
s ̃ao utilizadas para produzir demandas de barras menores nos tamanhos de

### 1


80m, 60m e 50m. A produ ̧c ̃ao de cada um dos tipos de barra de ferro da
demanda deve ser de 70, 100, e 120 unidades respectivamente. Escreva um
modelo que minimize o desperd ́ıcio na produ ̧c ̃ao da demanda desejada.”

Sabendo disso, fa ̧ca um programa gen ́erico, em linguagem de programa ̧c ̃ao
Python, que receba como entrada o tamanho da barra sobre a qual as de-
mandas ser ̃ao cortadas (no caso acima: 150). Em seguida, seu programa
deve receber a quantidade de tipos de itens que a demanda possui (no caso
acima: 3). Seu programa deve receber tamb ́em o tamanho de cada tipo de
item (no caso acima: 80, 60 e 50) e a quantidade a ser atendida de cada um
(no caso acima: 70, 100 e 120).

A partir da entrada e por meio do OR-Tools, modele o problema de forma
a minimizar o desperd ́ıcio para satisfazer a demanda. Seu programa deve
mostrar como sa ́ıda: a solu ̧c ̃ao ́otima, o desperd ́ıcio associado `a
solu ̧c ̃ao e o modelo de Programa ̧c ̃ao Linear Inteira. Observa ̧c ̃ao:
padr ̃oes incorretos (sejam mais padr ̃oes ou menos) invalidar ̃ao o
seu trabalho, uma vez que n ̃ao estar ́a condizente com o problema
proposto. Isso ́e determinante para validar o seu modelo!

### 2


