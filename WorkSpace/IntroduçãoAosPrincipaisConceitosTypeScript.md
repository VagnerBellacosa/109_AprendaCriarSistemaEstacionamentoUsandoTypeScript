- [REACT NATIVE](https://josiaspereira.com.br/tag/react-native/)
- 

# Introdução aos principais conceitos do TypeScript

[NodeJS](https://josiaspereira.com.br/tag/nodejs/)•Jun 05, 2020



O TypeScript é um superconjunto tipado de JavaScript, destinado a tornar a linguagem mais escalável e confiável.

É de código aberto e é mantido pela Microsoft desde que o criou em 2012. No entanto, o TypeScript teve sua inovação inicial como a principal linguagem de programação no Angular 2. Continua crescendo desde então, também nas comunidades React, Vue e agora mais recentemente com o lançamento do [Deno 1.0](https://deno.land/v1).

Neste tutorial, você aprenderá o básico do TypeScript com a ajuda de exemplos práticos.

Vamos começar.

### **Instalando o TypeScript**

Antes de começarmos a codificar, precisamos instalar o TypeScript em nosso computador. Vamos usar `npm`isso, basta abrir o terminal e digite o seguinte comando:

```sh
npm install -g typescript
ou
yarn global add typescript
```

Uma vez instalado, podemos verificá-lo executando o comando `tsc -v`que exibirá a versão do TypeScript instalado.

### **Escrevendo algum código**

Vamos criar nosso primeiro arquivo TypeScript e escrever um código dentro dele. Abra seu IDE ou Editor de Texto favorito e crie um arquivo com o nome `example.ts` - Para arquivos TypeScript, usamos a extensão`.ts`

Por enquanto, apenas escreveremos algumas linhas de JavaScript antigo simples, pois todo o código JavaScript também é um código TypeScript válido:

```js
let x = 3;  
let y = 5;  
let z = a + b;

console.log(z);
```

O próximo passo é compilar nosso TypeScript em JavaScript simples, pois os navegadores esperam arquivos `.js`.

### **Compilando TypeScript**

Para compilar, executaremos o comando de `tsc filename.ts`, que cria um arquivo JavaScript com o mesmo nome de arquivo, mas com uma extensão diferente, e que eventualmente podemos transmitir aos nossos navegadores.

Portanto, abra o terminal no local do arquivo e execute o seguinte comando:

```sh
tsc example.ts
```

***\*Dica\**** : Se você deseja compilar todos os arquivos TypeScript dentro de qualquer pasta, use o comando:`tsc *.ts`

### **Tipos de dados**

TypeScript - como o próprio nome sugere - é a versão tipada do JavaScript. Isso significa que podemos especificar tipos para diferentes variáveis no momento da declaração. Eles sempre manterão o mesmo tipo de dados nesse escopo.

A tipagem é um recurso muito útil para garantir confiabilidade e escalabilidade. A verificação de tipo ajuda a garantir que nosso código funcione conforme o esperado. Além disso, ajuda na busca de bugs e erros e na documentação adequada do nosso código.

A sintaxe para atribuir um tipo a qualquer variável é escrever o nome da variável seguido por um sinal `:` e, em seguida, o nome do tipo seguido por um sinal de  `=`e o valor da variável, caso já queira atribuir valor à variável.

Existem três tipos diferentes no TypeScript: o `any`, os tipo `Built-in` e os tipos `User-defined`. Vamos dar uma olhada em cada um deles.

#### **Tipo any**

O  de dados `any` é o superconjunto de todos os tipos de dados no TypeScript. Dar a qualquer variável o tipo de `any`é equivalente a desativar a verificação de tipo de uma variável.

```js
let myVariable: any = 'This is a string'
```

#### **Tipos incorporados**

Esses são os tipos criados no TypeScript. Eles incluem `number`, `string`, `boolean`, `void`, `null`e `undefined`.

```js
let num: number = 5;  
let name: string = 'Alex';  
let isPresent: boolean = true;
```

#### **Tipos definidos pelo usuário**

Os tipos `User-defined` incluem `enum`, `class`, `interface`, `array`, e `tuple`. Discutiremos alguns deles posteriormente neste artigo.

### **Programação orientada a objetos**

O TypeScript suporta todos os recursos da programação orientada a objetos, como classes e interfaces. Esse recurso é um grande impulso para o JavaScript - ele sempre lutou com sua funcionalidade OOP, especialmente desde que os desenvolvedores começaram a usá-lo para aplicativos de grande escala.

#### **Classe**

Na programação orientada a objetos, uma classe é o modelo de objetos. Uma classe define como um objeto seria em termos de recursos e funcionalidades desse objeto. Uma classe também encapsula dados para o objeto.

O TypeScript possui suporte interno para classes que não são suportadas pelo ES5 e versões anteriores. Isso significa que podemos usar a palavra `class` para declarar facilmente uma classe.

```js
class Car {

// fields
  model: String;  
  doors: Number;  
  isElectric: Boolean;

constructor(model: String, doors: Number, isElectric: Boolean) {  
    this.model = model;  
    this.doors = doors;  
    this.isElectric = isElectric;  
  }
// methods
displayMake(): void {  
    console.log(`This car is ${this.model}`);  
  }

}
```

No exemplo acima, declaramos uma classe `Car`, juntamente com algumas de suas propriedades, que estamos inicializando no `constructor`. Também temos um método que exibia alguma mensagem usando sua propriedade

Vamos ver como podemos criar uma nova instância desta classe:

```js
const Prius = new Car('Prius', 4, true);  
Prius.displayMake(); // This car is Prius
```

Para criar um objeto de uma classe, usamos a palavra-chave `new`e chamamos o construtor da classe e passamos as propriedades para ela. Agora este objeto `Prius`tem suas próprias propriedades de `model`, `doors`e `isElectric`. O objeto também pode chamar o método de `displayMake`, que teria acesso às propriedades de `Prius`.

#### **Interface**

O conceito de interfaces é outro recurso poderoso do TypeScript, que permite definir a estrutura das variáveis. Uma interface é como um contrato sintático ao qual um objeto deve estar em conformidade.

As interfaces são melhor descritas através de um exemplo real. Então, suponha que tenhamos um objeto de `Car`:

```js
const Car = {  
  model: 'Prius',  
  make: 'Toyota',  
  display() => { console.log('hi'); }  
}
```

Se olharmos para o objeto acima e tentarmos extrair sua assinatura, seria:

```js
{  
  model: String,  
  make: String,  
  display(): void  
}
```

Se quisermos reutilizar essa assinatura, podemos declará-la na forma de uma interface. Para criar uma interface, usamos a palavra-chave `interface`.

```js
interface ICar {  
  model: String,  
  make: String,  
  display(): void  
}

const Car: ICar = {  
  model: 'Prius',  
  make: 'Toyota',  
  display() => { console.log('hi'); }  
}
```

Aqui, declaramos uma interface chamada `ICar`e criamos um objeto `Car`. `Car`agora está vinculando a interface `ICar`, garantindo que o `Car`objeto defina todas as propriedades que estão na interface. Todo objeto que implementar a interface `ICar` obrigatoriamente deverá possuir os mesmos métodos e atributos.

### **Conclusão**

Espero que isso tenha lhe dado uma rápida visão de como o TypeScript pode tornar seu JavaScript mais estável e menos propenso a bugs.

O TypeScript está ganhando muito impulso no mundo do desenvolvimento web. Há também uma quantidade crescente de desenvolvedores do React que estão adotando. O TypeScript é definitivamente algo que qualquer desenvolvedor JavaScript deve estar atento.