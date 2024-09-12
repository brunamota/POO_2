# Aula 7 - Relacionamentos entre classes: Generalização e Especialização

Conceitos que descrevem como classes podem ser organizadas em uma hierarquia, onde uma classe mais genérica (superclasse) é estendida por classes mais específicas (subclasses).

## :ocean: Generalização
Generalização é o processo de identificar características comuns entre várias classes e criar uma superclasse que encapsule essas características.
Permite a reutilização de código e a simplificação da estrutura do programa.

## :droplet: Especialização

Especialização é o processo de criar subclasses a partir de uma superclasse, onde cada subclasse adiciona ou modifica comportamentos específicos.
Permite que as subclasses herdem características da superclasse, ao mesmo tempo que introduzem suas próprias particularidades.

## 🧐 Análise do Código
- Classe ContaBancaria:
  - É uma classe abstrata que define a estrutura básica para todas as contas bancárias, incluindo atributos de titular e saldo, além de métodos abstratos e concretos.
  - É uma superclasse que **generaliza** os atributos e métodos comuns a todas as contas bancárias, como titular, saldo, sacar() e exibirSaldo().
  - A lista contas é do tipo ContaBancaria, mas armazena objetos de diferentes subclasses (ContaCorrente e ContaPoupanca). Isso demonstra o conceito de polimorfismo, onde o mesmo método (sacar() e exibirSaldo()) pode ter comportamentos diferentes dependendo do tipo de objeto.
- Subclasses ContaCorrente e ContaPoupanca:
  - Ambas herdam de ContaBancaria e implementam o método sacar(), com regras específicas para cada tipo de conta.
  - **especializam** o comportamento da classe ContaBancaria ao implementar o método sacar() de formas diferentes:
    - ContaCorrente permite saques com um limite estabelecido.
    - ContaPoupanca permite saques apenas até o saldo disponível.
- Classe Main:
  - Cria uma lista de contas e demonstra o uso de herança, abstração, métodos get e set, construtores e polimorfismo ao iterar sobre as contas e realizar saques.
 
#### Classe Conta Bancaria

```Java

package contabancaria;

abstract class ContaBancaria {
    private String nomeTitular;
    private double saldo;

    // Construtor
    public ContaBancaria(String nomeTitular, double saldo) {
        this.nomeTitular = nomeTitular;
        this.saldo = saldo;
    }

    // Métodos get e set
    public String getNometitular() {
        return nomeTitular;
    }

    public void setNomeTitular(String nomeTitular) {
        this.nomeTitular = nomeTitular;
    }

    public double getSaldo() {
        return saldo;
    }

    public void setSaldo(double saldo) {
        this.saldo = saldo;
    }

    // Método abstrato
    public abstract void sacar(double valor);

    // Método concreto
    public void exibirSaldo() {
        System.out.println("Saldo de " + nomeTitular + ": R$ " + saldo);
    }
}

```

#### Classe Conta Corrente

```Java

package contabancaria;


public class ContaCorrente extends ContaBancaria{
 private double limite;

    public ContaCorrente(String nomeTitular, double saldo, double limite) {
        super(nomeTitular, saldo);
        this.limite = limite;
    }

    @Override
    public void sacar(double valor) {
        if (valor <= (getSaldo() + limite)) {
            setSaldo(getSaldo() - valor);
            System.out.println("Saque de R$ " + valor + " realizado com sucesso da Conta Corrente.");
        } else {
            System.out.println("Saldo insuficiente para saque.");
        }
    }
}

```

#### Classe Conta Poupança

```Java

package contabancaria;


class ContaPoupanca extends ContaBancaria {
    public ContaPoupanca(String titular, double saldo) {
        super(titular, saldo);
    }

    @Override
    public void sacar(double valor) {
        if (valor <= getSaldo()) {
            setSaldo(getSaldo() - valor);
            System.out.println("Saque de R$ " + valor + " realizado com sucesso da Conta Poupança.");
        } else {
            System.out.println("Saldo insuficiente para saque.");
        }
    }
}
```

#### Classe Conta Poupança

```Java

package contabancaria;

import java.util.ArrayList;

public class Principal {

    public static void main(String[] args) {
         ArrayList<ContaBancaria> contas = new ArrayList<>();
        
        // Criando contas
        contas.add(new ContaCorrente("Alice", 1000.0, 500.0));
        contas.add(new ContaPoupanca("Bob", 800.0));

        // Exibindo saldos e realizando saques
        for (ContaBancaria conta : contas) {
            conta.exibirSaldo();
            conta.sacar(300.0);
            conta.exibirSaldo();
            System.out.println();
        }

        // Tentando saques com saldo insuficiente
        contas.get(0).sacar(1500.0); // Saque na Conta Corrente
        contas.get(1).sacar(900.0);   // Saque na Conta Poupança
    }
    
}

```
