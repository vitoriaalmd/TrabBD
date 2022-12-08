<h1> Prova de Banco de Dados </h1>

<h2> Criando o banco de dados </h2>

```
create database bdescola
```

<h2> Criando as Tabelas </h2>

Criando a tabela tb_aluno

```
create table tb_aluno( 
codigo_aluno integer primary key, 
nome_aluno varchar(60) not null, 
ano_nasc int, 
email varchar(60), 
sexo varchar not null 
)  
```

Criando a tabela tb_curso

```
create table tb_curso( 
codigo_curso integer primary key, 
nome_curso varchar(60) not null 
) 
```

Criando a tabela tb_matricula

```
create table tb_matricula( 
codigo_curso integer references tb_curso (codigo_curso), 
codigo_aluno integer references tb_aluno (codigo_aluno) 
) 

alter table  
add constraint fk_codigo_curso foreign  key (codigo_curso) references tb_curso(codigo_curso) 
add constraint fk_codigo_aluno foreign  key (codigo_aluno) references tb_aluno(codigo_aluno) 
```

<h2> Inserindo os dados nas tabelas </h2>

Tabela tb_aluno

```
insert into tb_aluno (codigo_aluno, nome_aluno, ano_nasc, email, sexo) 
    values (1,'Josiel Jardim',1974,'josiel@provaSQL.com.br','M');

insert into tb_aluno (codigo_aluno, nome_aluno, ano_nasc, email, sexo) 
    values (2,'Ana Maria',1980,'ana@provaSQL.com.br','F');

insert into tb_aluno (codigo_aluno, nome_aluno, ano_nasc, email, sexo) 
    values (3,'João Pedro',1979,'joao@provaSQL.com.br','M');
```
Tabela tb_curso
```
insert into tb_curso (codigo_curso, nome_curso)
    values (1,'Medicina');

insert into tb_curso (codigo_curso, nome_curso)
    values (2,'Arquitetura');

insert into tb_curso (codigo_curso, nome_curso)
    values (3,'Filosofia');

insert into tb_curso (codigo_curso, nome_curso)
    values (4, 'Informatica');

insert into tb_curso (codigo_curso, nome_curso)
   values (5,'Jornalismo');
```
Tabela tb_matricula
```
insert into tb_matricula (codigo_curso, codigo_aluno)  
    values (1,1);

insert into tb_matricula (codigo_curso, codigo_aluno)  
    values (1,2);

insert into tb_matricula (codigo_curso, codigo_aluno)  
    values (2,3);

insert into tb_matricula (codigo_curso, codigo_aluno)  
    values (5,3);
```

<h1> Resolução da Prova Prática </h1>
<h2> 1ª Questão </h2>
Faça um comando SQL para matricular o aluno "Pedro César" no curso de informática.Os dados devem ser inseridos na tabela TB_MATRÍCULA.

```
select * from tb_aluno
insert into tb_aluno(codigo_aluno, nome_aluno, ano_nasc, email, sexo)
values ('4', 'Pedro César', '1995-06-04', 'pedro@provaSQL.com.br', 'M')
select * from tb_matricula
insert into tb_matricula(codigo_curso, codigo_aluno)
values ('4', '4')
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186429-af1a1a67-b402-4d8d-9c29-eb38b7826505.png"></img>
<img src="https://user-images.githubusercontent.com/114403979/206186442-0047b5c9-f95d-4b70-99e5-2033b8503a11.png"></img>

<h2> 2ª Questão </h2>
Escreva um comando SQL que retorne os nomes dos alunos e do(s) cursos em que estão matriculados.Os dados devem estar ordenados pelo nome do curso.

```
select tb_aluno.nome_aluno, tb_curso.nome_curso
from tb_aluno
inner join tb_matricula
on tb_aluno.codigo_aluno = tb_matricula.codigo_aluno
inner join tb_curso
on tb_curso.codigo_curso = tb_matricula.codigo_curso
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186499-aa04cc46-34ac-4e64-b51f-1843522f754f.png"></img>

<h2> 3ª Questão </h2>
Crie um comando SQL que retorne o e-mail de todos os alunos maiores de idade.

