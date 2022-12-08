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
