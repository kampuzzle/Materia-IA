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
