# Padrão de Projeto Factory
## Carol e Felipe
### Introdução
Esse padrão de criação de projeto propõem que uma classe abstrata ou uma interface crie de fato o objeto e será a subclasse que irá determinar qual classe concreta será instanciada. Ou seja é a interface que irá criar os objetos em uma superclasse mas quem irá alterar o tipo do objeto são as subclasses.
O proposto nesse padrão é esconder do solicitante a lógica de criação do objeto.
### Problema
Imagina-se a seguinte situação, um restaurante de comida mexicana inicia seu negócio com tacos e começa a crescer nos pedidos. Até que um dia o restaurante fica tão famoso que seus clientes começam a pedir por outro prato deles, nachos. 
Isso é interessante para o crescimento desse comércio. Mas como começar esse novo ramo de nachos sendo que todo o planejamento deles se baseou em servir apenas tacos. Isso exigiria uma mudança em toda a organização do restaurante. E se no futuro essa empresa conseguisse lidar com esse problema momentaneamente para uma receita nova, caso ela continue a crescer deveria passar por todo esse processo de remodelação novamente.
### Solução
Por meio do pensamento de padrão de projeto Factory, propõem-se:
- A crição de uma **interface comum** para os pratos: como a superclasse "Pratos mexicanos" que define métodos comuns a todos os pratos.
- Implementação de pratos específicos: cada prato tem sua receita específica e seu próprio conjunto de instruções sobre como seguir a sua criação.
- Fábrica de pratos: cria-se uma fábrica de pratos solicitados, seja taco ou nacho que irá receber o pedido e criá-lo conforme sua receita.
- Uso da fábrica: No cotidiano do restaurante, eles irão preparam as comidas conforme o pedido dos clientes se moldando na receita específica hora taco, hora nachos.

Sendo assim, apresenta-se o ideia de existir um método fábrica que realizará a criação de novos pratos ao menu, como burritos ou quesadillas, sem a necessidade de reestruturar o processo do restaurante. Isso é possível por meio de um planejamento mais genérico do negócio no ramo de comidas mexicanas e com seus pratos, como uma grande fábrica. Assim, a ampliação do menu torna-se mais fácil e flexível.
Logo, o padrão Factory visa solucionar o problema de crescimento e diversificação do menu do restaurante, proporcionando uma maneira organizada e escalável de gerenciar a criação e adição de novos pratos ao menu.

