# Semana 01

## Introdução

![Esquema básico de um compilador](./compiladores_introducao_fig.png)

### Sobre o que é este curso?

- Como os programas escritos em uma linguagem de alto nível (ex.: Java, C++) são transformados em código de máquina?
- Como podemos garantir que um programa tenha um significado (semântica)?
- Como é realizado o gerenciamento de memória do programa?
- Como nós podemos analisar programas para descobrir propriedades invariantes (constantes) e melhorar o desempenho em tempo de execução?

Ao longo do curso todas essas perguntas ficarão mais claras.

### Nota histórica

- Até a década de 50, computadores eram programados em assembly.
- Em 1951-1952, Grace Hopper desenvolveu o sistema A-0 para o UNIVAC I.
  - Posteriormente ela contribuiu significativamente para o desenvolvimento da linguagem COBOL.
- Em 1957 o compilador de FORTRAN foi desenvolvido pela IBM.
  - Com uma equipe liderada por John Backus.
- Na decada de 60 ocorreu o desenvolvimento do primeiro compilador de bootstrapping para LISP.
- Na decada de 70 o design de linguagens/compiladores floresceu*.
- Hoje nós temos milhares de linguagens a disposição (muitas delas pouco utilizadas).
  - Algumas com um design melhor que outras.

### Arquitetura básica

![Arquitetura básica de um compilador](./compiladores_arquitetura_basica.png)  
*Para manter uma fidelidade maior ao material, optamos por manter alguns termos em inglês. Porém suas equivalências serão feitas posteriormente.

#### Front-end

- Realiza a análise léxica, sintática e semântica (Lexing e Parsing);
  - Faz a conversão de cadeias de caracteres (código fonte) em estruturas de dados internas do compilador.
  - Ocorre usualmente em duas fases:

![Estruturas de dados do front-end de um compilador](./front_end_compilador.png)

#### Ferramentas de *Parsing*

- A etapa de *parsing* ocorre basicamente em todas as aplicações.
  - Ex.: Barra de pesquisa do Google, calendários, etc.
  - É o primeiro passo para transformar dados brutos em informação.
- Um pouco de teoria da computação pode te ajudar a entender esses passos (aqui vai um [link](https://cs121.boazbarak.org))
  - Expressões regulares
  - Gramáticas livre de contexto (automato de pilha)
  - Essas abstrações aparecem também na etapa de otimização!
- Existem também muitas ferramentas para te ajudar nessa etapa:
  - Ex.: Yacc e Lex, Menhir, Antlr, *Parsing Combinators*, etc.

#### Análise Semântica (Elaboration)

- É aqui onde ocorre as checagens de tipos.
  - Resolver variáveis, módulos, etc.
  - Checagem das operações sobre os tipos (se a operação é válida sobre aquele tipo de variável).
  - Infere tipos para sub-expressões.
  - Checa outros problemas.

![Etapa da análise semântica](./elaboration_compilador.png)

#### Geração de Código Intermediário (Lowering)

- Traduz recursos de alto nível em um pequeno número de instruções.
  - Ex.: `while`, `for`, `do-while` são traduzidos basicamente em instruções utilizando `goto`.
  - Ex.: Objetos, closures e funções de ponteiros.
  - Ex.: Realiza testes de tipagem, verificações de tamanho de arrays, etc. (Explicitamente).

#### Otimização de Código

- Reescreve sequências instruções custosas em sequências menos custosas.
  - Ex.: operações com constantes: `3 + 4` → `7`
  - Ex.: Retira uma instrução invariável de um loop
  - Ex.: Paraleliza um loop

![Otimização em Compiladores](./otimizacao_compiladores.png)

#### Geração de Código

- Traduz o código intermediário em código de máquina (ou algum código alvo).
  - Registra atribuições
  - Instruções de seleção
  - Instruções de scheduling
  - Otimização específica para a arquitetura de cada máquina

### Quem deve fazer o CS153?

- Pessoas facinadas por linguagens de programação e compiladores
  - "Por que esta linguagem não inclue essa feature?"
  - Programadores de sistemas
- Conheça a ferramenta que você usa todos os dias
  - "O que o compilador não pode fazer tão bem?"
- Designers de Arquiteturas
  - Interdependência entre compiladores e arquiteturas
  - Veja as falhas do Intel iAPX 432 e Intel Itanium em relação a compiladores
  - Atualmente, o pessoal da arquitetura usa compiladores também!
- Desenvolvedores de APIs
  - Uma linguagem é uma API
  - Ex.: A linguagem Hack do Facebook.

### Conhecimentos adquiridos

- Você vai aprender sobre:
  - Aplicações práticas da teoria
  - Análise léxica, sintática e interpretadores
  - Como linguagens de alto nível são implementadas em código de máquina
  - (Um subconjunto) da arquitetura Intel x86
  - Mais sobre ferramentas de compiladores como GCC e LLVM
  - Um entendimento maior sobre códigos
  - Um pouco sobre semântica das linguagens de programação, análises de programas e tipos
  - Como manipulas estruturas de dados complexas
  - Como ser um melhor programador

### Pré-requisitos sugeridos

- É interessante saber sobre teoria da computação, estruturas de dados e arquitetura de computadores
- A linguagem utilizada será OCaml
  - Como nos materiais originais não haviam, vamos disponibilizar um conjunto de materiais open source, bem como instruções sobre a linguagem e tentar trazer aplicações para o ReasonML, mais semelhante ao Javascript.
  - 