# Ferramentas e Recursos. Como monitorar e Analizar

### 01 - Set statistics

Uma das formas de você identificar se uma qury é lenta ou não é avaliando o quanto ela consome de páginas de dados e recursos do servidor.

Você consegue esses valores usando uma das ferramentas e recursos abaixo:

 - Profiler
 - Extend Events
 - Usando DMVs
 - Estatisticas de Acesso e Tempo
 - Performance Monitor

Nessa aula, vamos ver como usar o editor de query para obter no momento da execução das cosultas, esses valores.

SET STATISTICS IO

Quando ligado e uma instrução é executada, o SQL Server apresenta as estatísticas de acesso ao cache e ao buffer ou a área de disco.

set statistics on -- Ligar a apresentação
set statistics off -- Desligar a apresentação

Quais dados são apresentados:

Para cada tabela envolvida na instrução, é apresentada uma linha com as informações de estatisticas. São elas:

Table 'XXXX'       Nome da Tabela
Scan count         Contagem de buscas para recuperar os dados.
logical reads      Páginas acessadas no Buffer Pool (cache de dados).
physical reads     Páginas acessadas do Disco.
read-ahead reads   Páginas incluidas no Buffer Pool. Chamada leitura antecipada.

Para verificar queries com exemplos da utilização de set statistics on:

https://github.com/JosiTubaroski/Monitorar_Analisar/blob/main/01-Set%20statistics%20IO.sql

### 02 - Client statistics

Um recurso da ferramenta SSMS, é a coleta de informações referentes a execução de comandos e a apresentação após seu término de execução.

De forma semelhante ao SET STATISTICS, o recurso nativo do SMSS
Include Cliente Statistics, apresenta um conjunto de informações

Para mais informações acesse:

https://github.com/JosiTubaroski/Monitorar_Analisar/blob/main/02-Client%20Statistics.sql

### 03 - Profiler

Profiler - Ferramenta para rastrear eventos que ocorrem no lado do servidor de Bando de Dados.

Ref.: https://docs.microsoft.com/pt-br/sql/tools/sql-server-profiler/sql-server-profiler?view=sql-server-2017

Eventos:

São ações criadas por uma instância do SQL SERVER, como:

- Conexões, desconexão e falhas;
- Bloqueios criados e liberados;
- Aumento e Redução do banco de dados;
- Mensagem de erros e avisos.
- Execuções de comandos SELECT, INSERT, UPDATE e DELETE.

Os eventos são agrupados em classes de eventos.

A classe de eventos TSQL, por exemplo, tem os seguintes eventos:

Exec Prepared SQL     Indica que SqlCliente, OLE DB ou DB-Library executou uma ou mais instruções Transact-SQL preparadas.
Prepared SQL          Indica que SqlClient, ODBC, OLE DB ou DB-Library preparou uma ou mais instruções Transact-SQL para uso.
SQL: BatchCompleted   Indica que o Lote Transact-SQL está iniciado.
SQL: BatchStarting    Indica que uma Transact-SQL foi iniciado.
SQL: StmtCompleted    Indica que uma Transact-SQL foi concluida.
SQL: StmtRecompile    Indica recompilações em nível de instrução causadas por todos os tipos de lotes: procedimentos armazenados, gatilhos, lotes ad hoc e consultas.
SQL: StmtStarting     Indica que uma instrução Transact-SQL está iniciado.
Unprepare SQL	        Indica que SqlCliente, ODBC, OLE DB ou DB-Library exclui uma ou mais instruções Transac-SQL preparadas.
Xquery Static Type    Ocorre quando o SQL Server executa uma expressão XQuery.

Coluna de dados

------------

Atributo de uma classe de eventos que foi rastreado pelo Profiler.
Nem todas as colunas são aplicadas para as classes de eventos.
Algumas colunas importantes para o evento: "SQL:StmtCompleted"

SPID       Identificação da Sessão
CPU        Tempo da CPU (em milisegundos) usado pelo evento.
Duração    Período de tempo (em microssegundos) utilizado pelo evento.
Reads      Número de leituras de páginas emitidas pela instrução SQL.
RowCounts  Numero de linhas afetadas por um evento.
TextData   Texto da instrução que foi executada.
Writes     Número de gravações de páginas emitidas pela instrução SQL.

Ref.: https://docs.microsoft.com/pt-br/sql/relational-databases/event-classes/sql-stmtcompleted-event-class?view=sql-server-2017

Filtros

Utilizados para reduzir a quantidade de eventos que são capturados.

Utilizado para reduzir a quantidade de eventos que são capturados.
Eles são criados com base nas colunas de dados e utilizam as regras de condições e expressões padrão.

Mais detalhes verificar

https://github.com/JosiTubaroski/Monitorar_Analisar/blob/main/03-Profiler.sql

### 04 - Performance Monitor

- Ferramenta do Windows que visualiza as estatísticas de contadores de objetos em tempo real do computador local ou de um computador remoto.

- Os objetos podem pertender ao Sistema Operacional como Disco ou Interface de rede ou de um software como o SQL Server.

Algumas caracteristicas.

- Exibe os dados no formato gráfico em linha ao longo do tempo.
- Exibe os dados em formato barra ou texto em tempo real.
- Permite definir o intervalo de captura.
- Salva os dados em arquivo texto
- Permite a leitura de dados gravados.

- Para saber mais acesse:

https://github.com/JosiTubaroski/Monitorar_Analisar/blob/main/05%20-Performance%20Monitor.sql

