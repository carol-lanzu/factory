# Template Method (Samuel && Gabriel)

### Definição 

O padrão de projeto **Template Method** é um padrão _comportamental_  
que define a estrutura básica de um algoritmo em uma classe abstrata,  
permitindo que as subclasses implementem detalhes específicos do algoritmo   
sem alterar sua estrutura geral.

### Problema que o padrão objetiva resolver

Quando temos um algoritmo que deve ser executado em etapas bem definidas, mas algumas dessas etapas variam dependendo do contexto, o padrão Template Method resolve o problema de:
* **Evitar duplicação de código** ao reutilizar a estrutura geral do algoritmo.
* **Garantir consistência** ao executar o algoritmo, permitindo que diferentes implementações respeitem uma sequência lógica definida.
* **Facilitar a extensão do comportamento** sem modificar o código existente (princípio do Open/Closed).

### Solução

O padrão Template Method define um "esqueleto" do algoritmo em uma classe abstrata, com métodos concretos (que não mudam) e métodos abstratos ou hooks (que podem ser sobrescritos pelas subclasses). Assim, subclasses podem fornecer implementações específicas para algumas partes do algoritmo sem alterar sua estrutura global.

### Exemplos de Código
![codeimage-snippet_23](https://github.com/user-attachments/assets/5c3b01ad-3841-4571-a0e0-530019f3b4c7)
***
![codeimage-snippet_23 (1)](https://github.com/user-attachments/assets/cd18668a-4af1-439c-aa71-c5e41d85a1c2)

### Vantagens do padrão

* Reutilização: Reduz duplicação de código para a lógica comum.
* Extensibilidade: Permite adicionar novos comportamentos sem alterar a estrutura existente.
* Manutenção: Simplifica o entendimento da lógica geral do algoritmo.

### Facilidade de implementação e entendimento
Nível de dificuldade: Fácil a médio.
O padrão Template Method é considerado relativamente fácil de implementar e entender, especialmente para programadores que já têm experiência com:
Polimorfismo.
Herança (ou composição, em linguagens mais modernas).
Por que é fácil?
O conceito é direto: separar o que é comum (na superclasse) do que varia (nas subclasses).
Ajuda a evitar a duplicação de código, organizando o comportamento de forma clara e legível.
É amplamente suportado por todas as linguagens orientadas a objetos.
Por que pode ser difícil?
Em projetos complexos, o número de métodos abstratos ou hooks pode aumentar, tornando difícil entender a hierarquia ou rastrear como partes do algoritmo são executadas.
O abuso do padrão pode levar a hierarquias de classes profundas, dificultando a manutenção.

### Quando usar o Template Method

Consistência: Quando várias classes precisam executar uma sequência fixa de operações, mas com implementações específicas para algumas etapas.
Evitar duplicação de código: Reduz a duplicação em situações em que o fluxo geral é sempre o mesmo, mas com variações específicas.
Facilidade para adicionar novos comportamentos: Adicionar novas subclasses para customizar etapas sem alterar a classe base.