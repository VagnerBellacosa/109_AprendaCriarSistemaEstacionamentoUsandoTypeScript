# Vamos falar de transpilers e supersets de Javascript.

## Existem algumas questões que você deveria levar em conta antes de usar um superset e talvez nem tenha percebido.

[![Filipe M. Silva](https://miro.medium.com/fit/c/96/96/1*_TKKGCc33U28JmkvdTd7gQ.jpeg)](https://medium.com/@flpms?source=post_page-----735f107e1869-----------------------------------) -  [Filipe M. Silva](https://medium.com/@flpms?source=post_page-----735f107e1869-----------------------------------  - [Nov 28, 2016](https://medium.com/aprendendo-nodejs/porque-não-usar-transpilers-e-supersets-de-javascript-735f107e1869?source=post_page-----735f107e1869-----------------------------------) · 7 min read



*Babel* e *Typescript*, ambas as ferramentas são muito comentadas dentro da comunidade e usadas em larga escala no *front-end.* *React* e *Ember* usando *Babel* e o *Angular 2* usando *Typescript.* E justamente no *front-end* que a falta de sabedoria pode trazer problemas.

Para deixar claro esse texto é focado no contexto de *front-end*. Mas inicialmente existe alguns problemas que se aplicam ao *Typescript*, independente do ambiente, seja no *front-end* ou *back-end*.

## Tipos no Javascript. Oi?! — Essa parte vale para todos os ambientes.

Tipar o JavaScript é algo que as empresas tentam fazer há muito tempo e existe um esforço grande para que isso se torne um padrão para o *Ecmascript*. Por exemplo a Adobe tentou isso com o *Action Script 3* e a Microsoft já tentou isso no passado com o *jScript*. É interessante que a grande *feature* do *Typescript* seja exatamente essa capacidade. De novo Microsoft?!

Os benefícios relacionados ao tipo de variáveis também podem ser alcançado usando uma bom nomenclatura para as variáveis. Um ganho de se ter tipos, em uma linguagem que já nasceu fracamente tipada, é auxiliar nos [*IntelliSenses* ](https://www.typescriptlang.org/docs/tutorial.html#running-your-typescript-web-app)para mostrar qual é o tipo da variável que você usará. Existe uma queda de performance quando você troca em tempo de execução o tipo do valor dentro do *Javascript.* Mas não é algo que você deveria se preocupar, *já que raramente você troca o tipo do dado em tempo de execução, né*?! Se estiver fazendo isso fica a dica. Mas na realidade o código escrito em *Typescript* vai virar código *Javascript* e não vai garantir que uma variável `number`, receba uma `string`de uma API.

Sei que *Typescript* tem outros benefícios como decorators e adiantar o tempo em que podemos usar a ES 2015 no *front-End*, mas para o *back-end* já temos o *Node* com uma compatibilidade altíssima e não agrega muito usar o *Typescript*, além de termos tipos nas variáveis.

## Transpilers, supersets e seu tempo

É importante ter em mente que temos uma mente limitada e ânsia por novas ferramentas começam a trazer uma complexidade desnecessárias e que não apresentam ganhos reais. Agora estamos falando do *Babel*.

*Babel* é uma ferramenta interessante, nos adiantou no tempo, já que pode levar alguns anos para que os usuários tenham browsers totalmente compatíveis à ES2015.

Mas tanto o *Babel* quanto o *Typescript*, você adiciona complexidade no seu desenvolvimento, para que você tenha no final um extraordinário resultado: ***Javascript\****.* Esse Javascript mesmo que você conhece, fracamente tipado, na versão ES5, sem decorators e etc.

Você vai precisar compilar as coisas logo não poderá usar assim que terminar de salvar o seu arquivo, vai ter o tempo de compilação e também a preocupação de instalação e adição de dependências. Quanto tempo será consumido com essas tarefas ao invés da atividade principal que é a entrega de software?

Mas vamos ver se o código gerado é benéfico?

## O código gerado

No *front-end*, devemos ter a preocupação com o tamanho do arquivo. E isso envolve escrever mais ou menos código, mesmo que o código passe por um minificador, existem coisas que ele não vai fazer e isso pode adicionar problemas com relação ao tamanho do arquivo. Por que o tamanho do arquivo é importante?

O tamanho dos dados trafegado para o usuário e após finalizado o download do seu script, serão armazenados em memória. Para se ter uma ideia os [5 celulares mais usados no Brasil](http://olhardigital.uol.com.br/noticia/saiba-qual-e-o-smartphone-mais-usado-no-brasil/61508) todos os modelos possuem 1 GB RAM. O que não é muita coisa se levar em conta todos os outros aplicativos e o próprio sistema rodando de fundo.

Então polyfills e outros scripts para suportar a execução do seu script, vão pesar no carregamento do seu site/aplicação e fazer o seu usuário desistir, a não ser que ele realmente precise usar. [[1\]](https://brasil.uxdesign.cc/a-importância-da-performance-das-páginas-na-experiência-do-usuário-36c375876e87#.6vc3itflm) [[2\]](http://www.ilex.com.br/site/pt-br/blog/latencia-e-tempo-de-carregamento-o-seu-site-esta-sendo-penalizado-e-voce-ainda-nao-percebeu-parte-2-245) [[3\]](https://www.nngroup.com/articles/website-response-times/) [[4\]](http://tecnologia.uol.com.br/ultimas-noticias/redacao/2011/07/27/internautas-moveis-esperam-so-5-segundos-pelo-carregamento-de-um-site-diz-pesquisa.jhtm)

Isso é algo que você deveria se preocupar. Por exemplo imagine o seguinte trecho de código escrito em ES6:

```
"use strict"class Person {    constructor(firstName, lastName) {
      this.firstName = firstName;
      this.lastName = lastName;
    };    get fullName() {
        let name;        name = `${this.firstName} ${this.lastName}`;        return name;
    };    get upperCaseName() {
        let name, upperCaseName;        name = this.fullName();
        upperCaseName = name.toUpperCase();        return upperCaseName;
    };
};let person = new Person('Filipe', 'Silva');console.log(person.upperCaseName());
```

O código que o babel irá gerar será semelhante ao seguinte:

```
"use strict";var _createClass = function () {
    function defineProperties(target, props) {
        for (var i = 0; i < props.length; i++) {
            var descriptor = props[i]; descriptor.enumerable = descriptor.enumerable || false;
            descriptor.configurable = true; if ("value" in descriptor) descriptor.writable = true;
            Object.defineProperty(target, descriptor.key, descriptor);
        }
    }
    return function (Constructor, protoProps, staticProps) {
        if (protoProps) defineProperties(Constructor.prototype, protoProps);
        if (staticProps) defineProperties(Constructor, staticProps);
        return Constructor;
    };
}();function _classCallCheck(instance, Constructor) {
    if (!(instance instanceof Constructor)) {
        throw new TypeError("Cannot call a class as a function");
    }
}var Person = function () {
    function Person(firstName, lastName) {
        _classCallCheck(this, Person);        this.firstName = firstName;
        this.lastName = lastName;
    }     _createClass(Person, [{
        key: 'upperCaseName',
        value: function upperCaseName() {
            var name = void 0,
                upperCaseName = void 0;            name = this.fullName;
            upperCaseName = name.toUpperCase();            return upperCaseName;
        }
    }, {
        key: 'fullName',
        get: function get() {
            var name = void 0;            name = this.firstName + ' ' + this.lastName;            return name;
        }
    }]);return Person;
}();;var person = new Person('Filipe', 'Silva');console.log(person.upperCaseName());
```

> Para ver exatamente o código gerado pelo Babel [Visualize o Gist](https://gist.github.com/flpms/637d28bc49d2902d48806680fdbee369). Fiz uma modificação para criar dar maior legibilidade ao código.

O código acima poderia ter várias alterações que já reduziriam o tamanho. Não estou falando de *minify* e *uglify*. Por exemplo dentro da função `getUpperCaseName` nas declarações de variáveis houve uma adição de ***14 bytes\*** a função, isso quando não temos o Babel adicionando `undefined` que adiciona para cada variável declarada no inicio ***10 bytes\***, no exemplo apresentado acima já somariam ***20 bytes.\***

Ele gerou um ponto e virgula no meio do código sem necessidade alguma. E para que o `get fullName` funcionasse como uma propriedade, ele adicionou duas funções que não normalmente não fariam parte de um código escrito sem usar o Babel. O arquivo escrito em ES6 possui um tamanho de ***550 bytes\*** e o arquivo gerado pelo Babel possuí ***1554 bytes\*** representando quase 3 vezes o tamanho do arquivo original. Mais a frente vou demonstrar um código escrito diretamente em ES5 e o tamanho do arquivo. Após mostrar o arquivo escrito em *Typescript*.

Parece micro-otimização, mas devemos lembrar de que isso em um codebase maior do tipo de uma SPA, pode acrescentar muito mais bytes e nem percebermos. Não podemos esquecer que boa parte dos usuários estão usando rede 3G e como isso deve estar afetando o pacote de dados dele. Se ele sente que seu app/site está consumindo muito do pacote ele vai embora.

Agora usando o mesmo código vamos ver o que acontece com o *Typescript*:

```
"use strict";
var Person = (function () {
    function Person(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.firstName = firstName;
        this.lastName = lastName;
    }
    ;
    Object.defineProperty(Person.prototype, "fullName", {
        get: function () {
            var fullname;
            fullname = this.firstName + " " + this.lastName;
            return fullname;
        },
        enumerable: true,
        configurable: true
    });
    Person.prototype.upperCaseName = function () {
        var name, upperCaseName;
        name = this.fullName;
        upperCaseName = name.toUpperCase();
        return upperCaseName;
    };
    ;
    return Person;
}());
;
var person = new Person('Filipe', 'Silva');
console.log(person.upperCaseName());
```

> [Link para o código no gist](https://gist.github.com/flpms/2996dcf7ff94f2e182772e11a5c66a20)

O código gerado pelo *Typescript* é mais enxuto do que o código gerado pelo Babel, mas ainda é notável que houve um aumento do arquivo. O arquivo .ts possuí ***548 bytes\*** enquanto o .js gerado pelo T*ypescript* tem ***849 bytes\***. Mas não deixa de apresentar seus problemas. O primeiro problema é que o código não tem suporte para IE8. Não deveria ser uma preocupação, mas dependendo do seu projeto fica o alerta.

Outro ponto é que o tanto o Babel como o *Typescript*, parecem se perder nos ponto e virgulas no final da declaração da classe. No construtor da classe ele se perde e duplica a atribuição das parâmetros recebidos. O ponto positivo para o código gerado do *Typescript* é que ele não adicionou *tokens* as variáveis declaradas e não usadas.

Agora segue um exemplo de como o código poderia ser escrito e atigindo o mesmo resultado em ES5.

```
"use strict";var Person = function(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
};Person.prototype = {
    getFullName: function() {
        var name;        name = this.firstName + ' ' + this.lastName;        return name;
    },
    getUpperCaseName: function() {
        var name, upperCaseName;        name = this.getFullName();        upperCaseName = name.toUpperCase();        return upperCaseName;
    }
};var person = new Person('Filipe', 'Silva');console.log(person.getUpperCaseName());
```

O código acima possuí uma pequena diferença na função `getFullName` já que para ser uma propriedade da classe aumentasse a complexidade desnecessariamente. O arquivo com o código possui ***542 bytes\*** e funciona no IE8, um código menor do que se fosse escrito com ES6.

## E ai vale a pena?

No fundo tanto o *Typescript* e o Babel, ajudam a adiantar algumas coisas e garantir outras. O fato do *Typescript* tipar o Javascript, não quer dizer que ele vai evitar a sua aplicação de quebrar, caso venha uma informação inesperada da sua API, já que no hora em que sua aplicação tiver executando, será o *Javascript* rodando.

Quanto ao Babel, se você lembrar que no final tudo que ele fez foi gerar um arquivo *Javascript* maior do que o necessário e adicionou uma complexidade desnecessária para depois rodar ES5. Fica até que obvio que não é uma boa solução para ambientes de produção. E se você quer realmente aprender ES6, procure usar o Node.JS, ele já tem 99% das features já implementadas e não existe a necessidade de gerar arquivos.

**Tanto o \*Babel\* como o \*Typescript\*, são ferramentas que precisam de uma analise maior sobre os prós e contras de seu uso em produção.** É importante descermos da *hype* e olhar profundamente se realmente vale a pena adotar para nossos projetos e aplicações tais soluções. Algumas discussões não valem a pena se no final quem sai prejudicado é quem paga as contas: **O seu cliente/usuário final.**

Se deseja consultar os códigos escritos e os gerados que foram usado nesse artigo, podem consultar aqui. https://github.com/flpms/transpilers-test

## Titulo das referencias sobre UX

*[1] — A importância da performance das páginas na experiência do usuário*

*[2] — Latência e Tempo de Carregamento: o seu site está sendo penalizado e você ainda não percebeu!*

*[3] — Website Response Times*

*[4] — Maioria dos usuários espera só 5 segundos para site abrir no celular, diz pesquisa*





[![Filipe M. Silva](https://miro.medium.com/fit/c/72/72/1*_TKKGCc33U28JmkvdTd7gQ.jpeg)](https://medium.com/@flpms?source=follow_footer-----735f107e1869-----------------------------------)WRITTEN BY[Filipe M. Silva](https://medium.com/@flpms?source=follow_footer-----735f107e1869-----------------------------------)Follow

