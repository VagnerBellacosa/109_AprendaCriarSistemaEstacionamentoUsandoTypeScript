# Quais as diferenças entre tipagens: estática ou dinâmica e forte ou fraca

Uma dúvida muito comum é sobre tipagem nas linguagens de programação. Nesse artigo falamos de forma simples e com exemplos sobre as tipagens estática, dinâmica, fraca e forte. Além do conceito de inferência de tipo.

 cerca de 1 ano atrás

[Artigos](https://www.treinaweb.com.br/blog)Quais as diferenças entre tipagens: estática ou dinâmica e forte ou fraca

Quando vemos uma nova linguagem de programação, uma das primeiras coisas que as pessoas costumam colocar na descrição dela é a tipagem. Neste artigo vamos falar um pouco sobre os tipos de tipagem.

## Tipagem Estáticas

Linguagens com tipagem estática não permitem ao desenvolvedor alterar o tipo da variável depois de declarada. Geralmente a verificação de tipo é feita em tempo de compilação. Podemos ver o exemplo abaixo na linguagem Java:

Copiar

```java
public class MyClass {
    public static void main(String args[]) {
      int variavel = 10;

      variavel = "Elton Fonseca"; //error: incompatible types: String cannot be converted to int
    }
}
```

Quando tentamos atribuir um valor de um tipo diferente do que foi declarado na variável temos um erro.



![Java - Fundamentos](https://d2knvm16wkt3ia.cloudfront.net/assets/svg-icon/java.svg)

##### CursoJava - Fundamentos

[Conhecer o curso](https://www.treinaweb.com.br/curso/java-fundamentos)

## Tipagem Dinâmica

A tipagem dinâmica está ligado a habilidade da linguagem de programação em escolher o tipo de dado de acordo com o valor atribuído à variável em tempo de execução dinamicamente. Veja o exemplo abaixo na linguagem PHP:

Copiar

```php
$variavel = "Elton Fonseca";

echo gettype($variavel); //string

$variavel = 340;

echo gettype($variavel); //integer

$variavel = 340.89;

echo gettype($variavel); //double

$variavel = true;

echo gettype($variavel); //boolean
```

Muita gente confunde, acha que linguagem de tipagem dinâmica não possui tipos. Na verdade, ela possui tipos normalmente, a diferença está apenas na capacidade da linguagem em escolher o tipo automaticamente.



![PHP - Fundamentos](https://d2knvm16wkt3ia.cloudfront.net/assets/svg-icon/php.svg)

##### CursoPHP - Fundamentos

[Conhecer o curso](https://www.treinaweb.com.br/curso/php-fundamentos)

## Inferência de tipo

Algumas linguagens estáticas podem fazer a inferência de tipo na declaração de variáveis, mas não permite que o tipo seja alterado após a declaração. Veja esse exemplo na linguagem C#:

Copiar

```csharp
using System;

public class Program
{
    public static void Main()
    {
        var variavel = "Treinaweb";

        Console.WriteLine(variavel.GetType()); //System.String

        variavel = 28; //Compilation error (line 11, col 14): Cannot implicitly convert type 'int' to 'string'
    }
}
```

Ele apresenta um erro quando tentamos atribuir um valor de tipo diferente a variável. Isso porque ele apenas realiza a inferência do tipo inicial da variável, depois disso como a linguagem possui características estáticas não permite alterar o tipo.



![C# (C Sharp) Básico](https://d2knvm16wkt3ia.cloudfront.net/assets/svg-icon/csharp.svg)

##### CursoC# (C Sharp) Básico

[Conhecer o curso](https://www.treinaweb.com.br/curso/csharp-basico)

## Tipagem Fraca

A tipagem fraca está ligada a característica da linguagem de realizar conversões automaticamente entre tipos diferentes de dados. Veja o exemplo abaixo abaixo em Javascript:

Copiar

```javascript
var nome = "Elton Fonseca"; //string

var idade = 28; //number

console.log(nome + " " + idade); //Elton Fonseca 28
```



![JavaScript Básico](https://d2knvm16wkt3ia.cloudfront.net/assets/svg-icon/javascript.svg)

##### CursoJavaScript Básico

[Conhecer o curso](https://www.treinaweb.com.br/curso/javascript-basico)

## Tipagem Forte

Linguagens fortemente tipadas não realizam conversões automaticamente. Vamos pegar como exemplo a linguagem Python. Ela possui tipagem forte, se formos executar o exemplo acima em Python teríamos um erro:

Copiar

```php
nome = "Elton Fonseca" #str
idade = 28 #int

print(nome + " " + idade) #TypeError: can only concatenate str (not "int") to str
```



![Python - Fundamentos](https://d2knvm16wkt3ia.cloudfront.net/assets/svg-icon/python.svg)

##### CursoPython - Fundamentos

[Conhecer o curso](https://www.treinaweb.com.br/curso/python-fundamentos)

## Considerações finais

Muitas linguagens de programação não se enquadram exatamente entre tipagem estática ou dinâmica e tipagem forte ou fraca. Principalmente pelo fato de cada uma destas abordagens possuírem vantagens e desvantagens, as linguagens mais modernas tendem a mesclar alguns aspectos de cada uma.