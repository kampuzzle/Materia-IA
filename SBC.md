# Sistemas Baseados em Conhecimento

Programa computacional inteligente que usa conhecimento representado explicitamente para resolver problemas, capaz de interpretar o conhecimento e realizar inferências automaticamente

Normalmente requer uma grande quantidade de conhecimento especializado

---

## Sistemas especialistas

* Sistemas de inteligência artificial que emulam a expertise e o conhecimento de um especialista humano em um domínio específico.
* Separação explícita do conhecimento da forma de inferência
* Idéia era “extrair” o conhecimento dos especialistas e codificá-lo em uma linguagem de representação
* É necessária a formulação do conhecimento
  1. Extração de conhecimento especialista não é possível;
  2. Uso de fontes de conhecimento: anotações, livros, etc;
  3. Necessário senso comum aliado ao conhecimento especializado.
 
---

## Arquitetura

Dividido em módulos básicos, complementares e núcleo
1. Básicos:
   * **Base de conhecimento:** onde o conhecimento especializado é armazenado. A base de conhecimento contém regras, fatos, heurísticas e outras formas de representação do conhecimento. Pode ser representada em formato de banco de dados, ontologias ou estruturas de dados específicas para a representação do conhecimento.
   * **Mecanismo de inferência:** responsável por processar a base de conhecimento e realizar inferências lógicas. Ele aplica as regras e o conhecimento armazenado para chegar a conclusões e tomar decisões.
2. Complementares:
   * **Memória de Trabalho:** área temporária de armazenamento para processamento e raciocínio durante a execução do sistema. A memória de trabalho contém informações relevantes e contextuais sobre o problema em questão, bem como dados intermediários gerados durante o processo de inferência. Esses dados são atualizados e modificados à medida que o sistema faz deduções e toma decisões.
   * **Explicação:** fornece justificativas, raciocínio e evidências sobre como uma resposta ou conclusão foi alcançada. Isso ajuda os usuários a entenderem o processo de tomada de decisão do sistema e a confiarem nas respostas fornecidas.
   * **Aquisição de Conhecimento:** processo de obtenção, formalização e incorporação de conhecimento especializado no sistema baseado em conhecimento. Esse processo envolve interação com especialistas humanos, análise de documentos, consulta a bases de dados e outras fontes relevantes de conhecimento.
   * **Interface com Usuário:** meio pelo qual os usuários interagem com o sistema baseado em conhecimento. Ela permite a entrada de consultas, dados e informações relevantes para o sistema, bem como a apresentação dos resultados, respostas e recomendações geradas pelo sistema.
3. Shell ou Núcleo:
   * SBC com facilidade para substituição da base de conhecimento

---

## Representação do conhecimento

1. **Redes Semânticas:** representam o conhecimento através de nós e arestas, onde os nós representam conceitos ou entidades, e as arestas representam as relações entre eles. Essa forma de representação é útil para representar hierarquias, classificações e relacionamentos entre conceitos.

2. **Lógica:** uso de sentenças lógicas. A lógica de predicados e a lógica de primeira ordem são comumente utilizadas para representar relações entre objetos e propriedades. A lógica permite o uso de regras de inferência e raciocínio lógico para derivar novas informações.

3. **Regras de Produção:** estruturadas em formato "se...então..." e descrevem condições (antecedentes) que, quando satisfeitas, levam a ações ou conclusões (consequentes). As regras de produção são eficazes para capturar conhecimento heurístico e tomada de decisão.

4. **Frames:** organiza as informações em estruturas de dados hierárquicas. Eles consistem em um conjunto de atributos e valores associados a um conceito ou objeto. Os frames permitem representar o conhecimento de forma estruturada e facilitam a recuperação e manipulação de informações.

5. **Regras de Produção com Objetos:** estendem as regras de produção tradicionais para lidar com objetos complexos e estruturados. Elas permitem representar conhecimento sobre objetos e suas propriedades, além de permitir a aplicação de operações e inferências sobre esses objetos.

Numa visão ideal, a base de conhecimento contém descrição do que é o problema (conhecimento declarativo) e a máquina de inferência sabe como o problema deve ser resolvido (conhecimento procedimental).

