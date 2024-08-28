# Aula 4 - Modificadores de acesso, métodos e atributos estáticos

## Modificadores de acessos

Os modificadores de acesso são palavras-chave que definem o nível de acesso aos membros (atributos e métodos) de uma classe.

- Os três principais modificadores de acesso são:
  - public: os membros públicos podem ser acessados de qualquer lugar, tanto dentro como fora da classe.
  - private: os membros privados só podem ser acessados de dentro da própria classe. Eles não são visíveis para outras classes.
  - protected: os membros protegidos têm um nível de acesso intermediário. Eles podem ser acessados dentro da própria classe, em subclasses (herança) e em classes no mesmo pacote.
  - abstract: Um método abstrato não possui implementação na classe em que é declarado. Ele deve ser implementado nas subclasses.
  - final: Um método final não pode ser sobrescrito em subclasses. Ele mantém a implementação definida na classe em que é declarado.
  - static: Atributos e métodos estáticos pertencem à classe em vez de pertencerem a instâncias individuais (objetos) da classe. Eles podem ser acessados diretamente usando o nome da classe, sem a necessidade de criar uma instância.
    - Atributo estático: É compartilhado por todas as instâncias da classe. Pode ser acessado usando o nome da classe, seguido pelo nome do atributo.
    - Método estático: Não requer uma instância da classe para ser invocado. Pode ser acessado usando o nome da classe, seguido pelo nome do método.
   
## Exemplo feito em sala

```Java
  
package pessoa;

import java.util.ArrayList;
import java.util.List;
import javax.swing.JOptionPane;

public class Principal {
    
    static List<Pessoa>pessoas = new ArrayList<Pessoa>();
    
    static void inserirPessoaLista(String nome, String CPF, int idade){
        Pessoa pessoa = new Pessoa(nome, CPF, idade);
        pessoas.add(pessoa);
    }

    public static void main(String[] args) {

        for(int i = 0; i < 2; i++){
            inserirPessoaLista(JOptionPane.showInputDialog("Nome:"),
                               JOptionPane.showInputDialog("CPF:"),
                               Integer.parseInt(JOptionPane.showInputDialog("Idade:")));
        }
        //Aparecer janela nomes digitados
        for(Pessoa pessoa: pessoas){
            JOptionPane.showMessageDialog(null, pessoa);
        }
        
         System.out.println(pessoas);
    }
    
}
```
