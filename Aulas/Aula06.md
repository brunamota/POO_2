# Aula 6 - Estrutura de Classes e Instanciação de Objetos - Continuação Polimorfismo e Classes Abstratas

## Continuação Polimorfismo

Polimorfismo em Tempo de Compilação (Sobrecarga): Ocorre quando dois ou mais métodos têm o mesmo nome, mas diferentes parâmetros.

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
