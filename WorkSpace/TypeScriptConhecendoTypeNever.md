# TypeScript: conhecendo o type never

Em uma das versões anteriores do TypeScript foi adicionado um ***type\*** chamando ***never\****.* Esse ***type\*** indica que algo nunca deve ocorrer.

![img](https://cdn-images-1.medium.com/max/880/0*M8TE33bmRPffPZMZ.jpg)

what is never in TypeScript? Never no TypeScript

É isso mesmo, nós temos um ***type\*** no TypeScript chamado *never*, que indica que uma função ***nunca\*** deve retornar algo e que é diferente do ***type\*** **void**.

Mas calma, vamos entender ele melhor através de alguns exemplos práticos abaixo.

***Nós podemos utilizar o type never em funções sem retorno:\***

```typescript
function carregandoGame(): never { while (true) { console.log("Carregando todos processos de um game!"); } }
```

Essa função acima é comum no desenvolvimento de games onde nos temos um método que funciona como um loop infinito.

***(calma, eu irei explicar mais abaixo a diferença entre never x void)\***

Em funções com ***exception\***

```javascript
function verificandoTipo(x: string | number): boolean {
    if (typeof x === "string") {
      return true;
    } else if (typeof x === "number") {
      return false;
    }

    return fail("Esse método não aceita esse tipo de type!");
  }
  
  function fail(message: string): never { throw new Error(message); }
```

 

**Testando essa função**

```typescript
verificandoTipo("teste String"); //Ok
verificandoTipo(10); //Ok
let ativo = true;
verificandoTipo(ativo); // retorna uma exception
```

**Print do retorno na console:**

![img](https://cdn-images-1.medium.com/max/880/1*U0CM7DL39VOPbfHYUL2ECQ.png)

Validando retorno never no TypeScript

No exemplo anterior nós temos uma função que recebe um type *Union (string e number)*, que deve retornar um boolean. Caso seja passado um outro valor diferente de string e number, a chamada entra em uma outra função chamada ***fail\*** que irá retornar uma ***exception.\***

Agora, qual é a diferença entre void e never?

O **type** ***void\*** pode receber o valor ***null\*** ou ***undefined\*** e o ***type never\*** não pode receber nenhum valor. Abaixo você tem um exemplo demonstrando os os dois ***types\*** como variáveis:

![img](https://cdn-images-1.medium.com/max/880/1*iQ5o-qFdKz-WMVic6qnh4g.png)

diferença entre **never** e **void** no TypeScript

E para finalizar, quando não especificado um ***type\*** nas funções do TypeScript, ele retorna um valor ***undefined\***. Abaixo você tem um exemplo demonstrando esse cenário:

```typescript
function teste(): void {
  console.log('função void!')
}
let testeFuncaoVoid: void = teste();//função void!
console.log(testeFuncaoVoid); // undefined
```

Bom, a ideia desse artigo era apresentar mais um dos types do TypeScript. Espero que tenham gostado e até a próxima galera 😉