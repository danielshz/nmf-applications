# Non-Negative Matrix Factorization (NMF)

## Introdução
A **Fatoração de Matrizes Não-Negativas (NMF)** é um conjunto de algoritmos utilizado para análise de problemas multivariáveis e de álgebra linear, sendo também encarada como uma técnica de aprendizado não supervisionado amplamente usada em diversas áreas como:

- Processamento de sinais de áudio
- Astronomia
- Visão computacional
- Bioinformática
- Recomendação de sistemas
- Análise de documentos

O NMF consiste na fatoração de uma matriz $V$ (não negativa) em duas matrizes $W$ e $H$, onde todos os elementos são não-negativos. Embora não haja uma solução exata para essa fatoração, uma aproximação numérica pode ser utilizada.

<img src="https://github.com/danielshz/nmf-applications/blob/main/assets/figura1.png" alt="Fatoração" style="background-color:white; padding:10px;">

*Ilustração da aproximação da matriz* $V$ *representada por duas matrizes menos* $W$ *e* $H$*, usando non-negative matrix factorization (Wikipedia).*

## Estrutura

### Matriz de Entrada
A matriz $V$ (dimensão $m \times n$) contém valores multivariados não-negativos, ou seja, maiores ou iguais a zero (ex: intensidade das cores de pixels em imagens).

### Matrizes de Fatoração
- **$W$**: Contém uma base otimizada, de dimensão $m \times r$, onde $r$ é escolhido pelo usuário.
- **$H$**: Coeficientes de combinação linear, de dimensão $r \times n$, usados para aproximar $V$.

A equação de aproximação pode ser escrita como:
$$V \approx W \times H$$

## Aplicações
### Processamento de Imagens
A NMF pode ser usada para representar imagens como uma combinação de partes básicas (por exemplo, rostos e suas partes como olhos, nariz e boca), com valores não-negativos tornando a interpretação mais intuitiva.

<img src="https://github.com/danielshz/nmf-applications/blob/main/assets/figura2.png" alt="Fatoração" style="background-color:white; padding:10px;">

*Representação de faces usando algoritmos de aprendizado non-negative matrix factorization (NMF), principal component analysis (PCA) e vector quantization (VQ). A base de dados utilizada tinha 2429 imagens de 19 X 19 pixels e foram fatoradas em 49 imagens base (Nature 1999)*

### Análise de Texto
Em documentos textuais, a NMF pode ser aplicada para encontrar padrões semânticos ao fatorar a matriz de frequência de palavras em bases otimizadas e seus coeficientes.

<img src="https://github.com/danielshz/nmf-applications/blob/main/assets/figura3.png" alt="Fatoração" style="background-color:white; padding:10px;">

*Utilização do non-negative matrix factorization (NMF) para descobrir características semânticas de 30991 artigos da enciclopédia Grolier, considerando um vocabulário de 15276 palavras para cada documento. Foram extraídas 200 características semânticas desses documentos, sendo exibidas no canto esquerdo superior algumas delas*

## Algoritmo
O problema de NMF é resolvido usando **Gradiente Descendente Alternado (GD)**, onde as matrizes $W$ e $H$ são atualizadas iterativamente para minimizar a função de erro:

$$ \min \| V - W H \|_F^2 $$

As atualizações seguem um esquema multiplicativo que garante a não-negatividade dos elementos em cada iteração.

## Características
- **Convergência local**: O algoritmo não garante encontrar o mínimo global, mas assegura uma convergência local.
- **Esparsidade**: Muitas vezes, as soluções encontradas são esparsas, ou seja, muitas entradas de $W$ e $H$ são zero, facilitando a interpretação.
- **Interpretação intuitiva**: As matrizes fatoradas são mais interpretáveis devido à restrição de não-negatividade.
