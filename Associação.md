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


  

