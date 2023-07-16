# Regressão

A regressão é um método estatístico utilizado para modelar a relação entre uma variável dependente (também chamada de variável resposta) e uma ou mais variáveis independentes (também chamadas de variáveis preditoras ou regressores). O objetivo da regressão é encontrar uma equação matemática que possa descrever e prever a relação entre essas variáveis.

A função objetivo é a soma dos erros quadráticos (SEQ)

$Σ(predito_i - real_i)² = Σ(residual)²$

---

## Regressão linear simples

Envolve apenas uma variável independente e uma variável dependente. A regressão linear simples procura ajustar uma linha reta aos dados, minimizando a soma dos erros quadrados entre os valores observados e os valores preditos pela linha.

$y = β_0 + β_1 * x$

Os coeficientes são obtidos das seguintes fórmulas

$β_1 = \frac{nΣ(xy) - ΣxΣy}{nΣx²-(Σx)²}$

$β_0 = \frac{Σy - β_1Σx}{n}$

---

## Regressão linear múltipla

Extensão da regressão linear simples, onde há mais de uma variável independente. Nesse caso, a regressão linear múltipla busca ajustar um plano ou uma superfície hiperplanar aos dados para prever a variável dependente.

Entrada multidimensional, X é o vetor de características.

$Y = β_0 + β_1X_1 + β_2X_2 + ... + β_nX_n$

---

## Regressao linear multivariada

Extensão da regressão linear simples, na qual existem múltiplas variáveis independentes (também chamadas de variáveis preditoras) para prever uma variável dependente (também chamada de variável resposta).

Entrada e saída multidimensionais, X é o vetor de características e Y é o vetor de resultados.

Função objetivo é a média da soma da média dos erros quadráticos.

Equivale a soma das distâncias euclideanas:

$\frac{1}{N} Σ_{i=1}^{N} \frac{1}{M} Σ_{j=1}^{M}(ŷ_{ij} - y_{ij})²$

---

## Métricas de avaliação

* **MAE:** Erro médio absoluto
  
  $MAE = \frac{1}{N} Σ_{i=1}^{N} |y_i - ŷ|$

* **MSE:** Erro médio quadrático

  $MSE = \frac{1}{N} Σ_{i=1}^{N} (y_i - ŷ)²$

* **RMSE:** Raíz do erro médio quadratico

  $RMSE = √MSE$

* **R²:** Coeficiente de determinação

  $R² = 1 - \frac{Σ(y_i - ŷ)²}{Σ(y_i - ỹ)²}$

Em que $ŷ$ é o valor predito de $y$ e $ỹ$ é o valor médio de $y$
