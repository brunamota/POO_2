# Aula 5 - Estrutura de Classes e Instanciação de Objetos - Herança e Polimorfismo

## 👨‍👩‍👧 Herança

- É um mecanismo que permite que uma classe (subclasse) herde atributos e métodos de outra classe (superclasse).
- Facilita a reutilização de código e a criação de hierarquias de classes.
- Como exemplo, vamos criar a Superclasse/Classe Mãe Animais:

``` Java
package animais;

public class Animais {
    
    protected String nomeAnimal;
    protected String raca;
    protected String nomeDono;

    public Animais(String nomeAnimal, String raca, String nomeDono) {
        this.nomeAnimal = nomeAnimal;
        this.raca = raca;
        this.nomeDono = nomeDono;
    }

    public String getNomeAnimal() {
        return nomeAnimal;
    }

    public String getRaca() {
        return raca;
    }

    public String getNomeDono() {
        return nomeDono;
    }


    public void setNomeAnimal(String nomeAnimal) {
        this.nomeAnimal = nomeAnimal;
    }

    public void setRaca(String raca) {
        this.raca = raca;
    }

    public void setNomeDono(String nomeDono) {
        this.nomeDono = nomeDono;
    }

     // Método da classe Animal
    public void fazerSom() {
        System.out.println(nomeAnimal + " faz um som.");
    }

    @Override
    public String toString() {
        return "Animais{" + "nomeAnimal=" + nomeAnimal +
                "\nRaca=" + raca +
                "\nnomeDono=" + nomeDono + '}';
    }
    
}

```
- Então, criamos a subclasse Cachorro que herdará as caracteristicas de animais
- A palavra-chave extends é utilizada para definir uma subclasse.

``` Java
public class Cachorro extends Animais{
      
}
```

- A subclasse herda todos os métodos e atributos da superclasse, exceto os membros privados, utilizamos a palavra chave super para que isso aconteça.
- Uma subclasse pode ter seus próprios métodos e atributos adicionais.
- É possível sobrescrever métodos da superclasse para fornecer implementações específicas.

``` Java
public class Cachorro extends Animais{
    
    private int idadeCachorro;

    public Cachorro(String nomeAnimal, String raca, String nomeDono, int idadeCachorro) {
        super(nomeAnimal, raca, nomeDono);
        this.idadeCachorro = idadeCachorro;
    }

    public int getIdadeCachorro() {
        return idadeCachorro;
    }

    public void setIdadeCachorro(int idadeCachorro) {
        this.idadeCachorro = idadeCachorro;
    }

    public void fazerSom(){
            System.out.println(super.nomeAnimal + " late.");
    }
  
}
```

## 👥 Polimorfismo 

- É a capacidade de um objeto assumir diferentes formas. Em termos de orientação a objetos, isso geralmente se refere à habilidade de métodos com o mesmo nome se comportarem de maneira diferente, dependendo do objeto que os invoca.
- Permite que métodos com o mesmo nome se comportem de maneiras diferentes, dependendo do objeto que os invoca. Isso promove flexibilidade e reutilização de código.
- Facilita a expansão e manutenção do código.
- Permite que métodos sejam escritos de forma mais genérica, aumentando a flexibilidade.

- Polimorfismo em Tempo de Compilação (Sobrecarga): Ocorre quando dois ou mais métodos têm o mesmo nome, mas diferentes parâmetros.
    - Proxima aula.

- Polimorfismo em Tempo de Execução (Sobrescrita): Ocorre quando um método da subclasse substitui um método da superclasse.

```Java
package animais;


public class Principal {

    public static void main(String[] args) {
       Animais animal = new Animais("Boby", "Lhasa Apso", "Claudio");
       Cachorro cachorro = new Cachorro("Pluto", "Shih tzu", "Bruna", 5);
       Animais gato = new Gato("Margô", "Gato preto", "Sylvia");
       
       //Polimorfismo em Tempo de Compilação (Sobrecarga)
       animal.fazerSom(); // Saída: Animal faz um som.
       cachorro.fazerSom(); // Saída: O cachorro late.
       gato.fazerSom(); // Saída: O gato mia.
       
       System.out.println(cachorro.getNomeAnimal());
       
       System.out.println(animal);
       System.out.println(cachorro);
       System.out.println(gato);
           
    }
    
}

```

## 🧐 Análise do Código

- Classe Animal:
    - Tem um atributo nome e um construtor que inicializa esse atributo.
    - O método fazerSom() imprime uma mensagem genérica.
- Classe Gato:
    - Herda de Animal.
    - Seu construtor chama super(nomeCachorro, raca, nomeDono), que invoca o construtor da superclasse Animal para inicializar o atributo nomeCachorro, raca e nomeDono.
    - O método fazerSom() é sobrescrito para fornecer uma implementação específica para Gato.
- Classe Main:
    - Cria uma instância de Gato e chama o método fazerSom(), que resulta na saída "Margô mia."
