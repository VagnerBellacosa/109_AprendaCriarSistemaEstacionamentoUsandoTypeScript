# TypeScript: Introdução

Irei iniciar uma série de artigos sobre TypeScript. Vou tentar abordar desde os assuntos mais simples até os mais avançados. Neste artigo farei uma breve introdução junto a configuração inicial para os próximos artigos.

## Introdução

O TypeScript é um pré-processador de códigos JavaScript. Ele foi projetado para nos auxiliar no momento da codificação de códigos simples até os mais complexos. Para quem ainda não viu nada sobre TypeScript, ele herda conceitos de programação orientada a objetos, como no C#, Java, etc. Isso nos possibilita trabalhar com: classes, heranças e tipagens, sem fugir dos conceitos do JavaScript. Vejamos abaixo algumas vantagens em utilizá-lo:

- Com a tipagem, nós podemos depurar com mais facilidade o nosso código
- OOP (Programação Orientada a Objetos) nos auxilia na organização do código
- Validação em tempo de execução. Quando nós compilamos o TypeScript, ele válida todo nosso código, e em caso de erro, ele nos informa o arquivo e a linha que está ocorrendo o problema

Agora vamos configurar o nosso ambiente de trabalho e dar os primeiros passos com o ts.

## Configuração e criação de um projeto

Como premissa, nós precisamos ter o Node.js e o gerenciador de pacotes NPM instalados no nosso computador. Caso você ainda não tenha eles instalados, pode seguir a documentação oficial do site oficial do Node Docs. Para esse artigo não ficar muito longo, partirei de um ambiente com eles já instalados.

Com o ambiente OK, o seu primeiro passo é instalar o TypeScript em modo global. Para isso, execute o comando abaixo no seu terminal:

```shell
npm install -g typescript
```

Com o TypeScript em modo global, você pode executar ele de qualquer diretório do seu computador. O próximo passo será criar um projeto de exemplo.

Para os próximos passos será necessário um editor de textos. Eu irei utilizar o Visual Studio Code, mas você pode utilizar um de sua preferência. Com o seu editor aberto, crie um novo arquivo com a extensão .ts. Para esse exemplo, eu irei chamar o arquivo de hello.ts. Em seguida, atualize ele com o código abaixo:

```typescript
function hello(person) {
    return "Hello, " + person;
}

var user = "Bill Gates";

document.body.innerHTML = hello(user)
```

Para fazer o transpile, execute tsc .\hello.ts no seu terminal. Abaixo você pode ver o resultado da execução desse comando.

```typescript
function hello(person) {
  return "Hello, " + person; 
}
var user = "Bill Gates";
document.body.innerHTML = hello(user);
```

Com isso, nós finalizamos esse primeiro artigo, no próximo irei demonstrar as tipagens.