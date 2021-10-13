# TypeScript: ReadonlyArray<T>

Dando continuidade à minha série de artigos sobre ***TypeScript\***, hoje eu irei escrever sobre um modificador de acessos adicionado na versão 3.4 para arrays e tuplas, o ***readonly\***.

Mas antes de falar sobre ele, vamos dar uma passada no type ***ReadonlyArray<T>.\***

Para quem não conhece, o ***readonlyArray<T>\*** remove todos métodos de alteração de um array como: push, pop… etc.

Abaixo você tem um exemplo de como utilizar ele:

```javascript
let arrNumber: number[] = [1, 2, 3, 4];
let readOnlyArr: ReadonlyArray<number> = arrNumber;
readOnlyArr[0] = 12; // error!
readOnlyArr.push(5); // error!
readOnlyArr.length = 100; // error!
a = readOnlyArr; // error!
```

Note nas linhas 2,3,4,5 e 6 que nós não conseguimos alterar o seu valor.

Agora que estamos alinhados com ***ReadonlyArray<T>\***, vamos ao modificador `***readonly.\***`

Ele funciona da mesma forma que nós vimos no exemplo anterior, a unica diferença é a sua sintaxe, nessa nova versão está mais simples e nós podemos utilizar ele também com *tuplas*.

> Caso você não tenha visto nada sobre *tuplas* no **TypeScript**, eu recomendo a leitura do seguinte artigo: [***TypeScript Tuplas\***](https://medium.com/@programadriano/typescript-tuplas-fae7eba00066)*.*

Agora vamos alterar o ***ReadonlyArray<T>\*** do exemplo anterior para ***readonly\*** e navegar por ele utilizando o *for*.

Abaixo você tem um trecho de código demonstrando essa alteração:

```javascript
let arrNumber: number[] = [1, 2, 3, 4];
let readOnlyArr: Readonly<number[]> = arrNumber;


for (let index = 0; index < readOnlyArr.length; index++) {
    const element = readOnlyArr[index];
    console.log(element);
}

/*
Resultado:
1
2
3
4
*/
```

Como você pode ver no exemplo acima, nós alteramos de *ReadOnlyArray* para *readonly* e ele funcionou da mesma forma.

E conforme passei acima, nessa nossa versão nós também podemos utilizar o moderador ***readonly\*** com tuplas:

```javascript
class Calc {
    somaComTuplas(numbs: readonly[number, number]) {
    const x = numbs[0] + numbs[1];
    return x;
 }
}


const readonlyTuple: readonly[number, number] =[10, 5];
let c = new Calc();
console.log(c.somaComTuplas(readonlyTuple));
```

***Resultado: 15\***

Dai vem aquela pergunta, onde eu poderia utilizar ele ou onde encontrar um exemplo prático utilizando ele?

Pensando nisso eu dei uma pesquisa em algumas bibliotecas no portal **NPM** e encontrei uma biblioteca que exporta dados **json** para um arquivo ***.csv\*** chamado [*json2csv*](https://www.npmjs.com/package/json2csv)*.*

Analisando as suas chamadas eu encontrei o método abaixo:

```javascript
export function parseAsync<T>(
    data: Readonly<T> | ReadonlyArray<T> | Readable,
    opts?: json2csv.Options<T>,
    transformOpts?: TransformOptions
): Promise<string>;
```

Note que ele recebe como parâmetro o ***readonlyArray<T>.\***

Bom, a ideia desse artigo era demonstrar mais uma das novidades do TypeScript 3.4 através de alguns exemplos práticos 😉

Espero que tenham gostado e até um próximo artigo pessoal 😉



### [THIAGO ADRIANO](https://imasters.com.br/perfil/thiagoadriano)

