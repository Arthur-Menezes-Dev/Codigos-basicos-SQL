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

## Codigo 6 - 19/10/2026

-- ctrl + enter já seleciona a linha

CREATE DATABASE mercadinhomerc ; 

USE  mercadinhomerc ;

CREATE TABLE Cliente(
    codigo INT Primary Key Auto_Increment,
    nome VARCHAR(50) NOT NULL,
    estado VARCHAR(2) NOT NULL,
    email VARCHAR(30) NOT NULL,
    data_nascimento DATE NOT NULL
);

CREATE TABLE Endereco(
    CEP VARCHAR(8) NOT NULL,
    logradouro VARCHAR(40) NOT NULL,
    numero VARCHAR(5) NOT NULL,
    codigo_cliente INT UNIQUE,
    FOREIGN KEY (codigo_cliente) REFERENCES Cliente(codigo)
);

CREATE TABLE Pedido(
    codigo INT PRIMARY KEY Auto_Increment,
    data DATE NOT NULL,
    total FLOAT NOT NULL,
    codigo_cliente INT,
    FOREIGN KEY (codigo_cliente) REFERENCES Cliente(codigo)
);

CREATE TABLE Produto(
    codigo INT PRIMARY KEY Auto_Increment,
    descricao VARCHAR(20) NOT NULL,
    preco_unitario FLOAT NOT NULL
);

CREATE TABLE ItemPedido(
    codPed INT NOT NULL,
    codProd INT NOT NULL,
    quantidade INT NOT NULL,
    subtotal FLOAT NOT NULL,
    PRIMARY KEY (codPed,codProd),
    FOREIGN KEY (codPed) REFERENCES Pedido(codigo),
    FOREIGN KEY (codProd) REFERENCES Produto(codigo)
);

/* DADOS DOS CLIENTES */
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(1,'Maria Francisca','SP','maria@eumesma.com.br','1990-07-15');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(2,'Joana Castro ','SP','joana@hotmail.com.br','2000-07-15');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(3,'Fernando Lima','MG','fernando@gmail.com.br','1990-04-06');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(4,'Janio Francisco','ES','janio@hotmail.com.br','1996-08-10');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(5,'Robson Nascimento','RJ','robson@hotmail.com.br','2000-05-05');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(6,'Luiz Carlos','RJ','luiz@gmail.com.br','1980-07-05');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(7,'Keila Lopes','MG','keila@hotmail.com.br','1983-12-15');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(8,'Paula Silva','PR','paula@empresa.com.br','1990-09-07');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(9,'Roberto Simões','SP','roberto@empresa.com.br','1979-02-03');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(10,'Maria das Graças','PR','mariag@eumesma.com.br','1990-07-15');

/* ENDEREÇO DE CADA CLIENTE */
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('12345678','Rua Cariri','145',1);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('23456789','Rua Bastos Limões','234',2);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('34567890','Av Rebouças','1380',3);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('45678901','Av. Consolação','100',4);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('56789012','Rua Gentil de Mais','300',5);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('67890123','Travessa Tumba','476',6);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('78901234','Rua Mandei Cunha','569',7);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('89012345','Av Mantido Vivo','521',8);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('90123456','Rua Sandra Rosa Madalena','2315',9);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('01234567','Travessa Passanao','15',10);

/* PEDIDO */
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(1,'2020-01-02',46.77,1);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(2,'2020-03-03',30.95,1);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(3,'2020-04-10',100.63,2);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(4,'2020-05-12',63.52,2);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(5,'2020-06-15',86.30,2);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(6,'2020-07-07',96.10,3);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(7,'2020-08-20',300.40,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(8,'2020-09-20',55.60,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(9,'2020-10-26',245.66,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(10,'2020-11-28',320.63,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(11,'2020-12-30',630.98,5);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(12,'2020-04-08',358.12,5);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(13,'2020-02-06',147.96,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(14,'2020-03-09',368.45,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(15,'2020-04-11',278.23,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(16,'2020-05-16',630.52,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(17,'2020-06-19',128.75,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(18,'2020-07-22',635.42,7);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(19,'2020-08-27',322.15,7);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(20,'2020-09-29',745.15,8);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(21,'2020-10-30',520.36,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(22,'2020-11-05',396.46,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(23,'2020-12-07',20.36,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(24,'2020-01-08',985.75,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(25,'2020-02-14',1030.63,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(26,'2020-03-18',423.62,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(27,'2020-04-21',460.77,10);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(28,'2020-05-23',412.86,10);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(29,'2020-06-18',98.17,10);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(30,'2020-07-30',63.52,10);

/* PRODUTO */
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(1, 'Sabão',8);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(2, 'Sabonete',1.39);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(3, 'Macarrão',2.79);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(4, 'Miojo',1.6);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(5, 'Detergente',1.75);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(6, 'Refrigerante',4);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(7, 'Café',9.5);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(8, 'Chocolate',6.35);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(9, 'Chá',4.55);


/* ITENS DO PEDIDO */
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(1,1,4,32);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(1,3,3,8.37);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(1,4,4,6.40);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(2,1,3,24);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(2,2,5,6.95);



select * from cliente;

select * from pedido where codigo_Cliente=1;

select * from ItemPedido where codped= 1;

select * from produto where codigo in(1,3,4);

select * from Cliente,Pedido where Cliente.codigo = Pedido.codigo_cliente; 

  -- carry é consulta no Banco de Dados
  
-- Esse comando mostra todos os pedidos da cliente maria francisca
select Cliente.codigo,Cliente.nome,Cliente.estado,Cliente.email,Pedido.codigo,Cliente.data_nascimento,Pedido.data,Pedido.total
	from Cliente c,Pedido p 
    where Cliente.codigo = Pedido.codigo_cliente 
		and nome='Maria Francisca'; 
        
-- o c é um apelido eo p tb. c é apelido pra cliente e o p para produto. Assim podemos colocar acima

select c.codigo,c.nome,c.estado,c.email,p.codigo,c.data_nascimento,p.data,p.total
	from Cliente c,Pedido p 
    where c.codigo = p.codigo_cliente 
		and nome='Maria Francisca'; 
        	

-- mostrar todos os produtos do codigo 2
    select ped.data,prod.descricao,prod.preco_unitario,item.quantidade,item.subtotal,item.subtotal,ped.total
		from pedido ped, itemPedido item, Produto prod
        where ped.codigo = item.codped
			and prod.codigo = item.codprod 
            and ped.codigo = 2;
			

-- Padrão ANSI89
-- mostrar todos os pedidos da Maria Francisca e Todos os Produtos de cada Pedido

select cli.nome, ped.codigo, ped.data,prod.descricao,prod.preco_unitario,item.quantidade,item.subtotal,item.subtotal,ped.total
		from Cliente cli, Pedido ped, ItemPedido item, Produto prod
        where cli.codigo = ped.codigo_cliente
        and ped.codigo = item.codped
        and prod.codigo = item.codped
        and cli.nome = 'Maria Francisca';
        
-- modo do professor criar as queries dele 1 from, 2 definir a pk e a fk 3 and 4 select as colunas 
