# Aula 3 - Estrutura de Classes e Instanciação de Objetos - Encapsulamento, Construtor, Get, Set e toString

### 💊 Encapsulamento

- É o princípio de ocultar os detalhes internos de uma classe e expor apenas o que é necessário por meio de métodos públicos (getters e setters).
Isso ajuda a proteger o estado interno do objeto e a controlar o acesso a ele.

- Consiste em restringir o acesso direto a alguns dos componentes de um objeto. Isso é feito por meio da definição de modificadores de acesso (como private, protected, e public) e o uso de métodos públicos (getters e setters) para manipular os dados internos da classe.

#### 🔏 Características dos atributos utilizando encapsulamento

- Modificadores de Acesso:
  - private: A propriedade ou método é acessível apenas dentro da própria classe.
  - protected: A propriedade ou método é acessível dentro da classe e em subclasses.
  - public: A propriedade ou método é acessível de qualquer lugar.
 
### 🔨 Construtor

É um método especial de uma classe que é chamado automaticamente quando um objeto daquela classe é criado. O principal objetivo do construtor é inicializar/instanciar os atributos do objeto, garantindo que ele comece sua vida em um estado válido.

#### 🧰 Características dos Construtores
  - Nome: O construtor deve ter o mesmo nome da classe.
  - Sem Tipo de Retorno: O construtor não possui um tipo de retorno, nem mesmo void.
  - Sobrecarga: É possível ter múltiplos construtores (sobrecarga), permitindo diferentes maneiras de inicializar um objeto.

```Java
//Exemplo de um Construtor da classe Pessoa
//Constutor com parametros
public Pessoa(String nome, String CPF, int idade) {
        this.nome = nome;
        this.CPF = CPF;
        this.idade = idade;
    }
```

#### 🪹 Construtor Vazio:
  - Não recebe parâmetros.
  - Inicializa atributos com valores padrão.
  - Útil quando você deseja criar um objeto e configurar seus atributos mais tarde.
#### 🪺 Construtor com Atributos:
  - Recebe parâmetros que são usados para inicializar os atributos do objeto.
  - Permite a criação de objetos com valores específicos desde o início.
  - Ideal para garantir que um objeto comece em um estado válido.
    
Ambos os tipos de construtores são importantes no design de classes:

- O construtor vazio oferece flexibilidade para criar objetos sem inicialização imediata, enquanto o construtor com atributos fornece uma maneira de garantir que os objetos sejam criados com valores significativos.
- Você pode ter ambos os tipos de construtores em uma classe, permitindo que os desenvolvedores escolham como desejam criar os objetos.
  
#### 🔓 Getters e Setters:

- Métodos que permitem acessar e modificar propriedades privadas de forma controlada.

- 
```Java
//Exemplo de setter para a classe Pessoa
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

#### 💻 Exemplo feito em sala:
- Classe Pessoa
```Java
public class Pessoa {
    private String nome;
    private int idade;

    // Getter para nome
    public String getNome() {
        return nome;
    }

    // Setter para nome
    public void setNome(String nome) {
        this.nome = nome;
    }

    // Getter para idade
    public int getIdade() {
        return idade;
    }

    // Setter para idade
    public void setIdade(int idade) {
        if (idade >= 0) {
            this.idade = idade;
        }
    }
}
```

### 📌 Conclusão

Encapsulamento é uma prática essencial na programação orientada a objetos, pois:

- Ajuda a proteger o estado interno do objeto, evitando alterações indesejadas.
- Facilita a manutenção do código, pois alterações internas não afetam o código que usa a classe, desde que a interface (métodos públicos) permaneça a mesma.
- Promove um design mais limpo e modular, tornando o código mais legível e compreensível.
