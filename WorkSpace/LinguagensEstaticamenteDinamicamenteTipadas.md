# [Linguagens estaticamente ou dinamicamente tipadas?](https://robsoncastilho.com.br/2019/11/16/linguagens-estaticamente-ou-dinamicamente-tipadas/)

Por quase toda minha carreira, trabalhei com linguagens de tipagem estática. De dois anos para cá, estive quase totalmente focado em linguagens dinâmicas (Ruby e agora Elixir). Tendo já uma boa base prática para comparações, trago neste artigo minha visão sobre ambos estilos de tipagem e o porquê de minha preferência por um deles.

***DEFINIÇÕES***

**Tipagem estática** significa que os tipos das variáveis de um programa são explicitamente definidos no código e, portanto, conhecidos/checados em tempo de compilação. Exemplos de linguagens com essa característica: Java, C#, F#, Kotlin, Go, etc.

Na **tipagem dinâmica** é justamente o contrário: os tipos não são declarados no código e, portanto, conhecidos/checados em tempo de execução. Exemplos de linguagens: Ruby, Python, Clojure, Elixir, etc.

ATENÇÃO: Não confunda esses conceitos com tipagem forte e fraca. Tipagem dinâmica NÃO significa tipagem fraca! **Ruby possui tipagem dinâmica e forte, enquanto JavaScript possui tipagem dinâmica e fraca.**

***VANTAGENS DAS LINGUAGENS ESTATICAMENTE TIPADAS
***

**Identificação de erros em tempo de desenvolvimento**. A possibilidade de checar os tipos em tempo de desenvolvimento evita uma série de *bugs* em *runtime*, que podem, no pior caso, serem pegos apenas em ambiente de produção. Se seu método recebe um parâmetro do tipo X, é isso que precisa ser fornecido a ele.*
*

Ainda com relação à corretude, é muito simples refatorar o código, por exemplo, alterando os parâmetros de um método ou renomeando uma classe, sem risco de quebrar algo em *runtime*.

**Clareza de código.** Entender o código é fácil, já que não precisamos fazer suposições sobre o que é cada atributo de um objeto e quais são as entradas e saídas esperadas de um método/função. O código se torna a documentação.

**Ferramental.** Graças a uma boa IDE, ***refactoring\*** é trivial. Quanto maior o *codebase*, mais isso é visível: altere o nome de uma classe ou método e a IDE garante que tudo foi devidamente corrigido em todos os arquivos impactados. Ainda temos outras facilidades, como mover arquivos, navegar por eles (*Go To Definition*, *Go to Implementation*, *Find Usages*), *IntelliSense,* ***debugging\*** e ferramentas para **análise estática** de código.

***VANTAGENS DAS LINGUAGENS DINAMICAMENTE TIPADAS***

**Menos verbosidade.** Código mais enxuto, para escrever e para ler.

**Sem espera de compilação.** O ciclo “coda – testa” torna-se imediato. Basta salvar e rodar os testes ou a aplicação.

