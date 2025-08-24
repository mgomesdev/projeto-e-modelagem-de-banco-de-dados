-  [Introdução](#introducao)
-  [Papeis](#papeis)
   -  [Projetistas de aplicação](#projetistas-de-aplicacao)
   -  [DBA](#dba---database-administrator)
-  [Dados e gerenciamento de banco de dados](#dados-e-gerenciamento-de-bancos-de-dados)
   -  [Item de dados](#item-de-dados)
   -  [Banco de dados](#banco-de-dados)
   -  [SGBD - Sistema gerenciador de banco de dados](#sgbd---sistema-gerenciador-de-banco-de-dados)
-  [O ciclo de vida do banco de dados](#o-ciclo-de-vida-do-banco-de-dados)
   -  [Análise de requisitos](#análise-dos-requisitos)
   -  [Projeto lógico](#projeto-logico)
   -  [Projeto físico](#projeto-fisico)
   -  [Implementação, monitoração e modificação de bancos de dados](#implementação-monitoração-e-modificação-de-bancos-de-dados)
-  [Modelagem de dados conceitual](#modelagem-de-dados-conceitual)
   -  [Resumo](#resumo)
   -  [Dicas](#dicas)

## Introducao

-  Os sistemas relacionais continuam sendo a tecnologia de banco de dados dominante nas empresas comerciais.
-  Este livro foca no projeto lógico de banco de dados relacionais mais populares.

### Papeis

#### Projetistas de aplicacao

-  O projeto lógico, ou seja, a estrutura dos relacionamentos básicos dos dados e a sua definição em um determinado sistema de banco de dados é em grande parte de dominio dos projetistas de aplicação.

#### DBA - Database administrator

-  O projeto físico, ou seja, a implementação do armazenamento e recuparação de dados é normalmente de dominio do administrador de banco de dados (Database administrator - DBA).

### Dados e gerenciamento de bancos de dados

#### Item de dados

-  É o componente básico de um arquivo em um sistema de arquivos, por exemplo, sobrenome, nome, nome da rua etc...
-  Um grupo de itens de dados relacionados, é chamado de registro, ex: pedido, vendedor, cliente, produto etc...
-  Em um banco de dados relacional, um item de dados é chamado de coluna ou atributo;
   -  Um registro é chamado de linha ou tupla;
   -  e um arquivo é chamado de tabela.

#### Banco de dados

-  São coleções inter-relacionadas de muitos tipos diferentes de tabelas.

#### SGBD - Sistema gerenciador de banco de dados

-  É um software para manipular banco de dados de forma visual para facilitar.
-  Por ex: prisma studio, mysql workbench etc...

### O ciclo de vida do banco de dados

-  Incorpora os passos básicos envolvidos no projeto de um esquema global do banco de dados lógico e a definição de esquemas locais especificos do SGBD e depois o ciclo de vida continua com a implementação e a manutaenção do banco de dados.
-  No processo de projetar bancos de dados, passamos desde a modelagem de requisitos até o projeto lógico, usando uma serie de diagramas.

#### Análise dos requisitos

-  Os requisitos do banco de dados sao determinados por meio de entrevistas com os produtores e os usuarios dos dados;
-  As informações sao usadas para produzir uma especificação formal de requisitos.
-  Essa especificação inclui os dados exigidos para o processamento, relacionamentos, plataforma de software para implementação do banco de dados.

#### Projeto logico

-  O esquema global, um diagrama d emodelo conceitual qu emostra todos os dados e seus relacionamentos.
   -  **modelagem conceitual de dados**: Os requisitos de dados são analisados e modelados por meio de um diagrama ER e UML.
      -  Mostra uma possivel representação do modelo ER do banco de dados de produto/cliente na mente do usuario final.
   -  **integração da visão**: quando possui varias visoes dos dados e relacionamentos, para evitar inconsistencias e eliminar redundancias do modelo, essas visoes precisam ser consolidadas em uma unica visao global.
   -  **transformação do modelo de dados concitual em tabelas SQL**: cada relacionamento e suas entidades associadas são transformadas em um conjunto de tabelas relacionais especificas dO SGBD.
   -  **normalização de tabelas**: as tabelas são divididas em tabelas menores por meio de técnicas padronizadas.

#### Projeto fisico

-  Envolve a representação precisa da realidade.
-  São feitas otimizações de desempenho das consultas e eliminação de redundancias.

#### Implementação, monitoração e modificação de bancos de dados

-  O banco de dados é implementado usando a linguagem SQL.

### Modelagem de dados conceitual

-  É o principal componente do projeto lógico de banco de dados.
-  Foram formalizados na década de 1960.
-  A técnica entidade relacionamento - ER para modelagem de dados conceitual foi representada inicialmente em 1976 por Peter Chen.
-  A UML foi introduzida em 1997 por Grady Booch e James Rumbaugh e tornou-se a linguagem padrão de modelagem de software de grande escala.
-  O objetivo do ER está na simplicidade e legibilidade e capturar os requisitos do mundo real de uma maneira simples e significativa, que seja inteligivel pelo projetista de banco de dados e pelo usuario final.

### Resumo

-  O conhecimento de modelagem de dados é importante para os desenvolvedores.
-  O ciclo de vida mostra as etapas necessárias para o projeto de um banco de dados, desde o projeto lógico até o projeto fósico.
-  Os modelos de dados ER e UML são comprovadamente os mais populares em uso hoje em dia devido a simplicidade e legibilidade.

### Dicas

-  Trabalhe metodicamente pelas etapas do ciclo de vida
-  Corrija erros o mais cedo possivel.
-  Separe o projeto lógico e fisico completamente.
-  Projeto logico: obter uma solução viavel para otimização do projeto fisico.
-  Projeto fisico: consultas e atualizações conhecidas e projetadas.
