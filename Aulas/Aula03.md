# Aula 3 - Estrutura de Classes e Instanciação de Objetos - Encapsulamento, Construtor, Getter, Setter

## 💊 Encapsulamento

- Consiste em restringir o acesso direto a alguns dos componentes de um objeto. Isso é feito por meio da definição de modificadores de acesso (como private, protected, e public) e o uso de métodos públicos (getters e setters) para manipular os dados internos da classe.

- É uma prática essencial na programação orientada a objetos, pois:
  - Ajuda a proteger o estado interno do objeto, evitando alterações indesejadas.
  - Facilita a manutenção do código, pois alterações internas não afetam o código que usa a classe, desde que a interface (métodos públicos) permaneça a mesma.
  - Promove um design mais limpo e modular, tornando o código mais legível e compreensível.


### 🔐 Características dos atributos utilizando encapsulamento

- Modificadores de Acesso:
  - **private:** A propriedade ou método é acessível apenas dentro da própria classe.
  - **protected:** A propriedade ou método é acessível dentro da classe e em subclasses.
  - **public:** A propriedade ou método é acessível de qualquer lugar.
 
```Java
//Exemplo de atributos utilizando diferentes tipos de encapsulamento.
//atributos - características
    public String nome; //é acessível de qualquer lugar.
    private String CPF; //acessível apenas dentro da própria classe
    private int idade; //acessível apenas dentro da própria classe
```
 
## 🔨 Construtor

É um método especial de uma classe que é chamado automaticamente quando um objeto daquela classe é criado. O principal objetivo do construtor é inicializar/instanciar os atributos do objeto, garantindo que ele comece sua vida em um estado válido.

### 🧰 Características dos Construtores:
  - **Nome:** O construtor deve ter o mesmo nome da classe.
  - **Sem Tipo de Retorno:** O construtor não possui um tipo de retorno, nem mesmo void.
  - **Sobrecarga:** É possível ter múltiplos construtores (sobrecarga), permitindo diferentes maneiras de inicializar um objeto ou que os desenvolvedores escolham como desejam criar os objetos.

```Java
//Exemplo de um Construtor da classe Pessoa
//Constutor com parametros
public Pessoa(String nome, String CPF, int idade) {
        this.nome = nome;
        this.CPF = CPF;
        this.idade = idade;
    }
```

### 🪹 Construtor Vazio:
  - Não recebe parâmetros.
  - Inicializa atributos com valores padrão.
  - Oferece flexibilidade para criar objetos sem inicialização imediata
  - Útil quando você deseja criar um objeto e configurar seus atributos mais tarde.
### 🪺 Construtor com Atributos:
  - Recebe parâmetros que são usados para inicializar os atributos do objeto.
  - Permite a criação de objetos com valores específicos desde o início.
  - Ideal para garantir que um objeto comece em um estado válido.
  
## 🔓 Getters e Setters:

São métodos que permitem acessar e modificar os atributos de uma classe de maneira controlada. Eles são uma parte essencial do encapsulamento, ajudando a proteger os dados internos de uma classe.

### Características dos GEtters e Setters:
- **Controle de Acesso:** Permitem que você controle como os atributos são acessados e modificados.
- **Validação:** Os setters podem incluir lógica para validar os dados antes de atribuí-los a um atributo.
- **Encapsulamento:** Mantêm a integridade dos dados, permitindo que a implementação interna da classe mude sem afetar o código que usa a classe.

### 📂 Getters:
Métodos que retornam o valor de um atributo privado.

```Java
//Exemplo de getter para a classe Pessoa
public String getNome() {
        return nome;
    }

    public String getCPF() {
        return CPF;
    }

    public int getIdade() {
        return idade;
    }
```

### 📝 Setters: Métodos que permitem definir ou atualizar o valor de um atributo privado.

```Java
//Exemplo de setter para a classe Pessoa
 public void setNome(String nome) {
        this.nome = nome;
    }

    public void setCPF(String CPF) {
        this.CPF = CPF;
    }

    public void setIdade(int idade) {
        this.idade = idade;
    }
```

## ✍️ toString()

É um método que pertence à classe Object em Java (e em muitas outras linguagens orientadas a objetos). Esse método é usado para retornar uma representação em forma de string de um objeto. Quando você imprime um objeto ou o converte em uma string, o método toString() é chamado automaticamente.

### 🛑 Importância
- **Representação Legível:** Permite que você forneça uma representação legível e informativa do objeto, facilitando a depuração e a compreensão do estado do objeto.
- **Personalização:** Você pode sobrescrever o método para personalizar a saída de acordo com os atributos do objeto.
- **Facilita a Depuração:** Ao imprimir objetos, você pode obter informações úteis sobre seus atributos e estado.

```Java
    //Exemplo do toString() para a classe Pessoa
    @Override
    public String toString() {
        return "Pessoa{" + "nome = " + nome + ", CPF = " + CPF + ", idade = " + idade + '}';
    } 
```

## 💻 Exemplo feito em sala:
- Classe Pessoa
```Java

package pessoa;

public class Pessoa {
    
    //atributos - características
    public String nome; //é acessível de qualquer lugar.
    private String CPF; //acessível apenas dentro da própria classe
    private int idade; //acessível apenas dentro da própria classe
    
    //Construtor
    public Pessoa(String nome, String CPF, int idade) {
        this.nome = nome;
        this.CPF = CPF;
        this.idade = idade;
    }

    //Getters
    public String getNome() {
        return nome;
    }

    public String getCPF() {
        return CPF;
    }

    public int getIdade() {
        return idade;
    }
    
    //Setters
    public void setNome(String nome) {
        this.nome = nome;
    }

    public void setCPF(String CPF) {
        this.CPF = CPF;
    }

    public void setIdade(int idade) {
        this.idade = idade;
    }

    //Assinatura da classe utilizadno o método toString()
    @Override
    public String toString() {
        return "Pessoa{" + "nome = " + nome + ", CPF = " + CPF + ", idade = " + idade + '}';
    } 
}
```
- Classe Principal
```Java

package pessoa;

public class Principal {

    public static void main(String[] args) {
        // instaciar um objeto
        Pessoa pessoa1 = new Pessoa("João", "000.000.000-00", 20);
        Pessoa pessoa2 = new Pessoa("Alfredo", "111.111.111-11", 24);
        
        System.out.println(pessoa1.nome);
        
        pessoa1.nome = "Pedro"; 
        System.out.println(pessoa1.getNome());
        
        System.out.println(pessoa1.getCPF());
        
        pessoa1.setCPF("222.222.222-22");
        System.out.println(pessoa1.getCPF());
        
        System.out.println(pessoa1);
    }
    
}

```
