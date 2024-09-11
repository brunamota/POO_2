# Aula 8 - Relacionamentos entre Classes: Composição, Agregação e Associação

### Associação
É um relacionamento onde uma classe usa outra classe. É uma relação "usa um" (ou "tem um"). Pode ser unidirecional (uma classe conhece a outra) ou bidirecional (ambas as classes se conhecem).

- Exemplo: Imagine uma classe Professor que tem um relacionamento com a classe Aluno.

```Java
class Aluno {
    private String nome;

    public Aluno(String nome) {
        this.nome = nome;
    }

    public String getNome() {
        return nome;
    }
}

class Professor {
    private String nome;

    public Professor(String nome) {
        this.nome = nome;
    }

    public void ensinar(Aluno aluno) {
        System.out.println(nome + " está ensinando " + aluno.getNome());
    }
}

```

### Agregação
- A agregação é um tipo de associação onde uma classe contém referências a outras classes, mas essas classes podem existir independentemente da classe que as contém. É uma relação "tem um" onde as partes podem viver sem o todo.
- Exemplo: Considere uma classe Departamento que agrega a classe Professor.
  
```Java
import java.util.ArrayList;

class Departamento {
    private String nome;
    private ArrayList<Professor> professores;

    public Departamento(String nome) {
        this.nome = nome;
        this.professores = new ArrayList<>();
    }

    public void adicionarProfessor(Professor professor) {
        professores.add(professor);
    }

    public void listarProfessores() {
        System.out.println("Professores do departamento " + nome + ":");
        for (Professor professor : professores) {
            System.out.println(professor.getNome());
        }
    }
}
```

### Composição
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
public class Main {
    public static void main(String[] args) {
        // Demonstração de Associação
        Aluno aluno = new Aluno("João");
        Professor professor = new Professor("Maria");
        professor.ensinar(aluno);

        // Demonstração de Agregação
        Departamento departamento = new Departamento("Ciências");
        departamento.adicionarProfessor(professor);
        departamento.listarProfessores();

        // Demonstração de Composição
        Carro carro = new Carro("V8");
        carro.exibirInfo();
    }
}
```
