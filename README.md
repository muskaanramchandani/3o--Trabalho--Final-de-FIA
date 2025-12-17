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


# Sistema de Raciocínio Neuro-Simbólico com Logic Tensor Networks (LTN)

Este repositório contém a implementação do Trabalho Final de Inteligência Artificial, focado em uma arquitetura **Neuro-Simbólica**. O projeto utiliza o framework **LTNtorch** para integrar Deep Learning com Lógica Fuzzy, permitindo o raciocínio sobre cenários visuais e a validação de regras lógicas complexas.

## 📋 Sobre o Projeto

O sistema é capaz de processar ambientes visuais simulados (inspirados no dataset CLEVR simplificado) para classificar objetos e inferir relações espaciais e semânticas.

**Principais capacidades:**
* **Classificação de Atributos**: Cor, Forma, Tamanho e Posição.
* **Inferência de Relações**: *Precedes* (Precede), *Beneath* (Abaixo), *IntermediatePosition* (Entre).
* **Validação Lógica**: Aprendizado guiado por axiomas (regras) que definem a consistência do mundo.

## 🛠️ Tecnologias Utilizadas

* **Python 3.8+**
* **[LTNtorch](https://github.com/logictensornetworks/LTNtorch)**: Framework de Logic Tensor Networks.
* **PyTorch**: Backend de redes neurais.
* **Matplotlib**: Visualização dos cenários 2D.
* **Scikit-Learn**: Cálculo de métricas de avaliação.

## ⚙️ Instalação

Para executar este projeto, instale as dependências listadas abaixo. Note que o `LTNtorch` deve ser instalado via git.

```bash
# Instalação do LTNtorch
pip install git+[https://github.com/logictensornetworks/LTNtorch](https://github.com/logictensornetworks/LTNtorch)

# Outras dependências essenciais
pip install torch numpy matplotlib scikit-learn
```
## 🚀 Pipeline da Arquitetura

O código segue um fluxo estruturado em 12 etapas principais:

1.  **Inicialização e Setup**: Configuração do ambiente e *seeds* para reprodutibilidade.
2.  **Síntese de Cenários**: Geração de objetos com vetores de 11 dimensões (Posição, Cor, Forma, Tamanho).
3.  **Renderização**: Visualização gráfica personalizada dos objetos (Cilindros, Cones, Prismas).
4.  **Redes Neurais (Predicados)**:
    * `FeatureExtractor`: Extração de *features* diretas dos vetores.
    * `BinaryPredictor`: Rede para prever relações entre dois objetos.
    * `TernaryPredictor`: Rede para prever relações entre três objetos.
5.  **Modelos Paramétricos**: Classificadores de magnitude (tamanho) e modelos de proximidade gaussiana.
6.  **Lógica Fuzzy**: Definição de conectivos (`AND`, `OR`, `IMPLIES`) e quantificadores (`FORALL`, `EXISTS`) diferenciáveis.
7.  **Definição de Axiomas**: Regras lógicas de taxonomia (ex: "Cone implica Volumoso") e exclusão (ex: "Esfera não é Cubo").
8.  **Treinamento**: Otimização dos parâmetros baseada na maximização da satisfação da Base de Conhecimento (Sat KB).
9.  **Avaliação**: Cálculo de métricas como F1-Score e precisão das inferências aprendidas.

## 🧠 Base de Conhecimento (Exemplos de Axiomas)

O modelo aprende a satisfazer regras lógicas que definem o comportamento do ambiente:

* `Forall x: Cone(x) → Massive(x)`
    *(Todo cone é massivo)*
* `Forall x: Sphere(x) → ¬Red(x)`
    *(Esferas não podem ser vermelhas)*
* `Forall x,y: Blue(x) ∧ Prism(x) → Exists y: Green(y) ∧ Beneath(y, x)`
    *(Se existe um Prisma azul, deve haver algo verde abaixo dele)*

## 📊 Resultados Consolidados

Abaixo, a performance média após 5 execuções (Runs) em cenários distintos.

| Run | Sat KB | Prec F1 | Beneath F1 | Q1 (Sat) | Q2 (Sat) |
|:---:|:------:|:-------:|:----------:|:--------:|:--------:|
|  1  | 0.6464 |  0.9366 |   0.9604   |  0.0722  |  0.2205  |
|  2  | 0.6623 |  0.9296 |   0.9404   |  0.0689  |  0.2790  |
|  3  | 0.6509 |  0.9517 |   0.9658   |  0.1334  |  0.1663  |
|  4  | 0.6582 |  0.9393 |   0.9659   |  0.0810  |  0.1727  |
|  5  | 0.6543 |  0.9412 |   0.9588   |  0.0950  |  0.2100  |

* **Sat KB**: Satisfação global da base de conhecimento (0.0 a 1.0).
* **F1 Scores**: Precisão harmônica das relações espaciais aprendidas.

## 🖥️ Como Usar

1.  Faça o clone deste repositório.
2.  Abra o arquivo `TRAB_FINAL_IA.ipynb` no Jupyter Notebook, VS Code ou Google Colab.
3.  Execute todas as células sequencialmente.
4.  Os gráficos dos cenários e as métricas detalhadas serão exibidos ao final da execução.
Link do Colab: https://colab.research.google.com/drive/1J7sbf3XxmBgcN9vVUPfqRR-gr0oJYcHC?usp=sharing
---
*Projeto desenvolvido para a disciplina de Inteligência Artificial.*
