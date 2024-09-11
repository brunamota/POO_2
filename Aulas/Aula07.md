# Aula 7 - Relacionamentos entre classes: Generalização e Especialização

Conceitos que descrevem como classes podem ser organizadas em uma hierarquia, onde uma classe mais genérica (superclasse) é estendida por classes mais específicas (subclasses).

### :busts_in_silhouette: Generalização
Definição:
Generalização é o processo de identificar características comuns entre várias classes e criar uma superclasse que encapsule essas características.
Permite a reutilização de código e a simplificação da estrutura do programa.
Exemplo:
Considere as classes Cachorro, Gato e Pássaro. Cada um possui atributos e métodos comuns, como nome, idade e fazerSom().
Podemos criar uma superclasse chamada Animal que contém esses atributos e métodos.

### :bust_in_silhouette: Especialização
Definição:
Especialização é o processo de criar subclasses a partir de uma superclasse, onde cada subclasse adiciona ou modifica comportamentos específicos.
Permite que as subclasses herdem características da superclasse, ao mesmo tempo que introduzem suas próprias particularidades.
Exemplo:
As subclasses Cachorro e Gato herdam de Animal e implementam o método fazerSom() de maneira específica.
