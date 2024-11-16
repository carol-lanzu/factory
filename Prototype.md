# Abraão Sacaia - João José

## Prototype

O padrão de projeto `Prototype` pertence à categoria dos criacionais e possibilita a criação de novos objetos a partir de cópias de instâncias já existentes, evitando a dependência direta do código com as classes dessas instâncias. Assim como herança os objetos podem herdar propriedades ou métodos de outros objetos. O prototype permite mudar o comportamento de um objeto adicionando métodos ou propriedades sem a necessidade de alterar o objeto original.

No padrão Prototype, os objetos podem ser criados a partir da clonagem de outros já existentes, em vez de depender de hierarquias rígidas de classes. Essa abordagem é especialmente útil em linguagens como JavaScript, que privilegiam a composição em vez da herança.

As abordagens e implementação do padrão prototype podem as vezes ser diferentes em cada linguagens de programação, mas os conceitos acabam sendo os mesmos. Neste contexto vamos abordar o conceito de padrão Prototype em Javascript.

![Imagem do WhatsApp de 2024-11-15 à(s) 20 41 06_09d691ca](https://github.com/user-attachments/assets/5d2f2755-ad48-4798-b7be-b7f743454671)

`[[prototype]]` em javascript, objetos têm uma propriedade oculta especial [[prototype]] que é _null_ ou faz referência a outro objeto que é chamado de objeto.

O diagrama da imagem mostra que a `Base prototype` é o protótipo para as classes `class_1` e `class_2` onde herdam os métodos ou propriedades. Se desejamos reutilizar o que temos em `Base prototype` não copiar/reimplementar seus métodos, apenas construir um novo objeto em cima dele, essa abordagem é conhecida como **Herança Protótipa**.

Isso pode até parecer que estamos falando de herança em POO, apesar de o padrão prototype os objetos herdarem comportamentos da Base prototype. Embora os conceitos são parecidos eles tem propósitos distintos e implementações diferentes.
 
Por exemplo a herança segue uma estrutura hierárquica, onde subclasses derivam atributos e comportamentos das superclasses, criando um sistema fixo e bem estruturado. Já o modelo prototype estabelece relações diretamente entre objetos, permitindo a clonagem e personalização de forma dinâmica, sem depender de hierarquias rígidas. Ambas as abordagens podem ser implementadas no mesmo projeto, porém devem ser usadas conforme o objetivo: `Prototype` _para customizações rápidas_ enquanto `herança` _para estruturas mais formais e reutilizáveis_.

## Descrição do Problema

Para aplicarmos o conceito de prototype vamos simular uma situação em que estamos desenvolvendo um sistema de e-commerce, e já existe uma classe chamada Produto que foi criada por outra equipe ou faz parte de uma biblioteca de terceiros. Essa classe tem métodos e propriedades básicas, mas queremos adicionar um comportamento extra que nos permita aplicar descontos em determinados produtos.

## Solução

Neste caso, podemos usar o Prototype para estender a funcionalidade da classe Produto sem modificar o código original, o que nos permite manter a compatibilidade e facilidade de atualização.

Adicionamos um novo método, chamado `aplyDiscount`, foi integrado ao protótipo de Produto, possibilitando que todas as instâncias da classe usufruam dessa funcionalidade, para adicionarmos esse método basta utilizarmos a propriedade `Product.prototype.<Nome do metodo ou Propriedade>` com isso criamos a função que calcula os descontos dos produtos.

Aproveitamento de Recursos: O método está acessível a todas as instâncias sem a necessidade de alterar a definição original da classe, promovendo eficiência e flexibilidade no uso.

## Código Fonte
```ts
//============== PRODUCT OBJECT ==========================

//Product prototypes
class Product {
    constructor(name: string, price: number, desc: string) {
        this.name = name;
        this.price = price;
        this.desc = desc;
    }
}


//============== PRODUCT PROTOTYPE ==========================

// Adding a new method to our object:
Product.prototype.applyDiscount = function(discount: number) {
    const discountAmount: number = (this.price * discount) / 100;
    this.price -= discountAmount;
    return New price of ${this.name}: R$ ${this.price.toFixed(2)};
}



//============== CLIENT ==========================

// Creating the new instance of product
const product_1 = new Product("Phone", 2000, "Samsung");
console.log(product_1.applyDiscount(10));
; 
```

![Imagem do WhatsApp de 2024-11-15 à(s) 22 35 32_279165ed](https://github.com/user-attachments/assets/31e3fc96-669a-4b5e-abe3-d08c0af7696d)

### Entendendo o código:

* Primeiro criamos a Classe Product: É a base para criar produtos com propriedades name, price, e desc.
* Protótipo e Herança: O método applyDiscount é adicionado ao protótipo de Product, de forma que todas as instâncias podem acessá-lo. Isso segue o conceito de herança prototípica em JavaScript, onde objetos podem herdar propriedades e métodos de outros objetos.
* Funcionalidade Adicional: O método applyDiscount adiciona uma funcionalidade que modifica o preço da instância com base no percentual de desconto fornecido.

* `const product_1 = new Product("Phone", 2000, "Samsung")` criamos uma instância do Produto e `console.log(product_1.applyDiscount(10))` executamos o método aplyDiscount e passando o parâmetro.

## Resumo 

O padrão Prototype é um conceito criacional que permite criar novos objetos a partir de clones de instâncias existentes, promovendo flexibilidade e reutilização. Em JavaScript, o método prototípico foi usado para adicionar dinamicamente o método `applyDiscount` à classe `Product`, permitindo modificar o preço de produtos sem alterar a classe original. Essa abordagem facilita personalizações rápidas e manutenção do código.
