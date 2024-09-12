# Aula 8 - Relacionamentos entre Classes: Composição, Agregação e Associação

### 🧑🏻‍🏫 Associação
É um relacionamento onde uma classe usa outra classe. É uma relação "usa um" (ou "tem um"). Pode ser unidirecional (uma classe conhece a outra) ou bidirecional (ambas as classes se conhecem).

- Exemplo: A implementação é direta e mostra como as classes interagem. O professor não é parte da sala e vice-versa, mas eles têm um relacionamento onde o professor pode lecionar na sala.

```Java

package relacionamentoclasses;


class SalaDeAula {
    private String numero;
    private int capacidade;

    public SalaDeAula(String numero, int capacidade) {
        this.numero = numero;
        this.capacidade = capacidade;
    }

    public String getNumero() {
        return numero;
    }

    public int getCapacidade() {
        return capacidade;
    }

    @Override
    public String toString() {
        return "Sala " + numero + " (Capacidade: " + capacidade + ")";
    }
}

class Professor {
    private String nome;

    public Professor(String nome) {
        this.nome = nome;
    }

    public String getNome() {
        return nome;
    }

    public void ensinar(SalaDeAula sala) {
        System.out.println(nome + " está lecionando na " + sala);
    }
}

```

### ⛓️ Agregação
- A agregação é um tipo de associação onde uma classe contém referências a outras classes, mas essas classes podem existir independentemente da classe que as contém. É uma relação "tem um" onde as partes podem viver sem o todo.
- Exemplo: A classe Instituicao contém uma lista de Professor, mas os professores podem existir independentemente da instituição. Isso caracteriza uma relação de agregação. O Instituicao pode ter zero ou mais professores, e a mesma instância de Professor pode ser adicionada a várias instituições, se necessário.
  
```Java

package relacionamentoclasses;

import java.util.ArrayList;

class Instituicao{
    private String nome;
    private ArrayList<Professor> professores;

    public Instituicao(String nome) {
        this.nome = nome;
        this.professores = new ArrayList<>();
    }

    public void adicionarProfessor(Professor professor) {
        professores.add(professor);
    }

    public void listarProfessores() {
        System.out.println("Professores da " + nome + ":");
        for (Professor professor : professores) {
            System.out.println("- " + professor.getNome());
        }
    }
}

```

### 🔗 Composição
- A composição é um tipo de agregação mais forte, onde a classe contida não pode existir sem a classe que a contém. É uma relação "parte de" (ou "é parte de").
- Exemplo: Considere uma classe Carro que possui uma classe Motor. O motor não faz sentido fora do carro.

```Java
class Motor {
    private String tipo;

    public Motor(String tipo) {
        this.tipo = tipo;
    }

    public String getTipo() {
        return tipo;
    }
}

class Carro {
    private Motor motor;

    public Carro(String tipoMotor) {
        this.motor = new Motor(tipoMotor); // O motor é criado junto com o carro
    }

    public void exibirInfo() {
        System.out.println("Carro com motor do tipo: " + motor.getTipo());
    }
}
```

#### Classe Principal
```Java
public class Principal {
    public static void main(String[] args) {
        // Demonstração de Associação
        SalaDeAula sala101 = new SalaDeAula("101", 30);
        Professor professor1 = new Professor("João");
        professor1.ensinar(sala101); 

        // Demonstração de Agregação
        Instituicao instituicao = new Instituicao("Escola Superior de Tecnologia");
        instituicao.adicionarProfessor(professor1);
        instituicao.listarProfessores();

        // Demonstração de Composição
        Carro carro = new Carro("V8");
        carro.exibirInfo();
        
    }
}
```
