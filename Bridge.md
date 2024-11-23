# Ebenezer & André
# Padrão de Projeto Bridge
### O que é?
O padrão de projeto Bridge é um padrão estrutural que tem como objetivo desacoplar uma abstração da sua implementação, de modo que ambas possam evoluir de forma independente. Em outras palavras, ele separa a interface (abstração) de um sistema da sua implementação, permitindo que você altere uma sem impactar a outra.
### Problema que o padrão de projeto objetiva resolver:
O padrão Bridge busca solucionar o problema de rigidez e acoplamento excessivo entre uma abstração e sua implementação. Frequentemente, ao utilizar herança para estender funcionalidades, criamos um vínculo permanente entre as classes abstratas e suas implementações concretas. Isso torna o sistema menos flexível, dificultando a extensão de funcionalidades ou a portabilidade para outras plataformas, especialmente quando há múltiplas implementações possíveis para a mesma abstração. Um exemplo típico é o desenvolvimento de interfaces gráficas que precisam ser compatíveis com diferentes sistemas de janelas (como XWindow e PMWindow). A abordagem convencional de herança resultaria em uma explosão combinatória de subclasses para suportar todas as variações necessárias.
### Solução proposta pelo Bridge:
O Bridge propõe separar uma abstração de suas implementações, permitindo que ambas possam variar de forma independente. Isso é alcançado dividindo a hierarquia de classes em duas partes: uma para a abstração e outra para a implementação. A classe abstrata mantém uma referência a um objeto que implementa a interface necessária, possibilitando que a implementação seja alterada em tempo de execução sem impactar a abstração. Assim, o padrão permite a combinação flexível de diferentes abstrações e implementações, aumentando a extensibilidade e portabilidade do sistema.



