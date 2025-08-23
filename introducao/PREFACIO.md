## Sumário

-  [Prefácio](#prefacio)
-  [Glossário](#)
   -  [Projeto Lógico](#projeto-logico)
   -  [Projeto Físico](#projeto-fisico)
   -  [Data warehousing](#data-warehousing)
   -  [Data mining](#data-mining)
   -  [OLAP](#olap)
   -  [Banco de dados orientados a objeto](#banco-de-dados-orientados-a-objeto)
   -  [Banco de dados espaciais](#banco-de-dados-espaciais)
   -  [Acesso a dados na web](#acesso-a-dados-na-web)
   -  [Modelo entidade relacionamento - MER](#modelo-entidade-relacionamento)
   -  [Normalização de banco de dados](#normalizacao-de-banco-de-dados)
   -  [SQL - Structured Query Language](#sql-structured-query-language)
   -  [UML - Unified modeling language](#uml---unified-modeling-language)
   -  [SAD - Sistemas de apoio a decisão](#sistemas-de-apoio-a-decisao)

### Prefacio

-  O modelo relacional permite que o projetista de banco de dados focalize separadamente:
   -  Projeto lógico (relacionaentos de dados e tablelas)
   -  Projeto físico (armazenamento e recuperação dos dados físicos)
-  Tambem existem outros tipos de bancos de dados que tem impacto importante nos no projeto de banco de dados:
   -  Data warehousing
   -  OLAP
   -  Data mining
   -  Bancos de dados orientados a objeto, espaciais e acesso a dados na web.

### Glossario

#### Projeto logico

-  É, em grande parte, dominio dos projetistas de aplicações, que criam a estrutura lógica do banco de dados de acordo com os requisitos de manipulação de dados e consultas estruturadas da aplicação.
-  Usamos a abordagem entidade-relacionamento (ER) para a espacificação de requisitos de dados e modelagem conceitual.
-  Tambem usamos uma outra abordagem dominante de modelagem de dados, a UML (unified modeling language).
-  Voce converte o diagrama ER em um esquema relacional e define (tabelas, colunas, chaves primarias e estrangeiras, restrições de integridade) sem definir ainda tipos físicos ou tamanhos exatos dos campos.

<pre>
model Evento {
  id            Int      @id
  nome          String
  data          DateTime
  organizadorId Int
  participantes EventoParticipante[]
}
</pre>

**Analogia eventos**

-  Define tabelas (Evento, Participante, EventoParticipante), com PKs e Fks.

#### Projeto fisico

-  Define os detalhes de implementação no SGBD real.
-  Define tipos de dados exatos (varchar(255), INT, Date), indices, chaves estrangeiras concretas, etc...

<pre>
model Evento {
  id            Int      @id @default(autoincrement())
  nome          String   @db.VarChar(100)
  data          DateTime
  organizadorId Int      @index
  participantes EventoParticipante[]
}
</pre>

**Analogia eventos**

-  Implementa o banco real.

#### Data warehousing

-  É um banco de dados especializado para analise e tomada de decisão, não para processamento de transações diarias.
-  Tem o objetivo de consolidar dados de multiplas fontes, organizada para consultas complexas e relatorios.
-  É a base do BI (business inteligence).

<pre>
Tabela FatoInscricao
-------------------
id_inscricao
id_evento
id_participante
valor

Tabela DimEvento
----------------
id_evento
nome
data
organizador

Tabela DimParticipante
---------------------
id_participante
nome
idade
</pre>

**Analogia (Eventos)**

-  O data warehouse é o banco que guarda todos os eventos, incrições e participantes ao longo do tempo.
-  Um BI consome esse data warehouse e responde perguntas tipo:
   -  Quantos participantes por evento?
   -  Qual evento teve mais inscrições no ultimo trimestre ?
   -  Quais organizadores tem maior engajamento?

#### OLAP

-  Online Analytical Processing é um conjunto de técnicas e ferramentas para analisar dados armazenados em um Data Warehouse.
-  Permite consultas complexas e multidimensionais com foco em tomada de decisao e analise, nao atualização de dados transacionais.

**Analogia eventos**

-  Data warehouse guarda todos os eventos, participantes e inscrições ao longo do tempo.
-  OLAP é o dashboard de analise que responde perguntas tipo:
   -  Quantos participantes se inscreveram e mcada evento no ultimo trimestre?
   -  Qual organizador teve mais engajamento or faixa etária?
   -  Evolução de inscrições mes a mes.

#### Data mining

-  É o processo de descobrir padroes, tendencias e informações uteis a partir de grandes volumes de dados armazenados em um Data warehouse com foco em extração de conhecimento para apoio á decisao.

**Analogia eventos**

-  Data wirehouse é o banco com todos os eventos, participantes e inscrições.
-  OLAP é o dashboard que response **"quantos participantes se inscreveram por evento/mes"**.
-  Data mining responde **"que tipo de participante tende a se inscrever em eventos de tecnologia"** ou "Quais eventos atraem mais inscritos que nunca faltam?"
   -  Exemplo pratico
      -  Analisar dados de eventos passados para prever demanda futura.
      -  Descobrir padroes de comportamento dos participantes.

#### Banco de dados orientados a objeto

-  é um banco de dados que integra conceitos de orientação a objetos ao modelo de dados com o objetivo de armazenar objetos completos (com atributos e métodos) diretamente no banco, sem precisar quebrar em tabelas relacionais.

#### Banco de dados espaciais

-  permitem armazenar, consultar e analisar dados geográficos, sao usados quando a localização é parte essencial da informação.

#### Acesso a dados na web

-  Manipular informações armazenadas em servidores remotos via protocolos HTTP/HTTPS, geralmente retornando formatos estruturados (JSON) para serem usados em aplicações.
-  Resumidamente consumir a api.

#### Modelo entidade relacionamento

-  É tradicionalmente um método popular para conceituar os requisitos de dados dos usuários.

#### UML - unified modeling language

-  Abordagem dominante de modelagem de dados, tornou-se um método padrão de modelagem de sistemas em grande escala para linguagens orientadas a objeto.

#### SQL structured query language

-  Linguagem padrão para consultar, inserir, atualizar e gerenciar dados em bancos relacionais.

#### Normalizacao de banco de dados

-  É o processo de organizar as tabelas de um banco de dados relacional para reduzir redundancias e garantir consistencia, dividindo os dados em estruturas menores e mais logicas (formas normais).

#### Sistemas de apoio a decisao

-  SAD - São softwares que ajudam gestores a tomar decisoes mais rapidas e embasadas usando dados, modelos analiticos e simulações.
