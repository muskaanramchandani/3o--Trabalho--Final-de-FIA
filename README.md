# 3o--Trabalho--Final-de-FIA

## Fundamentos de Inteligência Artificial (ES01)

Integrantes:
1. FERNANDA SOUZA DE FREITAS;
2. GABRIEL DA SILVA GLÓRIA;
3. GABRIEL DE ALBUQUERQUE FAÇANHA;
4. JULIO CESAR CERRATE CASTRO;
5. MUSKAAN RAMCHANDANI;
6. PEDRO HENRIQUE BARROS MENDONÇA;
7. RUAN COSTA DE MAGAÇHÃES.

Email:
1. fernanda.freitas@icomp.ufam.edu.br
2. gabriel.gloria@icomp.ufam.edu.br
3. gabriel.facanha@icomp.ufam.edu.br
4. julio.cesar@icomp.ufam.edu.br
5. muskaan.ramchandani@icomp.ufam.edu.br
6. pedro.mendonca@icomp.ufam.edu.br
7. ruan.costa@icomp.ufam.edu.br

Link do Colab: https://colab.research.google.com/drive/15EEh0pLuhf-lv1yyI3RFIOvayQ5xAZJ_#scrollTo=Kqtr2ntvH5yI

# Neuro-Symbolic Reasoning with LTNtorch on CLEVR

Este projeto explora raciocínio neuro-simbólico utilizando Logic Tensor Networks (LTN)
aplicadas a uma versão simplificada do dataset CLEVR.

## 1. NeSy e LTN
Neuro-Symbolic AI combina redes neurais com lógica simbólica, permitindo aprendizado
robusto aliado a capacidade de raciocínio. Logic Tensor Networks (LTN) integram
predicados neurais com lógica fuzzy, possibilitando a avaliação de fórmulas lógicas
em dados contínuos.

## 2. Dataset CLEVR Simplificado
Cada objeto é representado por um vetor contendo:
- posição (x, y)
- cor (R, G, B)
- forma (one-hot)
- tamanho (pequeno/grande)

Os dados são gerados aleatoriamente a cada execução.

## 3. Fórmulas e Satisfatibilidade
Foram definidas fórmulas lógicas representando restrições espaciais e semânticas.
A satisfatibilidade (satAgg) é calculada como a média dos valores fuzzy das fórmulas.

## 4. Experimentos
Foram realizadas 5 execuções independentes, cada uma com um dataset aleatório distinto.
Em cada execução foram calculados:
- Satisfatibilidade (satAgg)
- Accuracy
- Precision
- Recall
- F1-score

Os resultados são exportados em formato CSV.

## 5. Explicabilidade
Cada consulta lógica possui uma interpretação direta em linguagem natural, permitindo
raciocínio interpretável sobre os dados.

