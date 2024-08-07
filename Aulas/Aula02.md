# Aula 2 - Introdução à Orientação à Objetos – Conceitos Gerais

### Abstração

![cachorros](https://github.com/user-attachments/assets/79f1bf70-c3c0-4f86-bfa7-8cc66632aa7c)

O que Tobias e Jeremias são?

  - Cachorros

Quais as caracteristicas de um cachorro?

  - Nome
  - Raça
  - Sono
  - Alimentação
  - Exercício
    
Quais comportamentos/ações que o cachorro pode ter?

  - Comer
  - Dormir
  - Passear
    
Então, temos que cada cachorro:

- Cachorro 1:
  - Nome: Tobias
  - Raça: Pug
  - Sono: não
  - Alimentação: come 2 vezes no dia
  - Exercíco: passeia 1 vez no dia
    
- Cachorro 2:
  - Nome: Jeremias
  - Raça: Golden
  - Sono: não
  - Alimentação: come 3 vezes no dia
  - Exercíco: passeia 2 vezes no dia

Passando isso para a Orientação Objeto:
  - Classe: Cachorro
  - Atributos:
    - Nome
    - Raça
    - Sono
    - Alimentação
    - Exercício
  - Métodos:
    - Comer
    - Dormir
    - Passear
    
Passando isso para o java:

Classe Cachorro
```Java
package cachorro;

public class Cachorro {
    //atributos
    String nome;
    String raca;
    Boolean sono;
    int alimentacao;
    int exercicio;
    
    //Contrutor nulo
    Cachorro(){
        
    }
    
    //Construtor com parâmetros
    Cachorro(String nome, String raca, Boolean sono, int alimentacao, int exercicio){
        this.nome = nome;
        this.raca = raca;
        this.sono = sono;
        this.alimentacao = alimentacao;
        this.exercicio = exercicio;
    }
    
    //Metodos
    public Boolean dormir(){
        sono = true;
        return sono;
    }
    
    public int comer(int alimentacao){
        this.alimentacao = this.alimentacao - alimentacao;
        return this.alimentacao;
    }
    
    public int passear(int exercicio){
        this.exercicio = this.exercicio - exercicio;
        return this.exercicio;
    }

    //Assinatura do Objeto
    @Override
    public String toString() {
        return "Cachorro:" + 
                "\nNome = " + nome +
                "\nRaca = " + raca +
                "\nSono = " + sono +
                "\nAlimentacao = " + alimentacao +
                "\nExercicio = " + exercicio;
    }
    
}

```
Classe Principal
```Java
package cachorro;

public class Principal {
        public static void main(String[] args) {
           
           //Instanciar um objeto
           Cachorro cachorro1 = new Cachorro("Tobias", "Pug", false, 2, 1);
           Cachorro cachorro2 = new Cachorro("Jeremias", "Golden", false, 3, 2);
      
           System.out.println(cachorro1);
           System.out.println(cachorro2);
           
           //chamar métodos
           cachorro1.passear(1);
           cachorro1.dormir();
           cachorro2.comer(1);
           
           System.out.println(cachorro1);
           System.out.println(cachorro2);
    }
   
 }
```