```
select email
from tb_aluno where 2022 - ano_nasc >= 18
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186533-a190cc9f-05e8-4611-a4ea-f29c2c64f3d8.png"></img>

<h2> 4ª Questão </h2>
Desenvolva um comando SQL que mostre o total de alunos.v

```
select count(codigo_aluno)
from tb_aluno
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186568-aa8d2e99-5bd3-437c-a59c-e5c1cbec1640.png"></img>

<h2> 5ª Questão </h2>
Escreva um comando SQL para listar o total de alunos matriculados em cada curso.

```
select tb_curso.nome_curso,
codigo_curso + codigo_aluno as numero_alunos
from tb_curso
inner join tb_aluno
on tb_aluno.codigo_aluno = tb_curso.codigo_curso
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186607-70f17862-97dd-4c9e-8318-ca044ccb31a5.png"></img>

<h2> 6ª Questão </h2>
Desenvolva um comando SQL que retorna o nome de todos os alunos maiores que 18 anos.

```
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/105735037/206178292-be49f604-890b-494c-9a4b-07f093e433c1.PNG"></img>

<h2> 7ª Questão </h2>
Faça um comando SQL que retorna o nome de todas as mulheres.

```
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186706-6570fca1-5caa-41d0-8a2f-c71fc50761dd.png"></img>

<h2> 8ª Questão </h2>
Faça um comando SQL que retorna o nome de todas as mulheres matriculadas no curso de Medicina.

```
select tb_aluno.nome_aluno as mulheres_em_medicina
from tb_aluno
inner join tb_matricula
on tb_matricula.codigo_aluno = tb_aluno.codigo_aluno
and tb_matricula.codigo_curso = 1
and tb_aluno.sexo = 'F'
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186751-fd47532f-a7c7-4ba0-ac4a-5aa069914f5b.png"></img>

<h2> 9ª Questão </h2>
Faça um comando SQL que retorna os nomes dos cursos ordenados por ordem alfabética.

```
select nome_curso
from tb_curo order by nome_curso asc
```
<h3> Resultado </h3>
<img src="https://user-images.githubusercontent.com/114403979/206186768-c63918de-50f1-41da-a721-61b891b4f73e.png"></img>

<h2> 10ª Questão </h2>
Crie o enunciado de uma consulta SQL que utiliza "junção" (com resposta).
Selecione o nome e o curso dos alunos de sexo feminino que estão matriculados no curso de medicina.

```
select nome_aluno, tb_curso.nome_curso as nome_curso from tb_aluno
inner join tb_curso on tb_curso.nome_curso = 'MEDICINA'
where sexo = 'F'
```
<h3> Resultado </h3>
<img src="https://images2.imgbox.com/9b/5b/bbwmo7I8_o.jpeg"></img>

<h1> Resolução das questões teóricas </h1>
<h2> 1ª Questão: Defina: SQL </h2>
SQL é uma linguagem padrão para trabalhar com bancos de dados relacionais. Ela é uma linguagem declarativa e que não necessita de profundos conhecimentos de programação para que alguém possa começar a escrever queries, as consultas e pedidps, que trazem resultados de acordo com o que você está buscando. SQL significa Standard Query Language, literalmente a linguagem padrão para realizar queries.

A linguagem SQL é utilizada de maneira relativamente parecida entre os principais bancos de dados relacionais do mercado: Oracle, MySQL, MariaDB, PostgreSQL, Microsoft SQL Server, entre muitos outros. Cada um tem suas características, sendo o MySQL e o PostgreSQL extremamente populares por possuírem versões gratuitas e de código aberto.

<h2> 2ª Questão: Faça um relacionamento cronológico sobre SQL </h2>
<h4> Década de 60 </h4>
Os computadores se tornam parte efetiva do custo das empresas juntamente com o crescimento da capacidade de armazenamento. Foram desenvolvidos dois principais modelos de dados: modelo em rede (CODASYL - Comitee for Data Systems Language) e o modelo hierárquico (IMS – Information Management System). O acesso ao BD é feito através de operações de ponteiros de baixo nível que unem (link) os registros. Detalhes de armazenamento dependiam do tipo de informação a ser armazenada, desta forma, a adição de um campo extra necessitava de uma reescrita dos fundamentos de acesso/modificação do esquema. Os usuários precisavam conhecer a estrutura física do BD para poder realizar uma consulta.

