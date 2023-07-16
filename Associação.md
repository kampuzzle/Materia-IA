# Associação

Regras de associação são técnicas de mineração de dados utilizadas para descobrir relações interessantes e padrões frequentes entre itens em grandes conjuntos de dados. Essas regras identificam associações entre diferentes itens ou eventos com base em sua coocorrência nos dados.

O objetivo das regras de associação é revelar associações entre itens frequentemente comprados, consumidos ou utilizados em conjunto. Essas associações podem ser úteis em várias aplicações, como análise de cestas de compras, recomendação de produtos, marketing personalizado e análise de comportamento do cliente.

---

## Conceitos e Definições

### Base de Dados para Mineração de Regras de Associação

* Tabela Booleana de Itens-Transações:
  
Nessa representação, cada linha da tabela corresponde a uma transação, e cada coluna representa um item específico. Os valores da tabela são binários (verdadeiro ou falso), indicando se um determinado item está presente ou não em uma transação. Essa representação é útil quando a presença ou ausência de um item é o único aspecto relevante para as análises de associação. Essa tabela é conhecida como matriz binária ou tabela de incidência.

* Tabela de Itens-Transações:

Nessa representação, cada linha da tabela corresponde a um item, e cada coluna representa uma transação. Os valores da tabela podem ser numéricos ou contabilizar a quantidade de vezes que um item aparece em uma transação. Essa representação é útil quando as quantidades, valores ou informações adicionais dos itens são importantes para a análise de associação.

### Suporte

* Quantifica a incidência de um itemset X no conjunto de dados

  $sup(x) = \frac{n(x)}{N} * 100$

* *n(X)* é o número de transações nas quais *X* ocorre e *N* é o número total de transações
* O suporte de uma regra de associação, representada como LHS ⇒ RHS, onde LHS U RHS = X, é uma medida da frequência relativa com que a combinação de itens em LHS e RHS ocorre na base de dados em relação ao número total de registros.
* **LHS (Lado Esquerdo):** Também conhecido como antecedente, é a parte da regra que contém os itens ou conjunto de itens que estão sendo utilizados para estabelecer uma associação ou predição. Os itens no LHS são considerados as condições ou premissas da regra.
* **RHS (Lado Direito):** Também conhecido como consequente, é a parte da regra que contém os itens ou conjunto de itens que são esperados ou preditos a ocorrer juntamente com os itens do LHS. Os itens no RHS são considerados as conclusões ou consequências da regra.

  $sup(LHS ⇒ RHS) = sup(LHS ∪ RHS) = \frac{n(LHS ∪ RHS)}{N} * 100$

* *n(LHS ⇒ RHS)* é o número de transações nas quais **LHS** e **RHS** ocorrem juntos e *N* é o número total de transações

### Confiança

* Freqüência com que LHS e RHS ocorrem juntos em relação ao número total de transações em que LHS ocorre
* A confiança de uma regra LHS ⇒ RHS pode ser representada por:

  $conf(LHS ⇒ RHS) = \frac{sup(LHS ∪ RHS)}{sup(LHS)} = \frac{n(LHS ∪ RHS)}{n(LHS)} * 100$

* n(LHS) é o número de transações nas quais LHS ocorre

### K Itemsets Frequentes

* se referem a conjuntos de itens que ocorrem com frequência em uma base de dados.
* O valor de K indica o número de itens no conjunto. Esses conjuntos de itens são considerados importantes na mineração de dados, pois revelam associações e padrões de coocorrência entre os elementos.
* Para identificar os K itemsets frequentes, é comum usar algoritmos como o Apriori ou o FP-Growth.
* Esses algoritmos exploram a propriedade de monotonicidade de frequência, onde um subconjunto de itens frequente também é frequente.
* **Apriori:**
  * um dos algoritmos mais populares para a descoberta de regras de associação. Ele funciona em etapas iterativas, começando com itemsets de tamanho 1 (conjuntos de itens individuais) e expandindo-os gradualmente até encontrar os itemsets frequentes desejados. O Apriori utiliza a propriedade de monotonicidade de frequência, onde um subconjunto de itens frequente também é frequente. Ele é eficiente para encontrar itemsets frequentes, mas pode ser computacionalmente custoso em bases de dados grandes.
  * Inicialmente o algoritmo conta a ocorrência de itens, determinando os 1-itemsets freqüentes que são armazenados em L1
  * Em cada passo k, o algoritmo é dividido em duas etapas
  * Na primeira etapa, o conjunto de itemsets freqüentes $L_{k-1}$ obtido no passo *(k – 1)* é utilizado para gerar o conjunto de *k-itemsets* candidatos $C_k$
  * Na segunda etapa, a Base de Dados é percorrida para determinar o valor do suporte dos *k-itemsets* candidatos em $C_k$
  * Os k-itemsets freqüentes de cada passo são identificados
  * A solução final é dada pela união dos conjuntos $L_k$ de *k-itemsets* freqüentes

---

## Coisas do gabarito

### Suporte

Mede a frequância com que um padrão ocorre no conjunto de dados

**Suporte = Numero de transações contendo A e B (ou apenas A) / Numero total de transações**

### Confiaça

Mede a proporção de transações que contem B entre as transações que contem A

**Confiança = Numero de transações contendo A e B / Numero de transações contendo A**

### Elevação

O quanto a ocorrenciade B é dependente de A, em comparação com sua ocorrencia no dataset

**Elevação = Suporte de A e B / Suporte de A * Suporte de B**

