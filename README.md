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
ano_nascimento int, 
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





