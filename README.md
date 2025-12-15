# 3o--Trabalho--Final-de-FIA

## Fundamentos de Inteligência Artificial (ES01)

Integrantes:
1. FERNANDA SOUZA DE FREITAS;
2. GABRIEL DA SILVA GLÓRIA;
3. GABRIEL DE ALBUQUERQUE FAÇANHA;
4. JULIO CESAR CERRATE CASTRO;
5. MUSKAAN RAMCHANDANI;
6. PEDRO HENRIQUE BARROS MENDONÇA;
7. RUAN COSTA DE MAGALHÃES.

Email:
1. fernanda.freitas@icomp.ufam.edu.br
2. gabriel.gloria@icomp.ufam.edu.br
3. gabriel.facanha@icomp.ufam.edu.br
4. julio.cesar@icomp.ufam.edu.br
5. muskaan.ramchandani@icomp.ufam.edu.br
6. pedro.mendonca@icomp.ufam.edu.br
7. ruan.costa@icomp.ufam.edu.br


# Neuro-Symbolic Reasoning com LTNtorch e CLEVR

Este repositório apresenta a implementação de um sistema de raciocínio
neuro-simbólico utilizando Logic Tensor Networks (LTNtorch), aplicado a
uma versão simplificada do dataset CLEVR.

O objetivo do trabalho é explorar a integração entre aprendizado neural
e lógica simbólica, avaliando fórmulas lógicas e consultas semânticas
sobre dados visuais estruturados.

---

## 1. NeSy e LTN

Neuro-Symbolic AI (NeSy) combina modelos de aprendizado profundo com
representações simbólicas, permitindo unir a capacidade de generalização
das redes neurais com raciocínio lógico interpretável.

Logic Tensor Networks (LTN) implementam lógica fuzzy sobre tensores,
onde predicados lógicos são parametrizados por modelos neurais, e
fórmulas lógicas podem ser avaliadas de forma diferenciável por meio
de operadores fuzzy.

---

## 2. Dataset CLEVR Simplificado

O dataset utilizado é inspirado no CLEVR e é gerado artificialmente.
Cada objeto é representado por um vetor numérico contendo:

- Posição espacial: (x, y)
- Cor: (R, G, B)
- Forma: codificação one-hot (círculo, quadrado, cilindro, cone, triângulo)
- Tamanho: pequeno (0) ou grande (1)

Os dados são gerados aleatoriamente a cada execução, permitindo avaliar
a robustez do raciocínio em diferentes cenários.

---

## 3. Fórmulas Lógicas

Foram definidas fórmulas lógicas básicas para garantir consistência
semântica no conjunto de dados:

- Um objeto não pode ser círculo e quadrado simultaneamente
- Todo objeto é círculo ou quadrado
- Nenhum objeto pode estar à esquerda de si mesmo
- Se um objeto está à esquerda de outro, o inverso não ocorre

Essas fórmulas são avaliadas por meio de satisfatibilidade fuzzy.

---

## 4. Consultas Lógicas

Além das fórmulas básicas, foram definidas consultas que representam
relações espaciais e semânticas mais complexas.

### Consulta 1
**Existe um objeto pequeno que está abaixo de um cilindro e à esquerda de um quadrado.**

### Consulta 2
**Existe um objeto verde que está entre dois outros objetos.**

### Consulta 3
**Dois triângulos próximos possuem o mesmo tamanho.**

---

## 4.1 Explicação do Raciocínio (Ponto Extra)

Nesta seção é apresentado o raciocínio lógico associado a cada consulta,
em linguagem natural, caracterizando o ponto extra solicitado.

### Raciocínio da Consulta 1

A Consulta 1 verifica a existência de um objeto que satisfaça
simultaneamente três condições: ser pequeno, estar abaixo de um cilindro
e estar à esquerda de um quadrado. Essas condições são combinadas por
conjunções lógicas fuzzy, permitindo avaliar o grau de satisfação da
consulta mesmo quando as condições não são perfeitamente verdadeiras.

### Raciocínio da Consulta 2

A Consulta 2 busca identificar a existência de um objeto verde que esteja
localizado entre dois outros objetos. O conceito de "estar entre" é
modelado de forma composicional por meio das relações espaciais `leftOf`
e `rightOf`, demonstrando a capacidade expressiva do raciocínio
neuro-simbólico.

### Raciocínio da Consulta 3

A Consulta 3 expressa uma regra universal segundo a qual, se dois objetos
forem triângulos e estiverem próximos, então eles devem possuir o mesmo
tamanho. Essa regra integra predicados neurais (proximidade) com
predicados simbólicos (forma e tamanho).

---

## 5. Avaliação Experimental

Foram realizadas **5 execuções independentes**, cada uma com um dataset
aleatório distinto. Em cada execução foram calculadas as seguintes
métricas:

- Satisfatibilidade média das fórmulas (satAgg)
- Accuracy
- Precision
- Recall
- F1-score

As métricas foram obtidas a partir da saída dos modelos neurais
associados aos predicados LTN.

---

## 6. Resultados

Os resultados completos das cinco execuções estão disponíveis no
arquivo: https://colab.research.google.com/drive/15EEh0pLuhf-lv1yyI3RFIOvayQ5xAZJ_#scrollTo=Kqtr2ntvH5yI




