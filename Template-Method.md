# Template Method (Samuel && Gabriel)

### Definição 

O padrão de projeto Template Method é um padrão comportamental que define a estrutura básica de um algoritmo em uma classe abstrata, permitindo que as subclasses implementem detalhes específicos do algoritmo sem alterar sua estrutura geral. Este padrão é particularmente útil quando temos um algoritmo que deve ser executado em etapas bem definidas, mas algumas dessas etapas variam dependendo do contexto

### Diagrama De Classes
![241123_13h01m31s_screenshot](https://github.com/user-attachments/assets/e4660292-fb83-4bf0-98c4-49b1f03df997)
  
### Problema que o padrão objetiva resolver

O Template Method resolve vários problemas comuns no desenvolvimento de software:

* **Evitar duplicação de código:** Reutiliza a estrutura geral do algoritmo, evitando a repetição de código em diferentes partes do sistema.
* **Garantir consistência:** Assegura que diferentes implementações do algoritmo respeitem uma sequência lógica definida.
* **Facilitar a extensão do comportamento:** Permite adicionar novos comportamentos sem modificar o código existente, seguindo o princípio do Open/Closed.

### Solução

O padrão Template Method define um "esqueleto" do algoritmo em uma classe abstrata, com métodos concretos (que não mudam) e métodos abstratos ou hooks (que podem ser sobrescritos pelas subclasses). Assim, subclasses podem fornecer implementações específicas para algumas partes do algoritmo sem alterar sua estrutura global.

### Estrutura
A estrutura do Template Method envolve os seguintes componentes:

* **Classe Abstrata:** Define o método template que implementa o esqueleto do algoritmo. Este método chama métodos abstratos que devem ser implementados pelas subclasses.
* **Métodos Abstratos:** Definidos na classe abstrata, são implementados pelas subclasses para fornecer o comportamento específico.
* **Subclasses Concretas:** Implementam os métodos abstratos definidos na classe abstrata, fornecendo a funcionalidade específica.

### Exemplos de Código
![codeimage-snippet_23](https://github.com/user-attachments/assets/5c3b01ad-3841-4571-a0e0-530019f3b4c7)
***
![codeimage-snippet_23 (1)](https://github.com/user-attachments/assets/cd18668a-4af1-439c-aa71-c5e41d85a1c2)

### Vantagens do Padrão
* **Reutilização:** Reduz a duplicação de código para a lógica comum.
* **Extensibilidade:** Permite adicionar novos comportamentos sem alterar a estrutura existente.
* **Manutenção:** Simplifica o entendimento da lógica geral do algoritmo.

### Desvantagens

* **Complexidade:** Em projetos complexos, o número de métodos abstratos ou hooks pode aumentar, tornando difícil entender a hierarquia ou rastrear como partes do algoritmo são executadas.
* **Abuso do padrão:** Pode levar a hierarquias de classes profundas, dificultando a manutenção.

### Quando usar o Template Method

Quando várias classes precisam executar uma sequência fixa de operações, mas com implementações específicas para algumas etapas.  
Quando precisar adicionar novos comportamentos as subclasses sem alterar a classe base.

***
### Referências:
* [C# Design Pattern: Template Method](https://dev.to/develop4us/c-design-pattern-template-method-portugues-372e)
* [Template Method](https://refactoring.guru/pt-br/design-patterns/template-method)
* [Padrão de Projeto Template Method em Java](https://www.devmedia.com.br/padrao-de-projeto-template-method-em-java/26656)

