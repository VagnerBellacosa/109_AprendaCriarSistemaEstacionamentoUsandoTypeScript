# TypeScript: Tuplas

### https://imasters.com.br/perfil/thiagoadriano)

## Introdução

Para quem não conhece as *Tuplas ou “Tuple* no inglês”, elas representam uma estrutura de dados simples parecida com um Array. A grande diferença entra as duas é que nos array’s nós trabalhamos somente com um tipo de dado e com as tuplas com diferentes tipos. Para ficar mais claro, veja abaixo a declaração de um array de number e de uma *tuple de string,number e string*.

```

let list: Array<number> = [1, 2, 3]; //Exemplo com Array

let list: [string, number, string]; //Exemplo com tuplas
nós também podemos declarar uma variável com um valor inicial no TS:

let list = [1, 2, 3]; //Exemplo com Array

let list = ['Thiago Adriano', 34, 'tadriano.net@gmail.com'];
```

Depois dessa breve introdução, vamos a dois exemplos práticos: um com adicionando um valor a uma tuple e um outro acessando esse valor.

## **Adicionando valores em uma Tuple**

Da mesma forma que no Array, nós utilizamos o ***.push()\*** para adicionar um novo registro em uma Tuple.

```typescript
let list: [string, number] = ['Bill Gates', 1]; list.push('Steve', 2); console.log(list); //resultado: [ 'Bill', 1, 'Steve Jobs', 2 ]
```

**Acessando valores em uma Tuple**

Agora para acessar esses valores, nós podemos buscar eles por seus indices:

```typescript
let list: [string, number] = ['Bill Gates', 1]; console.log(list[0]); //Bill console.log(list[1]); //1
```

Uma outra forma de acessar esses valores é utilizando um loop como o **foreach:**

```typescript
let list: [string, number] = ['Bill Gates', 1];
list.push('Steve Jobs', 2);
list.forEach(element => {
   console.log(element);
});
//Resultado:
Bill Gates
1
Steve Jobs
2
```

## Bem simples né?

A ideia aqui era ser algo rápido, e que pudesse apresentar mais uma das features que nós podemos utilizar do TypeScript. Espero que tenham gostado é até um próximo artigo pessoal 😉