<h4> Década de 70 </h4>
Muitas discussões a respeito do valor da competição entre os sistemas enquanto a teoria de banco de dados conduz ao objetivo final de projeto de pesquisa. Dois principais protótipos de sistema relacional foram desenvolvidos entre 1974 e 1977 e demonstram um ótimo exemplo de como a teoria conduz a boas práticas.

<h4> Década de 80 </h4>
A Linguagem Estruturada de Consulta – SQL (Structured Query Language) se torna um padrão mundial. A IBM transforma o DB2 como carro chefe da empresa em produtos para BD. Os modelos em rede e hierárquico passam a ficar em segundo plano praticamente sem desenvolvimentos utilizando seus conceitos, porém vários sistemas legados continuam em uso. O desenvolvimento do IBM PC desperta muitas empresas e produtos de BD como: RIM, RBASE 5000, PARADOX, OS/2 Database Manager, Dbase III e IV (mais tarde transformado em FoxBase e mais tarde ainda como Visual FoxPro), Watcom SQL, entre outros.

<h4> Década de 90 </h4>
Tem início uma leve crise econômica nas indústrias e algumas empresas sobrevivem oferecendo alguns produtos a custos muito elevados. O modelo cliente-servidor (client-server) passa a ser uma regra para futuras decisões de negócio e vemos o desenvolvimento de ferramentas de produtividade como Excel/Access (Microsoft) e ODBC, também é marcado como o início dos protótipos de Object Database Management Systems (ODBMS). É quando vemos a explosão da Internet./WWW e uma louca corrida para prover acesso remoto a sistemas de computadores com dados legados. Percebe-se um crescimento exponencial na tecnologia Web/BD. Aumentam o uso de soluções de código aberto (open source) através de gcc, cgi, Apache, MySQL, etc.

<h4> Século 21 </h4>
Vemos a decadência da indústria da Internet de uma maneira geral, mas sólidos crescimentos em aplicações para BD continuam.
Aparecem mais aplicações que interagem com PDAs (Personal Digital Assistant), transações em PDVs, consolidação de vendas, etc.
Três companhias predominam no amplo mercado de BD: IBM (que comprou a Informix), Microsoft e Oracle.

<h2> 3ª Questão: Liste as principais características do SQL </h2>
Sintaxe dos comandos o mais próximo possível da lingua natural inglesa; <br>
Não procedimental: indica-se a informação que se pretende obter sem qualquer preocupação em "como se vai obter". O utilizador não se preocupa com o método de acesso aos dados que fica a cargo do SGBD; <br>
Trabalha com conjuntos de registos e não com um registo de cada vez. Não existem comandos como "Next record" ou "Previus record"; <br>
É utilizada tanto pelos utilizadores normais como pelo DBA (Database Administrator);

<h2> 4ª Questão: Descreva a sintaxe do comando SQL: SELECT. Quais cláusulas são obrigatórias e quais são? </h2>
O comando SELECT é usado para extrair os dados das tabelas de um banco de dados. Ele pode extrair dados de uma ou mais tabelas ao mesmo tempo, executando desde consultas simples até comandos mais complexos, fazendo buscas, junções, filtros comparativos, ordenações e diversos outros itens.

<h2> 5ª Questão: Qual a importância da linguagem SQL no desenvolvimento de softwares atualmente? Justifique. </h2>
O SQL Server, criado pela Microsoft, é muito conhecido e utilizado no mercado. A linguagem usada nessa ferramenta é o T-SQL, e oferece recursos avançados e diferenciados para facilitar a atualização de dados e o armazenamento das informações de forma segura e confiável. O SQL Server atua com sistemas integrados de criptografia, permitindo que a visualização ou alteração das informações sejam feitas apenas pelas pessoas responsáveis, o que garante ainda mais segurança e tranquilidade para os usuários e empresários. É uma alternativa comumente utilizada em lojas online, instituições governamentais, bancos e fábricas dos mais diversos portes.



































