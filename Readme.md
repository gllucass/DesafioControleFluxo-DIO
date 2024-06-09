### DesafioControleFluxo

## DIO - Trilha Java Básico
[www.dio.me](https://www.dio.me)

### Projeto proposto por:
- Gleyson Sampaio
### Projeto realizado por:
- Geraldo Lucas

## Descrição do Desafio

Vamos exercitar todo o conteúdo apresentado no módulo de Controle de Fluxo codificando o seguinte cenário.

### Cenário
O sistema deverá receber dois parâmetros via terminal que representarão dois números inteiros. Com estes dois números, você deverá obter a quantidade de interações (for) e realizar a impressão no console (`System.out.print`) dos números incrementados.

**Exemplo:**

Se você passar os números 12 e 30, teremos uma interação (for) com 18 ocorrências para imprimir os números, como no exemplo: "Imprimindo o número 1", "Imprimindo o número 2" e assim por diante.

Se o primeiro parâmetro for MAIOR que o segundo parâmetro, você deverá lançar a exceção customizada chamada de `ParametrosInvalidosException` com a mensagem: "O segundo parâmetro deve ser maior que o primeiro".

### Requisitos
1. Crie o projeto `DesafioControleFluxo`.
2. Dentro do projeto, crie a classe `Contador.java` para realizar toda a codificação do nosso programa.
3. Dentro do projeto, crie a classe `ParametrosInvalidosException` que representará a exceção de negócio no sistema.

### Implementação

#### Classe `ParametrosInvalidosException`

```java
public class ParametrosInvalidosException extends Exception {
    public ParametrosInvalidosException(String message) {
        super(message);
    }
}
```

#### Classe `Contador`

```java
import java.util.Scanner;

public class Contador {
    public static void main(String[] args) {
        Scanner terminal = new Scanner(System.in);
        
        System.out.println("Digite o primeiro parâmetro");
        int parametroUm = terminal.nextInt();
        
        System.out.println("Digite o segundo parâmetro");
        int parametroDois = terminal.nextInt();
        
        try {
            // Chamando o método contendo a lógica de contagem
            contar(parametroUm, parametroDois);
        } catch (ParametrosInvalidosException exception) {
            // Imprimir a mensagem: O segundo parâmetro deve ser maior que o primeiro
            System.out.println(exception.getMessage());
        }
    }

    static void contar(int parametroUm, int parametroDois) throws ParametrosInvalidosException {
        // Validar se parametroUm é MAIOR que parametroDois e lançar a exceção
        if (parametroUm > parametroDois) {
            throw new ParametrosInvalidosException("O segundo parâmetro deve ser maior que o primeiro");
        }

        int contagem = parametroDois - parametroUm;
        
        // Realizar o for para imprimir os números com base na variável contagem
        for (int i = 1; i <= contagem; i++) {
            System.out.println("Imprimindo o número " + i);
        }
    }
}
```

### Como Executar

1. Certifique-se de ter o Java instalado em seu sistema.
2. Compile a classe `Contador.java` utilizando o comando:
   ```bash
   javac Contador.java
   ```
3. Execute o programa utilizando o comando:
   ```bash
   java Contador
   ```
4. Insira os valores solicitados pelo programa e observe a saída no console.

### Exemplo de Uso

1. Quando `parametroUm = 12` e `parametroDois = 30`, o programa deve imprimir:
   ```
   Imprimindo o número 1
   Imprimindo o número 2
   ...
   Imprimindo o número 18
   ```

2. Quando `parametroUm = 30` e `parametroDois = 12`, o programa deve lançar a exceção:
   ```
   O segundo parâmetro deve ser maior que o primeiro
   ```
   