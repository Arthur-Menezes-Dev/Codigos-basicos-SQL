# Codigos-basicos-SQL
Alguns codigos basicos SQL feitos em classe. Repositorio criado em (19/10/2026)

## Codigo 1

-- linguagem sql (structured query language)

-- DML (data manipilation language) Insert Delete Update Select 

-- DDL ( Data definition Language) Create Alter Drop

CREATE DATABASE produtodbd; 

USE produtodbd;

CREATE TABLE produtodb(
	id int,
	produto varchar (25),
	quantidade int,
	preco float
);

ALTER TABLE produtodb ADD COLUMN perecivel char (1);
ALTER TABLE produtodb MODIFY COLUMN produto char (35);
ALTER TABLE produtodb RENAME COLUMN quantidade TO qt;
ALTER TABLE produtodb RENAME TO tb_produto;
ALTER TABLE tb_produto DROP COLUMN preco; 
ALTER TABLE tb_produto ADD COLUMN precos float;

DROP TABLE tb_produto;

CREATE TABLE produtodb(
	id int,
	produto varchar (25),
	quantidade int,
	preco float
);

DROP TABLE produtodb;

desc produtodb;


## Codigo 2

-- Constraints (Restrições ) 
-- unique (Não permite valores repetidos na coluna) 
-- Not Null (Não permite colunas com valores nulos)]
-- Default (Insere um valor padão caso não esteja na inserção ou alteração) 
-- Primary Key 
-- Foreing Key

CREATE TABLE produtodb(
	id int unique not null,
	produto varchar (25) not null,
	quantidade int not null default 100,
	preco float not null
);

DROP TABLE produtodb;

insert into produtodb(id,produto,preco) values(1,'Teclado',35);
insert into produtodb(id,produto,quantidade,preco) values(2,'Monitor',100,600);

select * from produtodb;

desc produtodb;



## Codigo 3

CREATE DATABASE recursos_humanos; 

USE recursos_humanos;

CREATE TABLE funcionario(
	matricula int PRIMARY KEY auto_increment,
    nome varchar(30) not null,
    salario float not null default 1621,
    codigo_departamento int not null,
    foreign key (codigo_departamento) references departamento(codigo)
);

insert into funcionario(nome,codigo_departamento) values
	('Pedro Ramos',1);
    
  insert into funcionario(matricula,nome,codigo_departamento) values
	(5,'Humberto Costa',3);
 	(6,'Janice Arruda',2);   
    
  select * from funcionario;

CREATE TABLE departamento(
codigo int PRIMARY KEY auto_increment,
departamento varchar(15) not null,
ramal int not null
);


insert into departamento(departamento,ramal)values 
	('TI',222),
    ('financeiro', 555),
    ('administrativo', 123);
    
  select * from departamento;

  ## Codigo 4

  CREATE DATABASE Confeitariadb; 

USE Confeitariadb ;

CREATE TABLE produtotb(
	codigo_Produto int PRIMARY KEY auto_increment,
    nome_Produto varchar(30) not null,
	valor_Compra float not null,
    quantidade_Estoque int not null,
    fornecedor int not null,
    foreign key (fornecedor) references fornecedortb(num_Fornecedor)
);

CREATE TABLE fornecedortb(
nome_Fornecedor  varchar(15) ,
num_Fornecedor int not null PRIMARY KEY,
cidade_Fornecedor varchar(15) not null,
estado_Fornecedor varchar (2) not null
);

drop database Confeitariadb ;

insert into departamento(departamento,ramal)values 
	('TI',222),
    ('financeiro', 555),
    ('administrativo', 123);
    
  select * from departamento;

  ## Codigo 5

  create database mercadinho;

use mercadinho;

create table Cliente(
	id int primary key auto_increment,
    nome varchar(30) not null,
    id_endereco int unique not null, 
    foreign key (id_endereco) references Endereco(id)
);

create table Endereco(
	id int primary key auto_increment,
	logradouro varchar(50) not null
);

create table pedido(
	id int primary key auto_increment,
    data date not null,
    valor_total float not null,
    id_cliente int not null, 
    foreign key (id_cliente) references Cliente(id)
);

create table produto(
	id  int primary key auto_increment,
    produto varchar(20) not null,
    preco_unitario float not null

);

create table Itens_pedido(
	id_pedido int not null,
    id_produto int not null,
    quantidade int not null,
    subtotal float not null,
    primary key (id_pedido,id_produto), -- cria chave primaria composta por 2 colunas
    foreign key (id_pedido) references Pedido(id),
    foreign key (id_produto) references Pedido(id), -- Separadas as colunas são foreign, juntas são primary key

);
