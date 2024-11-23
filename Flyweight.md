# Padrão de Projeto Flyweight

O padrão Flyweight é amplamente utilizado para minimizar o consumo de memória em sistemas que lidam com um grande número de objetos semelhantes. A ideia principal é compartilhar objetos idênticos ou muito semelhantes em vez de criar novas instâncias para cada uso. Essa abordagem é particularmente útil em situações onde objetos contêm informações repetidas que podem ser segregadas, reduzindo a redundância e otimizando o desempenho do sistema.  

De acordo com a definição apresentada na [Wikipédia](https://pt.wikipedia.org/wiki/Flyweight), o Flyweight segrega as informações repetidas em um objeto adicional que deve ser imutável e comparável. Por exemplo, em um processador de texto, os caracteres podem ser representados como objetos que compartilham propriedades como fonte e tamanho, reduzindo o consumo de memória.  

Além disso, como destacado na [DevMedia](https://www.devmedia.com.br/design-patterns-net-aplicando-os-padroes-flyweight-e-decorator/31387), o Flyweight é um padrão estrutural que se preocupa com a composição de classes e objetos para formar estruturas maiores e flexíveis. Ele utiliza técnicas como delegação e composição de objetos para permitir que os módulos sejam reutilizados de forma eficiente.  

O Flyweight também é uma solução eficaz para casos como jogos ou interfaces gráficas. Por exemplo, segundo o [Dev.to](https://dev.to/higordiego/padrao-flyweight-2n69), em jogos, personagens semelhantes na tela podem compartilhar objetos Flyweight para reduzir o uso de memória, assim como em interfaces gráficas onde controles similares, como botões, podem ser otimizados.  

O exemplo a seguir demonstra a implementação do padrão Flyweight, utilizando Python, com um sistema que gerencia árvores em um mapa de jogo:  

```python
import random
import matplotlib.pyplot as plt
import matplotlib.patches as patches
import sys
import gc
import time

class TreeType:
    """Representa o tipo de árvore (estado intrínseco) compartilhado por várias árvores."""
    def __init__(self, name, color, texture):
        self.name = name
        self.color = color
        self.texture = texture

    def __str__(self):
        return f"{self.name}, {self.color}, {self.texture}"

class Tree:
    """Representa uma árvore específica (estado extrínseco), com sua posição, que usa um TreeType compartilhado."""
    def __init__(self, x, y, tree_type):
        self.x = x
        self.y = y
        self.tree_type = tree_type

    def draw(self, ax):
        """Desenha a árvore na tela (representada por um círculo)."""
        ax.add_patch(patches.Circle((self.x, self.y), 0.2, color=self.tree_type.color))

class TreeFactory:
    """Fábrica para gerenciar os tipos de árvores compartilhados."""
    def __init__(self):
        self.tree_types = {}

    def get_tree_type(self, name, color, texture):
        """Retorna o TreeType, criando um novo se necessário."""
        key = (name, color, texture)
        if key not in self.tree_types:
            self.tree_types[key] = TreeType(name, color, texture)
        return self.tree_types[key]

# Função para medir o uso de memória antes e depois da criação
def measure_memory(func):
    def wrapper(*args, **kwargs):
        gc.collect()  # Limpa a memória antes da medição
        mem_before = sys.getsizeof(args[0])
        start_time = time.time()
        result = func(*args, **kwargs)
        mem_after = sys.getsizeof(args[0])
        elapsed_time = time.time() - start_time
        print(f"Tempo de execução: {elapsed_time:.4f} segundos")
        print(f"Uso de memória: {mem_after - mem_before} bytes")
        return result
    return wrapper

# Função para criar a floresta e desenhá-la
@measure_memory
def create_forest(num_trees):
    factory = TreeFactory()
    trees = []
    fig, ax = plt.subplots(figsize=(10, 10))
    ax.set_xlim(0, 10)
    ax.set_ylim(0, 10)

    for _ in range(num_trees):
        # Gerando dados aleatórios para a árvore
        name = random.choice(["Pine", "Oak", "Birch", "Maple"])
        color = random.choice(["green", "darkgreen", "yellowgreen"])
        texture = random.choice(["smooth", "rough"])
        x = random.uniform(0, 10)
        y = random.uniform(0, 10)

        # Criando ou reutilizando o TreeType
        tree_type = factory.get_tree_type(name, color, texture)

        # Criando a árvore e adicionando à lista
        tree = Tree(x, y, tree_type)
        trees.append(tree)
        tree.draw(ax)

    ax.set_aspect('equal', adjustable='box')
    ax.set_title(f"Floresta com {num_trees} Árvores")
    plt.show()

# Exemplo de execução
create_forest(200)  # Cria uma floresta com 200 árvores
