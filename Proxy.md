## Alexis e Pedro Henrique - Proxy

# Proxy

### O que é o Proxy?

O Proxy é um padrão de projeto estrutural que atua como um intermediário ou substituto para outro objeto. Ele oferece uma camada adicional de controle, permitindo gerenciar o acesso ao objeto real (chamado de RealSubject). O Proxy é usado para adicionar comportamentos ou condições sem alterar o código do objeto real.

###Problemas que o padrao de projeto Proxy resolve:
O padrão de projeto Proxy resolve problemas como controle de acesso, desempenho e monitoramento, atuando como uma camada intermediária entre o cliente e o objeto real. Ele é útil para restringir acessos (Protection Proxy), como em sistemas que permitem apenas administradores visualizar relatórios confidenciais, ou para carregar recursos sob demanda (Virtual Proxy), adiando a criação de objetos pesados até serem necessários, como imagens em uma interface gráfica.

Além disso, o Proxy pode armazenar em cache resultados para evitar recalcular ou recarregar objetos, e pode registrar atividades para auditoria ou monitoramento de desempenho. Em sistemas distribuídos, ele facilita a comunicação remota (Remote Proxy), escondendo a complexidade de conexões de rede.

### Problema: 
Você precisa implementar objetos que precisam de muitos recursos, mas você não quer instanciar tais objetos a menos/até que eles sejam requisitados pelo cliente.

### Descrição da resolução:
Desenvolver um substituto, ou proxy, objeto que: instancia o objeto real na primeira vez que o cliente faz uma solicitação de proxy, lembra a identidade desse objeto real, e então redireciona a requisição para o objeto real. Então todas as requisições subsequentes são simplesmente redirecionadas diretamente para o objeto real encapsulado.

### Código Fonte:
Image

     public interface Image{
        void display(); 
      }
Real Image

     public class RealImage implements Image {  
       private String fileName;
       public RealImage(String fileName){
          this.fileName = fileName;
          loadFromDisk(fileName);
       }
       @Override
       public void display() {
          System.out.println("Displaying " + fileName);
       }
       private void loadFromDisk(String fileName){
          System.out.println("Loading " + fileName);
       }
     }
Proxy Image


     public class ProxyImage implements Image{
       private RealImage realImage;
       private String fileName;
       public ProxyImage(String fileName){
          this.fileName = fileName;
       }
       @Override
       public void display() {
          if(realImage == null){
             realImage = new RealImage(fileName);
          }
          realImage.display();
       }
     }
Proxy Pattern


     public class ProxyPatternDemo {
       public static void main(String args) {
          Image image = new ProxyImage("test_10mb.jpg");
          //image will be loaded from disk
          image.display();
          System.out.println("");
          //image will not be loaded from disk
          image.display();
       }
     }
### Diagrama de Classes
![](https://upload.wikimedia.org/wikipedia/commons/b/bc/Proxy.png)