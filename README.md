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

1.  **Inicialização**: Configuração do ambiente.
2.  **Importação de Dependências**: Carregamento das bibliotecas necessárias.
3.  **Construção de Cenários**: Geração dos vetores de características dos objetos (11 dimensões: posição, cor, forma, tamanho).
4.  **Renderização Espacial**: Visualização 2D dos objetos (Cilindros, Cones, Prismas, etc.).
5.  **Camadas Neurais (Predicados):**:
    * `FeatureExtractor`: Extração de *features* diretas dos vetores.
    * `BinaryPredictor`: Rede para prever relações entre dois objetos.
    * `TernaryPredictor`: Rede para prever relações entre três objetos.
6.  **Modelos Paramétricos**:
    * `ProximityModel`: Modelo Gaussiano para calcular proximidade.
    * `MagnitudeClassifier`: Classificação de tamanho (Massive vs Minute).
    * `StackabilityPredictor`: Predição de capacidade de empilhamento.
7.  **Atributos Primitivos**: Definição dos predicados base (HasRed, ShapeSpherical, IsMassive, etc.).
8.  **Operadores Fuzzy**: Configuração dos conectivos lógicos (AND, OR, IMPLIES, NOT) e quantificadores (FORALL, EXISTS).
9.  **Sistema de Axiomas**:Construção da Base de Conhecimento com regras lógicas.
10.  **Avaliação Semântica**: Cálculo da verdade semântica e satisfação da base.
11.  **Protocolo Experimental**: Execução de ciclos de teste em ambientes distintos.
12.  **Agregação de Métricas**: Consolidação dos resultados estatísticos.

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

Run  | Sat KB   | Prec F1  | Beneath F1 | Q1       | Q2       | Q3       | Q4      
---------------------------------------------------------------------------------------------------------
1    | 0.6464   | 0.9366   | 0.9604   | 0.0722   | 0.2205   | 0.9996   | 0.6255  
2    | 0.6623   | 0.9296   | 0.9404   | 0.0689   | 0.2790   | 0.9995   | 0.6027  
3    | 0.6509   | 0.9517   | 0.9658   | 0.1334   | 0.1663   | 0.9994   | 0.4241  
4    | 0.6582   | 0.9393   | 0.9659   | 0.0810   | 0.1727   | 0.9993   | 0.5813  
5    | 0.6571   | 0.9319   | 0.9744   | 0.0443   | 0.2239   | 0.9997   | 0.5277  
-----------------------------------------------------------------------------------------------
AVG  | 0.6550   | 0.9378   | 0.9614  
===============================================================================================

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
