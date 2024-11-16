# Abraão Sacaia - João José

## Prototype

O padrão de projeto `Prototype` pertence à categoria dos criacionais e possibilita a criação de novos objetos a partir de cópias de instâncias já existentes, evitando a dependência direta do código com as classes dessas instâncias. Assim como herança os objetos podem herdar propriedades ou métodos de outros objetos. O prototype permite mudar o comportamento de um objeto adicionando métodos ou propriedades sem a necessidade de alterar o objeto original.

No padrão Prototype, os objetos podem ser criados a partir da clonagem de outros já existentes, em vez de depender de hierarquias rígidas de classes. Essa abordagem é especialmente útil em linguagens como JavaScript, que privilegiam a composição em vez da herança.

![Imagem do WhatsApp de 2024-11-15 à(s) 20 41 06_09d691ca](https://github.com/user-attachments/assets/5d2f2755-ad48-4798-b7be-b7f743454671)

A herança segue uma estrutura hierárquica, onde subclasses derivam atributos e comportamentos das superclasses, criando um sistema fixo e bem estruturado. Já o modelo prototype estabelece relações diretamente entre objetos, permitindo a clonagem e personalização de forma dinâmica, sem depender de hierarquias rígidas. Enquanto a herança promove organização e estabilidade, o prototype oferece maior flexibilidade e capacidade de adaptação.

- **Herança:**  
  **Vantagem:** Facilita a reutilização de código, organiza os relacionamentos entre classes e possibilita o uso de polimorfismo.  
  **Desvantagem:** Eleva o nível de dependência entre as classes, impõe uma estrutura rígida e pode tornar a manutenção mais desafiadora.  

- **Prototype:**  
  **Vantagem:** Oferece alta flexibilidade, possibilita a clonagem de objetos de maneira eficiente e minimiza as dependências.  
  **Desvantagem:** Pode ser menos intuitivo de compreender, exige cuidado na manutenção e é mais propenso a problemas em tempo de execução.  

## Descrição do Problema

Vamos imaginar uma situação em que estamos desenvolvendo um sistema de e-commerce, e já existe uma classe chamada Produto que foi criada por outra equipe ou faz parte de uma biblioteca de terceiros. Essa classe tem métodos e propriedades básicas, mas queremos adicionar um comportamento extra que nos permita aplicar descontos em determinados produtos.

## Solução

Neste caso, podemos usar o Prototype para estender a funcionalidade da classe Produto sem modificar o código original, o que nos permite manter a compatibilidade e facilidade de atualização.

Incorporação de Funcionalidade: Um novo método, chamado aplicarDesconto, foi integrado ao protótipo de Produto, possibilitando que todas as instâncias da classe usufruam dessa funcionalidade.

Aproveitamento de Recursos: O método está acessível a todas as instâncias sem a necessidade de alterar a definição original da classe, promovendo eficiência e flexibilidade no uso.

## Código Fonte
`//Product prototypes
class Product {
    constructor(name: string, price: number, desc: string) {
        this.name = name;
        this.price = price;
        this.desc = desc;
    }
}


// Creating the new instance of product
const product_1 = new Product("Phone", 20, "Samsung");


// Adding a new method to our object:
Product.prototype.applyDiscount = function(discount: number) {
    const discountAmount: number = (this.price * discount) / 100;
    this.price -= discountAmount;
    return New price of ${this.name}: R$ ${this.price.toFixed(2)};
}



// Print the result
console.log(product_1.applyDiscount(10));`

