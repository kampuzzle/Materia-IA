# Agrupamento

* Também conhecido como clustering, técnica de análise de dados que visa dividir um conjunto de objetos em grupos, para que instâncias do mesmo grupo sejam similares entre si e diferentes de instâncias de outros grupos.
* Essas diferenças são definidas por medidas de distância ou similaridade/dissimilaridade

---

## Medidas de distância comuns

1. **Euclidiana:**
   $sqrt(sum(x-y)²)$
2. **Manhattan:**
   $sum(|x-y|)$
3. **Chebyshev:**
   $max(|x-y|)$  
4. **Hemming:**
   $\frac{N_uneq(x,y)}{N_total}$

---

## Métodos de Agrupamento

1. Particionais:
   * Criam grupos de forma iterativa
   * Reparticiona/reorganiza até atingir um limiar
2. Hierárquicos:
   * **Aglomeratívo:** cria pequenos grupos juntando as instâncias, repartindo até atingir um critério de parada.
   * **Divisivo:** considera todas as intâncias como pertencentes a um grande grupo, e subdivide recursivamente esse grupo.
3. Baseados em densidade:
   * A forma e o número de grupos não são definidos previamente

---

## K-MEANS

* **Entradas:**
  1. Número de grupos (K)
  2. Instâcias
  3. Número máximo de iterações
 
* **Saídas:**
  1. Centróide dos grupos
  2. Grupos
  3. Instâncias dos grupos

* Tenta minimizar o erro quadrático (Inércia) entre as instâncias e o centróide dos grupos
  
* **Procedimento:**
  1. Escolhe aleatoriamente *K* elementos como centroide dos grupos;
  2. Para cada instância, calcula a distância para os centroides e a aloca ao grupo com a menor distância ;
  3. Retepe a etapa 2 enquanto o algoritmo não convergir (converge quando chega em uma iteração sem nenhuma mudança de grupos).
 
* **Problemas:**
  1. Funciona melhor para grupos de formato esférico;
  2. Escolha inicial dos centróides:
     1. Normalmente aleatória;
     2. Resultados podem variar de execução para execução;
     3. Dependendo da escolha, a solução pode convergir para um mínimo local.
  3. O número de grupos (clusters) precisam ser definidos previamente.
 
* **Comparação das soluções:**
  * A comparação é feita pela inércia ou soma das distâncias euclidianas quadráticas:
    
    $SSE = ∑_{j=1}^{k} ∑_{x_j∈C_j} ||x_i-μ_j||²$
  * Quanto maior o *K*, menor será o valor da *SSE*

 ---

## Hierárquico Aglomerativo

* Processo iterativo, a cada passo um grupo se une a outro
* Pode ser interrompido no momento que for necessário
* Pode ser visualizado através de um dendograma
* **Critérios de ligação:**
  1. **Simples:** minimiza distancia mínima entre componentes de pares de clusters;
  2. **Completa:** minimiza distância máxima entre componentes de pares de cluesters;
  3. **Média:** minimiza distância média entre todos os componentes de pares de clusters;
  4. **Ward:** minimiza a inércia (avalia todos os possíveis agrupamentos para decidir);
* **Vantagens:**
  1. Podem ser formados grupos de vários formatos;
  2. Quantidade de agrupamentos não precisa ser pré-determinada;
  3. Análise dos resultados com uso de dendograma.
* **Procedimento:**
  1. Considera todas as instâncias como grupos;
  2. Localiza os dois grupos com menor distância entre eles e une estes grupos;
  3. Calcula a distância do novo grupo para os demais;
  4. Se não atingir critério de parada, volta ao passo 2.

---

## DBSCAN 

* Agrupamento sem padrão enviesao de formato
* Remove ruídos eficazmente
* Possui dois parâmetros principais:
  1. **ε (epsilon):** distância máxima entre dois vizinhos;
  2. **minPoints:** quantidade mínima de vizinhos em um grupo.
* Atribui três categorias aos pontos:
  1. **Core Points:** pontos com pelo menos *minPoints* vizinhos dentro de um raio *ε*. Formam o núcleo de um cluster.
  2. **Border Points:** pontos com menos de *minPoints* vizinhos dentro do raio *ε*, mas que estão dentro do raio de algum *Core Point*. Fazem parte de um clester.
  3. **Noise Points:** pontos com menos de *minPoints* vizinhos dentro do raio *ε* e que estão fora do raio de qualquer *Core Point*. São ruídos.
* **Dados categóricos:**
  1. Normalmente não ordinal;
  2. Problema do cálculo da distância.
* **Medidas de avaliação:**
  1. Inércia:
     * Minimiza soma de distâncias euclideanas quadradas intra-cluster
     * Serve para comparar soluções com o mesmo número de grupos apenas
     * Valoriza soluções de agrupamento esférico
  2. ARI (Adjusted Rand Index):
     * Verifica quão semelhante o agrupamento obtido pelo algoritmo equivale ao agrupamento de que deveria ser
     * Funciona quando já se sabe a resposta (ground truth)
     * Valores:
       1. 1.0: escore perfeito
       2. 0.0: equivalente a agrupamento aleatório
       3. <0.0: pior que agrupamento aleatório
          
  3. Coeficiente de Silhueta:
     * Não é necessário conhecer a resposta
     * Calculada elemento a elemento
     * Silhueta de agrupamento é a média da silhueta de todos os elementos

       $S = \frac{b - a}{max(a,b)}$

     * *a* corresponde a distância média do elemento para todos os outros dentro do grupo;
     * *b* corresponde a distância média do elemento para todos os elementos do grupo mais próximo.
     * Alta complexidade computacional: O(n²)
