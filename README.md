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