Na realidade: 
* Máquinas de inferência frequentemente usam procedimento exaustivo para varrer espaço de problema (busca em profundidade);
* Conhecimento declarativo parece não ser muito apropriado para descrição de processos, uma vez que se concentra mais em descrever fatos, conceitos e relacionamentos entre eles, em vez de detalhar a sequência de ações ou etapas específicas de um processo.
* Base de conhecimento também precisa conter conhecimento procedimental (execução de cálculos, conhecimentos específicos do domínio).

Atualmente, é considerado importante que a base tenha 3 tipos de conhecimento:
1. Domínio
   * Conceitos e relações
2. Tarefa
   * Natureza da classe de problemas a ser resolvido
3. Método de resolução
   * Procedimento a ser usado para resolver o problema

---

## Inferência

### Encadeamento para frente (Foward Chaining)

No encadeamento para frente, o sistema começa com os fatos conhecidos ou dados de entrada e, em seguida, aplica as regras de inferência para gerar novas informações e chegar a conclusões. Ele continua avançando na cadeia de inferência até que não seja possível derivar mais informações ou até que um objetivo específico seja alcançado. Essa estratégia é frequentemente usada quando se deseja descobrir respostas a partir dos dados disponíveis.

### Encadeamento para trás (Backward Chaining)

No encadeamento para trás, o sistema começa com um objetivo específico a ser alcançado e, em seguida, trabalha retroativamente para encontrar os fatos ou regras que suportam esse objetivo. Ele verifica as regras de inferência de forma regressiva, tentando provar a hipótese inicial ou atingir o objetivo desejado. Essa estratégia é frequentemente usada quando se deseja encontrar as evidências que suportam uma determinada conclusão ou objetivo. Usado no PROLOG.

---

## Aquisição de conhecimento

* Processo de obtenção e incorporação de conhecimento especializado em um sistema baseado em conhecimento. Envolve a captura, formalização e organização do conhecimento humano ou do domínio específico de aplicação, de modo que possa ser utilizado pelo sistema para realizar tarefas de tomada de decisão, raciocínio e solução de problemas.

* **Elicitação:** processo de extrair conhecimento tácito e especializado de especialistas humanos, por meio de técnicas de entrevistas, workshops, questionários ou outras formas de interação. O objetivo da eliciação é fazer com que os especialistas expressem seu conhecimento de forma explícita e compreensível, para que possa ser capturado e incorporado ao sistema. A eliciação de conhecimento é especialmente útil quando o conhecimento está enraizado na experiência prática dos especialistas e é difícil de ser formalizado.

* **Aquisição:** processo de obter conhecimento formalizado, seja por meio de análise de documentos, revisão de literatura, mineração de dados, aprendizado de máquina ou outros métodos. O objetivo da aquisição de conhecimento é capturar o conhecimento de uma forma que possa ser representada e utilizada pelo sistema.

* **Complexidade e desafios:**
  1. Necessidade de representar separadamente o conhecimento do domínio e o conhecimento de como processar eficientemente a base de conhecimento;
  2. Processo de aquisição/elicitação de conhecimento é extremamente complexo – considerado o gargalo na construção de SBCs;
  3. Verbalização do conhecimento tácito e esquecido é um desafio;
  4. Como saber que o sistema está correto;
  5. Necessidade de ajuste frequente da base.

---

## Explicação

* **Convencimento do usuário:** a SBC nem sempre acerta, mostrar a explicação de como ela chegou à conclusão pode ajudar a convencer o usuário a confiar na solução;
* **Aprendizagem:** A SBC pode servir como tutorial de aprendizagem;
* **Documentação:** A SBC possui memória das justificativas das decisões, o que pode ajudar na correção de erros, questões judiciais e na melhoria de novas resoluções
* **Tipos:**
  1. *O que é?* — Explica o que é determinado conceito, relação, atributo ou instância
  2. *Porque?* — Justifica porque uma alternativa foi escolhida baseada na análise de restrições e critérios
  3. *Como? — Apresenta a sequência de decisões que levaram a escolha de uma alternativa
  4. *Porque não?* — Justifica porque uma alternativa não foi escolhida
  5. *O que acontece se?* — Apresenta o impacto que uma escolha diferenciada podem produzir

 ---

 ## Resumos dos desafios da SBC

 * Gargalo da aquisição de conhecimento
 * Fragilidade dos SBCs:
   1. Conhecimento de heurísticas é superficial e pode gerar resultados imprevisíveis, às vezes, absurdos
   2. Como incorporar e usar senso comum
   3. Como modelar e tratar o conhecimento profundo através de princípios básicos do domínio
