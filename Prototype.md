# Abraão Sacaia - João José

O padrão de projeto `Prototype` pertence à categoria dos criacionais e possibilita a criação de novos objetos a partir de cópias de instâncias já existentes, evitando a dependência direta do código com as classes dessas instâncias.

## Problema

Vamos imaginar uma situação em que estamos desenvolvendo um sistema de e-commerce, e já existe uma classe chamada Produto que foi criada por outra equipe ou faz parte de uma biblioteca de terceiros. Essa classe tem métodos e propriedades básicas, mas queremos adicionar um comportamento extra que nos permita aplicar descontos em determinados produtos.

Neste caso, podemos usar o Prototype para estender a funcionalidade da classe Produto sem modificar o código original, o que nos permite manter a compatibilidade e facilidade de atualização.

