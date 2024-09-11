# Aula 7 - Relacionamentos entre classes: Generalização e Especialização

Conceitos que descrevem como classes podem ser organizadas em uma hierarquia, onde uma classe mais genérica (superclasse) é estendida por classes mais específicas (subclasses).

## :ocean: Generalização
Definição:
Generalização é o processo de identificar características comuns entre várias classes e criar uma superclasse que encapsule essas características.
Permite a reutilização de código e a simplificação da estrutura do programa.

## :droplet: Especialização

Especialização é o processo de criar subclasses a partir de uma superclasse, onde cada subclasse adiciona ou modifica comportamentos específicos.
Permite que as subclasses herdem características da superclasse, ao mesmo tempo que introduzem suas próprias particularidades.

## 🧐 Análise do Código
- Classe ContaBancaria:
  - É uma classe abstrata que define a estrutura básica para todas as contas bancárias, incluindo atributos de titular e saldo, além de métodos abstratos e concretos.
  - Generalização: é uma superclasse que **generaliza** os atributos e métodos comuns a todas as contas bancárias, como titular, saldo, sacar() e exibirSaldo().
  - Polimorfismo: a lista contas é do tipo ContaBancaria, mas armazena objetos de diferentes subclasses (ContaCorrente e ContaPoupanca). Isso demonstra o conceito de polimorfismo, onde o mesmo método (sacar() e exibirSaldo()) pode ter comportamentos diferentes dependendo do tipo de objeto.
- Subclasses ContaCorrente e ContaPoupanca:
  - Ambas herdam de ContaBancaria e implementam o método sacar(), com regras específicas para cada tipo de conta.
  - Especialização: **especializam** o comportamento da classe ContaBancaria ao implementar o método sacar() de formas diferentes:
    - ContaCorrente permite saques com um limite estabelecido.
    - ContaPoupanca permite saques apenas até o saldo disponível.
- Classe Main:
  - Cria uma lista de contas e demonstra o uso de herança, abstração, métodos get e set, construtores e polimorfismo ao iterar sobre as contas e realizar saques.
