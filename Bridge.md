# Ebenezer & André
# Padrão de Projeto Bridge
### O que é Bridge?
O padrão de projeto Bridge é um padrão estrutural que tem como objetivo desacoplar uma abstração da sua implementação, de modo que ambas possam evoluir de forma independente. Em outras palavras, ele separa a interface (abstração) de um sistema da sua implementação, permitindo que você altere uma sem impactar a outra.
### Problema que o padrão de projeto objetiva resolver:
O padrão Bridge busca solucionar o problema de rigidez e acoplamento excessivo entre uma abstração e sua implementação. Frequentemente, ao utilizar herança para estender funcionalidades, criamos um vínculo permanente entre as classes abstratas e suas implementações concretas. Isso torna o sistema menos flexível, dificultando a extensão de funcionalidades ou a portabilidade para outras plataformas, especialmente quando há múltiplas implementações possíveis para a mesma abstração. Um exemplo típico é o desenvolvimento de interfaces gráficas que precisam ser compatíveis com diferentes sistemas de janelas (como XWindow e PMWindow). A abordagem convencional de herança resultaria em uma explosão combinatória de subclasses para suportar todas as variações necessárias.
### Solução proposta pelo Bridge:
O Bridge propõe separar uma abstração de suas implementações, permitindo que ambas possam variar de forma independente. Isso é alcançado dividindo a hierarquia de classes em duas partes: uma para a abstração e outra para a implementação. A classe abstrata mantém uma referência a um objeto que implementa a interface necessária, possibilitando que a implementação seja alterada em tempo de execução sem impactar a abstração. Assim, o padrão permite a combinação flexível de diferentes abstrações e implementações, aumentando a extensibilidade e portabilidade do sistema.
### Exemplo de um código Fonte que desenhar Formas em Diferentes APIs Gráficas:
Interface Implementor 

      class Renderer {
       public:
        virtual void drawCircle(float x, float y, float radius) = 0;
        virtual ~Renderer() = default;
      };
 Implementação concreta para SVG 

        class SVGRenderer : public Renderer {
         public:
          void drawCircle(float x, float y, float radius) override {
          std::cout << "Desenhando círculo em SVG no centro (" << x << ", " << y << ") com raio " << radius << ".\n";
          }
        };

        // Implementação concreta para Canvas
       class CanvasRenderer : public Renderer {
        public:
        void drawCircle(float x, float y, float radius) override {
        std::cout << "Desenhando círculo em Canvas no centro (" << x << ", " << y << ") com raio " << radius << ".\n";
        }
       };
Abstração 


       class Shape {
        protected:
         Renderer* renderer;
        public:
         Shape(Renderer* r) : renderer(r) {}
         virtual void draw() = 0;
       };

       // Abstração refinada
       class Circle : public Shape {
       private:
        float x, y, radius;
       public:
        Circle(Renderer* r, float x, float y, float radius) 
        : Shape(r), x(x), y(y), radius(radius) {}
    
       void draw() override {
       renderer->drawCircle(x, y, radius);
       }
      };
Uso do padrão Bridge 


       int main() {
       SVGRenderer svg;
       CanvasRenderer canvas;
    
       Circle svgCircle(&svg, 10, 10, 5);
       Circle canvasCircle(&canvas, 20, 20, 10);
    
       svgCircle.draw();       // Desenha usando SVG
       canvasCircle.draw();    // Desenha usando Canvas
    
       return 0;
      }
Saída Esperada 

      Desenhando círculo em SVG no centro (10, 10) com raio 5.
      Desenhando círculo em Canvas no centro (20, 20) com raio 10.

## Explicação do Código
### Interface Implementor
Define a interface abstrata que descreve como a implementação de renderização deve funcionar.
Possui um método virtual puro (drawCircle) que força as classes derivadas a implementarem sua lógica específica de renderização. A interface implementor abstrai detalhes de como as formas geométricas serão renderizadas.
### Implementações Concretas
SVGRenderer e CanvasRenderer: São implementações concretas da interface Renderer. Cada classe fornece uma lógica específica para renderizar círculos em um formato particular (SVG ou Canvas). Estas classes encapsulam os detalhes de renderização e permitem que novas plataformas de renderização sejam adicionadas facilmente.
### Abstração
A classe base abstrata Shape define a interface comum para todas as formas geométricas.
Contém uma referência a um objeto Renderer, que será usado para delegar a lógica de renderização. A abstração não se preocupa com detalhes de implementação, apenas com o que precisa ser feito (exemplo: desenhar uma forma).
### Abstração Refinada
Circle é uma implementação concreta de Shape que fornece a lógica específica para uma forma geométrica (um círculo).
Mantém atributos específicos da forma (posição e tamanho do círculo) e utiliza a referência ao Renderer para delegar a renderização. As formas geométricas são separadas das plataformas de renderização, promovendo flexibilidade e reutilização.
###  Uso no main
Implementadores são criados: SVGRenderer e CanvasRenderer são instâncias de plataformas de renderização.
Formas são criadas através de Circle que é instanciado e configurado para usar uma plataforma de renderização específica.
Delegação de renderização é feita quando draw é chamado em Circle, a lógica de renderização é delegada ao implementador correspondente. A combinação de diferentes formas geométricas com diferentes plataformas de renderização é feita sem modificar nenhuma classe existente.

## Diagrama de Classes
Imagem de estrutura do padrão bridge:

![Bridge](https://github.com/user-attachments/assets/0595fb50-758d-48bf-b28e-130eca8ed8ad)

#### Abstraction: 
Define a interface de alto nível e mantém uma referência ao objeto Implementor.
#### RefinedAbstraction: 
Extende a Abstraction e implementa detalhes adicionais.
#### Implementor: 
Define a interface para todas as implementações.
#### ConcreteImplementor: 
Implementa a interface Implementor.
## Conclusão

O código implementa o padrão de projeto Bridge de forma clara e eficiente, demonstrando sua capacidade de desacoplar abstrações de implementações. Esse desacoplamento permite que ambas evoluam de forma independente, resultando em um sistema mais flexível, extensível e fácil de manter.


Através da separação entre formas geométricas (abstração) e plataformas de renderização (implementação), o código evita a explosão combinatória de subclasses que poderia ocorrer com uma abordagem baseada apenas em herança. Além disso, o uso de delegação garante que as abstrações (como Circle) não dependam diretamente das implementações concretas (SVGRenderer, CanvasRenderer), promovendo modularidade. Essa flexibilidade faz do Bridge uma solução ideal para sistemas que precisam combinar múltiplas abstrações e implementações, mantendo o código limpo, reutilizável e preparado para mudanças futuras.
## Referências

Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides. Padrão do projeto “Soluções reutilizáveis de software orientado a objetos”. 2007

[Link do texto de apoio](https://refactoring.guru/pt-br/design-patterns/bridge)
