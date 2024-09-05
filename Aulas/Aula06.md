# Aula 6 - Estrutura de Classes e Instanciação de Objetos - Continuação Polimorfismo e Classes Abstratas

## Continuação Polimorfismo

### Polimorfismo em Tempo de Compilação (Sobrecarga):

Ocorre quando dois ou mais métodos têm o mesmo nome, mas diferentes parâmetros.

#### Classe Mensagem
``` Java
package mensageiro;

public class Mensagem {
    // Método para exibir uma mensagem de texto

    void exibir(String mensagem) {
        System.out.println("Mensagem: " + mensagem);
    }

    // Método para exibir um número inteiro
    void exibir(int numero) {
        System.out.println("Numero: " + numero);
    }

    // Método para exibir um array de inteiros
    void exibir(int[] numeros) {
        System.out.print("Numeros: ");
        for (int num : numeros) {
            System.out.print(num + " ");
        }
        System.out.println();
    }  
}
```
#### Principal
```Java

package mensageiro;

public class Principal {

    public static void main(String[] args) {
       Mensagem mensagem = new Mensagem();

        // Chamadas para os métodos sobrecarregados
        mensagem.exibir("Olá, Mundo!"); // Chama o método que exibe uma mensagem
        mensagem.exibir(42); // Chama o método que exibe um número inteiro
        mensagem.exibir(new int[]{1, 2, 3, 4, 5}); // Chama o método que exibe um array de inteiros
    }
    
}

```

### Análise do Código
- Classe Exibidor:
  - Tem três métodos chamados exibir, mas com diferentes assinaturas:
  - exibir(String mensagem): exibe uma mensagem de texto.
  - exibir(int numero): exibe um número inteiro.
  - exibir(int[] numeros): exibe um array de inteiros.
- Classe Main:
  - Cria uma instância da classe Exibidor.
  - Faz chamadas para os métodos exibir com diferentes tipos de argumentos, demonstrando a flexibilidade da sobrecarga de métodos.

## Classes Abstratas

- É uma classe que não pode ser instanciada diretamente. Ela pode conter métodos abstratos (sem implementação) e métodos concretos (com implementação).
Fornece uma base para outras classes que herdam dela, definindo um conjunto de métodos que as subclasses devem implementar.
- Permitem a criação de uma estrutura comum para um grupo de classes relacionadas, garantindo que certas funcionalidades sejam implementadas.
- São extremamente úteis em design de software, especialmente em padrões de projeto, onde a flexibilidade e a reutilização de código são essenciais.

### Características das Classes Abstratas
- Não Instanciáveis: Você não pode criar uma instância de uma classe abstrata. Isso significa que você não pode usar a palavra-chave new para criar um objeto dessa classe.
- Métodos Abstratos: Uma classe abstrata pode ter métodos abstratos, que são declarações de métodos sem corpo. As subclasses devem implementar esses métodos.
- Métodos Concretos: Além dos métodos abstratos, uma classe abstrata também pode ter métodos com implementação.
- Palavra-chave abstract: Para declarar uma classe ou um método como abstrato, usamos a palavra-chave abstract.

```Java
abstract class NomeDaClasse {
    // Atributos
    // Métodos concretos
    void metodoConcreto() {
        System.out.println("Este é um método concreto.");
    }

    // Método abstrato
    abstract void metodoAbstrato();
}
```
