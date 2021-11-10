# TypeScript – O superset de JavaScript

Postado em [10 DE OUTUBRO DE 2012](https://www.eduardopires.net.br/2012/10/typescript/)

Olá pessoal, já ouviram / leram algo sobre TypeScript?

![TypeScript](https://i2.wp.com/www.eduardopires.net.br/wp-content/uploads/2012/10/image.jpg?resize=250%2C61&ssl=1)Sim, é uma novidade, estou escrevendo apenas 9 dia depois da Microsoft ter [anunciado](http://blogs.msdn.com/b/somasegar/archive/2012/10/01/typescript-javascript-development-at-application-scale.aspx) a release do preview do TypeScript.

O TypeScript é um superconjunto “superset” do JavaScript, logo escreve-se TypeScript da mesma forma que se escreve JavaScript, todo código JavaScript também é um código TypeScript.

- O TypeScript não é um [Dart](http://pt.wikipedia.org/wiki/Dart_(linguagem_de_programação)), a Microsoft não está tentando substituir o JavaScript.
- O TypeScript também não é uma resposta da Microsoft ao [CoffeeScript](http://coffeescript.org/), são propostas diferentes, o CoffeeScript é uma linguagem diferente e possui uma sintaxe própria.

Escrever grandes códigos JavaScript é complicado principalmente quando o assunto é ferramental “tooling”, a proposta do TypeScript é facilitar o desenvolvimento em JavaScript já que o TypeScript traz grandes benefícios, tais como:

- Classes (chega de prototypes)
- Módulos (ficou mais fácil exportar código)
- Tipos definidos (são opcionais)
- Navegação no código fonte (é possível renomear, encontrar referências e definições)
- Interfaces
- Refatoração.

Let’s try!
Veja nesse exemplo básico algumas coisas que nunca viu em JavaScript:

Código TypeScript

| `1`  | `// Veja uma classe.` |
| ---- | --------------------- |
|      |                       |

| `2`  | `class` `Greeter {` |
| ---- | ------------------- |
|      |                     |

| `3`  | `  ``greeting: string; ``// Tipo estático` |
| ---- | ------------------------------------------ |
|      |                                            |

| `4`  | `  ``constructor (message: string) { ``// Construtor` |
| ---- | ----------------------------------------------------- |
|      |                                                       |

| `5`  | `    ``this``.greeting = message;` |
| ---- | ---------------------------------- |
|      |                                    |

| `6`  | `  ``}` |
| ---- | ------- |
|      |         |

| `7`  | `  ``greet() {` |
| ---- | --------------- |
|      |                 |

| `8`  | `    ``return` `"Hello, "` `+ ``this``.greeting;` |
| ---- | ------------------------------------------------- |
|      |                                                   |

| `9`  | `  ``}` |
| ---- | ------- |
|      |         |

| `10` | `}`  |
| ---- | ---- |
|      |      |

| `11` |      |
| ---- | ---- |
|      |      |

| `12` | `var greeter = ``new` `Greeter(``"world"``);` |
| ---- | --------------------------------------------- |
|      |                                               |

| `13` |      |
| ---- | ---- |
|      |      |

| `14` | `var button = document.createElement(``'button'``)` |
| ---- | --------------------------------------------------- |
|      |                                                     |

| `15` | `button.innerText = ``"Say Hello"` |
| ---- | ---------------------------------- |
|      |                                    |

| `16` | `button.onclick = function() {` |
| ---- | ------------------------------- |
|      |                                 |

| `17` | `  ``alert(greeter.greet())` |
| ---- | ---------------------------- |
|      |                              |

| `18` | `}`  |
| ---- | ---- |
|      |      |

| `19` |      |
| ---- | ---- |
|      |      |

| `20` | `document.body.appendChild(button)` |
| ---- | ----------------------------------- |
|      |                                     |

Código JavaScript gerado:

| `1`  | `var` `Greeter = (``function` `() {` |
| ---- | ------------------------------------ |
|      |                                      |

| `2`  | `  ``function` `Greeter(message) {` |
| ---- | ----------------------------------- |
|      |                                     |

| `3`  | `    ``this``.greeting = message;` |
| ---- | ---------------------------------- |
|      |                                    |

| `4`  | `  ``}` |
| ---- | ------- |
|      |         |

| `5`  | `  ``Greeter.prototype.greet = ``function` `() {` |
| ---- | ------------------------------------------------- |
|      |                                                   |

| `6`  | `    ``return` `"Hello, "` `+ ``this``.greeting;` |
| ---- | ------------------------------------------------- |
|      |                                                   |

| `7`  | `  ``};` |
| ---- | -------- |
|      |          |

| `8`  | `  ``return` `Greeter;` |
| ---- | ----------------------- |
|      |                         |

| `9`  | `})();` |
| ---- | ------- |
|      |         |

| `10` | `var` `greeter = ``new` `Greeter(``"world"``);` |
| ---- | ----------------------------------------------- |
|      |                                                 |

| `11` | `var` `button = document.createElement(``'button'``);` |
| ---- | ------------------------------------------------------ |
|      |                                                        |

| `12` | `button.innerText = ``"Say Hello"``;` |
| ---- | ------------------------------------- |
|      |                                       |

| `13` | `button.onclick = ``function` `() {` |
| ---- | ------------------------------------ |
|      |                                      |

| `14` | `  ``alert(greeter.greet());` |
| ---- | ----------------------------- |
|      |                               |

| `15` | `};` |
| ---- | ---- |
|      |      |

| `16` | `document.body.appendChild(button);` |
| ---- | ------------------------------------ |
|      |                                      |

**Resumindo**

TypeScript ao meu ver é escrever JavaScript de uma forma melhorada e organizada, em conjunto com o Visual Studio ficou mais fácil navegar e refatorar o código, o resultado é maior produtividade.

O código TypeScript é escrito em um arquivo *.TS, porém ao publicar ou debugar uma aplicação com TypeScript o código TS será transformado em JS.
O ganho é produtividade mesmo, pois todo código produzido ao virar JavaScript não carrega com ele as melhorias citadas (classes, tipagem estática, etc), mas não tem problema, afinal o código a ser trabalhado vai ser sempre o TypeScript e esse permanece da forma que escrevermos.

Todo código TypeScript é JavaScript, podemos então copiar um código JS e colar num arquivo TS e funcionará normalmente, sem necessidade de migração, para projetos existentes esse comportamento é muito bacana, uma vez que ao colar o código JS num TS podemos fazer as melhorias que quisermos (ou nenhuma) e a vida segue normalmente.

O TypeScript é [open source](http://typescript.codeplex.com/license), no site oficial é possível brincar em um playground que transforma online TypeScript em JavaScript, podemos até rodar o código gerado (ótimo teste inicial).

**Utilizando o TypeScript**

A maioria dos desenvolvedores Microsoft tem como IDE de desenvolvimento o Visual Studio e para isso é necessário baixar e instalar um [plugin](http://www.microsoft.com/en-us/download/details.aspx?id=34790).

O TypeScript funciona em outras plataformas em sistemas operacionais diversos, é suportado pelo [Vim, Emacs e Sublime](http://blogs.msdn.com/b/interoperability/archive/2012/10/01/sublime-text-vi-emacs-typescript-enabled.aspx)

Outro ponto importante, o [Source Mapping](http://www.aaron-powell.com/web/typescript-source-maps), ao debugar um código JS ele é diretamente mapeado para o código TS, isso facilita muito a vida, outros geradores de JavaScript como o próprio CoffeeScript ainda não possuem esse recurso.

No Visual Studio podemos trabalhar com TypeScript criando um projeto HTML Application ou com MVC3 (não entendi por que não MVC4, logo abaixo demonstro como resolver isso).

Suporte para HTML Application with TypeScript:

[![html_TS](https://i1.wp.com/www.eduardopires.net.br/wp-content/uploads/2012/10/html_TS1.jpg?resize=584%2C399&ssl=1)](https://i1.wp.com/www.eduardopires.net.br/wp-content/uploads/2012/10/html_TS1.jpg?ssl=1)

Suporte para um template MVC3:

[![mvc_ts](https://i1.wp.com/www.eduardopires.net.br/wp-content/uploads/2012/10/mvc_ts.jpg?resize=577%2C536&ssl=1)](https://i1.wp.com/www.eduardopires.net.br/wp-content/uploads/2012/10/mvc_ts.jpg?ssl=1)

O template “Typescript Internet Application” é apenas um template ASP.NET MVC 3 que permite compilar códigos TypeScript para JavaScript no processo de Build.
Esta configuração de build é feita no arquivo de projeto:

| `1`  | `<``None` `Include``=``"Scriptsjquery.d.ts"` `/>` |
| ---- | ------------------------------------------------- |
|      |                                                   |

| `2`  | `  ``<``TypeScriptCompile` `Include``=``"Scriptssite.ts"` `/>` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

| `3`  | `  ``<``Content` `Include``=``"Scriptssite.js"``>` |
| ---- | -------------------------------------------------- |
|      |                                                    |

| `4`  | `   ``<``DependentUpon``>site.ts</``DependentUpon``>` |
| ---- | ----------------------------------------------------- |
|      |                                                       |

| `5`  | `  ``</``Content``>` |
| ---- | -------------------- |
|      |                      |

| `6`  | ` ``<``Target` `Name``=``"BeforeBuild"``>` |
| ---- | ------------------------------------------ |
|      |                                            |

| `7`  | ` ``<``Exec` |
| ---- | ------------ |
|      |              |

| `8`  | `   ``Command="&quot;$(PROGRAMFILES)` |
| ---- | ------------------------------------- |
|      |                                       |

| `9`  | `   ``Microsoft SDKsTypeScript\0.8.0.0tsc&quot;` |
| ---- | ------------------------------------------------ |
|      |                                                  |

| `10` | `   ``@(TypeScriptCompile ->'"%(fullpath)"', ' ')" />` |
| ---- | ------------------------------------------------------ |
|      |                                                        |

| `11` | ` ``</``Target``>` |
| ---- | ------------------ |
|      |                    |

O TypeScript não fornece um template para MVC4, mas como mencionei acima, existe uma forma de resolver este problema. Basta criar um template MVC4 padrão e adicionar no arquivo de projeto “.csproject” o seguinte código:

| `1`  | `<``ItemGroup``>` |
| ---- | ----------------- |
|      |                   |

| `2`  | `  ``<``TypeScriptCompile` `Include``=``"$(ProjectDir)***.ts"` `/>` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

| `3`  | `</``ItemGroup``>` |
| ---- | ------------------ |
|      |                    |

| `4`  | ` ``<``Target` `Name``=``"BeforeBuild"``>` |
| ---- | ------------------------------------------ |
|      |                                            |

| `5`  | `  ``<``Exec` `Command="&quot;$(PROGRAMFILES)` |
| ---- | ---------------------------------------------- |
|      |                                                |

| `6`  | `  ``Microsoft SDKsTypeScript\0.8.0.0tsc&quot;` |
| ---- | ----------------------------------------------- |
|      |                                                 |

| `7`  | ` ``@(TypeScriptCompile ->'"%(fullpath)"', ' ')" />` |
| ---- | ---------------------------------------------------- |
|      |                                                      |

| `8`  | ` ``</``Target``>` |
| ---- | ------------------ |
|      |                    |

Assim quando fizer o build do projeto o TypeScript vai ser compilado e o código JavaScript será gerado em arquivos JS automaticamente.

**Primeiras impressões**

Passei 4 dias aprendendo e utilizando TypeScript, eu gostei, consigo escrever um código mais bonito e organizado, de forma mais rápida e não precisei aprender uma outra linguagem ou sintaxe como seria no caso de utilizar o CoffeeScript.

Atenção ao versionar o código JS gerado, pois em um novo build ele será sobrescrito e ocasionará um erro, já que após versionar o arquivo se torna “read-only”.

Não é de hoje que diversas abordagens tentam esconder o JavaScript, o Google fez isso em 2011, o CoffeeScript faz, o WebForms do ASP.Net, todos geram JavaScript sem que nós nos preocupemos com isso, porém com TypeScript é a forma mais fácil que senti de trabalhar com JavaScript, afinal consigo debugar meu código original com o Source Mapping, mantenho atualizado meus conhecimentos em JavaScript e tenho uma visão mais clara do código que vai ser gerado, afinal JavaScript também é TypeScript.

Espero que tenham gostado, caso queira participar, dar um feedback ou tirar alguma dúvida faça um comentário ![🙂](https://s.w.org/images/core/emoji/13.1.0/svg/1f642.svg)

**Links úteis**

- [Site Oficial](http://www.typescriptlang.org/)
- [Documentação do TypeScript](http://go.microsoft.com/fwlink/?LinkId=267238)
- [Plugin para Visual Studio](http://www.microsoft.com/en-us/download/details.aspx?id=34790)
- [Plugin para outras IDE’s](http://blogs.msdn.com/b/interoperability/archive/2012/10/01/sublime-text-vi-emacs-typescript-enabled.aspx)
- [Código Fonte (open source)](http://typescript.codeplex.com/SourceControl/BrowseLatest)
- [Post do Somasegar](http://blogs.msdn.com/b/somasegar/archive/2012/10/01/typescript-javascript-development-at-application-scale.aspx)
- [Vídeo do Anders Hejlsberg](https://channel9.msdn.com/posts/Anders-Hejlsberg-Introducing-TypeScript)

**Referências**

- [Shiju Varghese Blog](http://weblogs.asp.net/shijuvarghese/archive/2012/10/02/microsoft-typescript-a-typed-superset-of-javascript.aspx)
- [Scott Hanselman Blog](http://www.hanselman.com/blog/WhyDoesTypeScriptHaveToBeTheAnswerToAnything.aspx)
- [Giovanni Bassi – Lambda3 Blog](http://blog.lambda3.com.br/2012/10/typescript-uma-anlise-inicial/)

Bons estudos e até mais pessoal.