# Busca

## Componentes das buscas

1. Variáveis: descrevem o problema (como todas as posições de um tabuleiro de xadrez)
2. Valores das variáveis: estabelecem o estado do problema (peças nas posições do tabuleiro)
3. Operadores: descrevem como os estados pdem ser modificados (todos os possíveis movimentos das peças)
4. Condição: descrevem o estado inicial (peças brancas de um lado, pretas ed outro), os estados válidos (onde peças não podem ficar) e os estados finais (cheque mate)
5. Função: descreve a qualidade do estado (núemro de peças no tabuleiro)

---

## Heurísticas

* São específicas para o problema proposto
* Acham uma solução, mas não necessariamente a solução ótima
* São normalmente baseadas em experiência
* **Vantagem:** podem usar livremente métodos e coisas que otimizem a solução ou o tempo de execução, já que são específicas para o problema
* **Desvantagem:** normalmente é difícil ou trabalhoso desenvolver uma heurística para um problema

---

## Meta-heurísticas

* São procedimentos *gerais*, podem ser aplicados a vários problemas
* Costumam incluir características que fazem o procedimento fugir de ótimos locais
* Fáceis de adaptar a novos problemas
* Normalmente não-determinísticos
* Possuem duas fases principais:
  1. **Diversificação:** fase inicial, visa explorar o espaço de estados
  2. **Intensificação:** fase final, visa aprimorar o resultado encontrado em alguma região do espaço de estados
* São divididas em dois tipos de solução: parciais e completas.


### Soluções Parciais

Explora o espaço de busca de maneira mais eficiente, não percorrendo todas as soluções possíveis. Algumas das meta-heurísticas de solução parcial estão descritas abaixo:

1. **Hill Climbing**:
* Começa com uma solução inicial e faz pequenas mudanças para tentar melhorar;
* Não permite retrocesso na busca
* Pode ser determinístico ou não-determinístico
    1. **Determinístico:**
    > Sempre faz a mesma escolha a cada iteração, avaliando a solução atual e as possíveis soluções disponísveis, se movendo para a melhor. Encerra quando encontra o ótimo local.
    2. **Não-determinístico:**
    > Possui um elemento de aleatoriedade na tomada de decisão. O algorítmo pode fazer escolhas probabilísticas ao invés de sempre escolher a melhor solução, permitindo que o algorítmo percorra mais do espaço de busca.

    > Isso evita a convergência prematura para ótimos locais para possivelmente encontrar soluções potencialmente melhores.
    
    > Usa o método da roleta¹ como aleatoriedade para escolha do próximo passo da iteração.
    
2. **Beam Search**:
* Busca em amplitude
* Limita o total de estados mantidos a *m* expansões do estados atuais
* Pode ser determinístico ou não-determinístico
    1. **Determinístico**:
    > Avalia todos os possíveis estados iniciais e adiciona os *m* melhores em uma fila *f*
    
    > Enquanto não achar a solução, continua a expandir os estados presentes na fila *f* e a avaliar cada um deles, mantendo na fila apenas os *m* melhores
    
    > Retorna o estado com a maior avaliação
    
    2. **Não-determinístico**:
    > Funciona de forma semelhando ao determinístico, mas usa a roleta¹ para escolher os *m* estados que serão mantidos em *f* a cada iteração até a solução ser completa.


### Soluções Completas

Trabalham com todo o espaço de busca avaliando as possíveis soluções, o vetor descritor de estados precisa estar totalmente preenchido.

Essas meta-heurísticas podem ser divididas em dois grupos: busca local e busca populacional.

1. **Busca Local**:
* Busca na vizinhança de uma ou mais soluções
* Obtem soluções de forma mais rápida
* Sua implementação é mais rápida
* Necessário o uso de métodos para fugir de vales ou picos, para não chegar a mínimos e máximos locais
* Faz saltos grandes na fase de diversificação
* Faz saltos pequenos na fase de intensificação
* O algorítmo geral funciona da seguinte forma:
  1. Gerar solução inicial
  2. Modificar levemente a solução
  3. Avaliar a nova solução
  4. Repetir *ii* e *iii* até que não encontre melhorias significativas
