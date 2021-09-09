# Um hack do OpenJDK que aceita Java em Português

Dê uma olhada em [](./doc/building.md) para saber como
compilar o projeto.

## Como que isso funciona?

Bem, eu basicamente modifiquei o analisador léxico para traduzir
palavras-chave da linguagem em português para o token correspondente.
Foi feito de forma que não quebrasse a especificação original da linguagem
para que o projeto podesse compilar.

Eu gostaria de poder fazer uma extenção do pacote `java.lang` para que
o *runtime* também fosse em português, mas essa parte iria me tomar bastante
tempo e eu queria terminar isso na quinta à noite.

Se você quiser um exemplo, basta compilar isso aqui:

```java
classe Principal {
  estatico classe Empregado {
    privado inteiro matricula;

    vazio defineMatricula(inteiro matricula) {
      esse.matricula = matricula;
    }

    inteiro pegaMatricula() {
      retorne esse.matricula;
    }

    vazio naoChame() lancas Exception {
      lanca novo Exception("Nao ta funcionando");
    }
  }

  publico estatico vazio main(String argumentos[]) {
    Empregado empregado = novo Empregado();

    empregado.defineMatricula(1337);

    tente {
      empregado.naoChame();
    } captura (Exception e) {
      System.out.println(e.getMessage());
    } finalmente {
      System.out.println("A matricula do empregado e " + empregado.pegaMatricula());
    }
  }
}
```