**Decisões sobre tipos podem ser evitados ou adiadas**. Escrever uma função pode ser mais rápido, sem a obrigação de definir os tipos de sua assinatura. Num primeiro momento, pode ser que você nem tenha certeza sobre qual tipo usar e, numa linguagem estaticamente tipada, você seria obrigado a decidir de imediato, com o risco de ter que mudar no futuro. Outro caso é o uso de [*duck typing*](https://pt.wikipedia.org/wiki/Duck_typing) para a modelagem de objetos de mesmo comportamento, sem a necessidade de criar um tipo base explícito, como uma classe abstrata ou interface.

**Metaprogramação/\*monkey patching\*.** Novamente, rapidez (para se fazer *hacks*, acessar as definições e membros de um objeto podendo alterá-los em *runtime*).

***VANTAGENS MESMO?***

Seguindo agora por um lado mais opinativo, vamos analisar as vantagens citadas para as linguagens dinâmicas.

Em se tratando de tempo de compilação, acredito que seja apenas questão de costume, já que houve muita evolução nesse sentido e o compilador é extremamente mais rápido do que nos primórdios do mesmo. A menos que você esteja trabalhando em um legado muito antigo – onde a compilação é penosa – o ciclo de desenvolvimento não é afetado em praticamente nada.

Com relação à menor verbosidade, hoje em dia, as linguagens estaticamente tipadas apresentam **inferência de tipo** – que é habilidade de detecção automática do tipo por parte do compilador – bastante evoluída, resultando em código bem menos verboso do que há 10 anos atrás.

Ainda em relação à verbosidade e às outras vantagens citadas, em softwares corporativos ou qualquer outro com certa complexidade e mudanças frequentes, essas ditas vantagens não se pagam no médio e longo prazo. Com o tempo, fica cada vez mais difícil de entender e manter o software, além de mais comuns os bugs em produção.

Por não ser uma exigência, o uso de tipos personalizados (classes, por exemplo) acaba desestimulado em certas situações. Um exemplo disso é o uso massivo de *hashes* no Ruby, que, embora simplifiquem a codificação, estimulam a violação de camadas, o desuso de termos de negócio ([*Ubiquitous Language*](https://martinfowler.com/bliki/UbiquitousLanguage.html)) e a dificuldade de compreensão do código.

E, por fim, vale dizer que quanto mais fácil de se fazer algo, mais fácil de ser usado indiscriminadamente, produzindo código de baixa qualidade. E aqui me refiro com mais ênfase à metaprogramação e *monkey patching*, que, independente de linguagem, devem ser usados com parcimônia.

***E OS TESTES?***

Outro assunto que aparece bastante quando falamos de tipagens estáticas x dinâmicas são os testes: escrevemos mais ou menos testes com tipagem dinâmica? Ou não há diferença?

Fato é que quanto melhor o sistema de tipos, menor a chance de termos estados irrepresentáveis no software, simplesmente “de graça”. É impossível, por exemplo, atribuir *null* a um tipo inteiro, em tempo de compilação.

Como garantimos esse tipo de coisa em uma linguagem dinâmica? Resposta: você NÃO garante. Por mais robusta que seja, uma suíte de testes irá validar o correto comportamento do sistema, porém desconsiderando possíveis erros de *type mismatch.*

Já vi erros em produção acontecerem porque um método esperava um objeto “user” com um atributo, digamos “name”, mas recebeu em *runtime* outro “user”, que não possuía este atributo. Isso em um software com ótima cobertura de código (aprox. 90%).

Respondendo as questões iniciais: ou você escreve a mesma quantidade de testes e torce para que tudo fique bem ou você escreve mais testes em linguagens dinâmicas (pelo menos para uma ou outra área mais crítica).

Acredito que “tipagem estática + testes” se complementam e trazem muito mais segurança e robustez. Indo além, a [verdadeira base da pirâmide de testes é o compilador](http://www.fabriciorissetto.com/blog/base-piramide-testes/).

***CONCLUINDO***

Este artigo propôs mostrar as vantagens de cada estilo de tipagem e, por tudo que foi dito, concluo que, para desenvolvimento de aplicações comerciais, que tendam a escalar, de forma segurança, robusta e mais gerenciável o uso de uma linguagem estaticamente tipada é mais apropriada a médio e longo prazo.

As vantagens mencionadas das linguagens estaticamente tipadas superam as vantagens das dinâmicas, que não chegam a ser vantagens tão grandes, principalmente no cenário de softwares com as características acima. Acredito que linguagens de tipagem dinâmica sejam mais adequadas para scripts, demos, MVPs e softwares de escopo menor e mais fechado.

É claro que diversos fatores contam para a seleção de uma linguagem, como o ecossistema, mas procurei manter o artigo focado em seu propósito original, até porque, incluindo ecossistema (*frameworks*, *libs*, comunidades, documentação e suporte), minha escolha seria ainda mais forte por linguagens tipadas.