* São necessárias funções para:
  1. Gerar a solução inicial
  2. Determinar a vizinhança buscada
  3. Definir a função objetivo
* Os métodos de busca mais comuns são:
  1. **Gradiente de descida/subida:**
     > Usa a derivada da função objetivo para guiar a busca
     
     > Envolve atualização da solução seguindo a direção do gradiente para achar um ótimo local
  2. **Tabu Search:**
     > Permite movimento para uma solução pior
     
     > Evita revisitar soluções ao salvar soluções visitadas em um array tabu
     
     > Busca escapar de ótimos locais e explora melhor o espaço
  3. **Simulated Annealing:**
     > Analogia ao resfriamento de sólidos superaquecidos
     
     > Busca não determinística
     
     > Usa abordagem probabilística para aceitar soluções piores, aceitando mais soluções piores no início (fase de diversificação) e menos soluções piores no final (fase de intensificação)
     
     > Evita máximos locais ao permitir o movimento para soluções piores.
  4. **GRASP (Greedy Randomized Adaptive Search):**
     > Método iterativo probabilístico em que cada iteração obtem uma solução do problema em estudo
     
     > Cada iteração possui uma etapa construtiva (determina a solução que será submetida à busca), e uma etapa de busca (tenta obter melhoria na solução corrente)
     
     > Requer avaliação gulosa
     
     > Na fase de diversificação ocorrem várias iterações da etapa construtiva
     
     > Na fase de intensificação ocorre a etapa de busca

2. **Busca Populacional:**

* Baseada numa população inicial de soluções
* As soluções são combinadas para gerar nova população
* Usada em algorítmos evolutivos (genético) e de inteligência coletiva (colônia de formigas, enxame de partículas)

  1. **Algorítmo genético:**
     > Baseados na teoria de seleção natural e hereditariedade
     
     > Favorecem candidatos mais promissores para a solução de um dado problema
     
     > Seleção: faz com que, após muitas gerações, o conjunto inicial gere indivíduos mais aptos
     >  1. Seleção por roleta: aptdão define a fatia, valor aleatório seleciona o cromossomo (fatia), repete ate gerar *n* indivíduos necessários
     >  2. Seleção por torneio: escolhe aleatóriamente *m* indivíduos e escolhe o melhor com função de aptidão, repete o processo para os *n* indivíduos necessários
     >  3. Seleção por amostragem: método da rleta, mas com *n* agulhas espaçadas igualmente. A roleta é girada apenas uma vez para escolher os *n* indvíduos necessários
     
     > Operadores genéticos:
     >  1. Cruzamento: crossover dos pais para gerar os filhos
     >  2. Mutação
     
     > Elitismo: um percentual dos indivíduos com maior aptidão são mandados para a próxima geração independente do método de seleção usado

  2. **Colônia de formigas:**
     > Explora a auto-prganização das formigas para encontrar rotas otimizadas
     
     > O algoritmo se beneficia das interações entre as formigas e o uso do feromônio como forma de comunicação entre elas
     
     > Aplicado para o problema do caxeiro viajante
     
  3. **Enxame de partículas (PSO):**
     > Inspirada no comportamento de pássaros e peixes
     
     > Cada solução é uma partícula no espaço de busca, mantem múltiplas soluções promissoras rodando em paralelo
     
     > As partículas se movem no espaço buscando valor ótimo da função objetivo

---

## Referencias - Apoio

### ¹ Método da Roleta:

Usado para selecionar soluções candidatas com base na aptidão relativa. Possui os seguintes passos:
1. Avaliação da aptidão:
   > calcula a aptidão de cada solução candidata
2. Cálculo das probabilidades de seleção:
   > representa a porcentagem de chance de cada solução candidata ser selecionada
3. Construção da roleta:
   > constroi uma roleta fictícia, dividindo um círculo em setores com tamanho proporcional à probabilidade de cada solução candidata
4. Geração de um número aleatório:
   > gera um número aleatório entre 0 e 1 para escolher qual setor da roleta será selecionado
5. Seleção da solução:
   > percorre a roleta e seleciona a seção que engloba o número escolhido.

   > a solução escolhida avança para a próxima iteração
6. Repetição:
   > repete os passos 4 e 5 para as próximas iterações 


