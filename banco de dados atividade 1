-- Criação de tabelas (produtos, clientes e vendas)

create table produtos(
    id_produto int AUTO_INCREMENT primary key,
    nome varchar(100),
    categoria varchar(50),
    preco decimal(10,2),
    estoque int
);

-- id_produto = Referência de cada produto, ex(produto01, produto02, produto03...). 
-- INT = Deve conter valores interios >0 (int) ex(1,2,3...). 
-- AUTO_INCREMENT = É auto incrementável, pois será criado um novo número a cada linha criada na tabela. 
-- primary key = Pois será preciso para relacionar com outras tabelas.
-- nome = Marca e modelo do produto contendo no máximo 100 caracteres.
-- categoria = Tipo do produto ex:(Caixa de som, Smartphone, Fita de led...).
-- preço = Valor do produto máximo de 10 dígitos e 2 casas decimais (Formatação de moeda) Ex:(0000000000.00)
-- Estoque = Quantidade desponível, contendo valores inteiros.

CREATE TABLE clientes(
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(320),
    telefone VARCHAR(12)
);

-- id_cliente = Referencia cada cliente, ex(cliente01, cliente02, cliente03...).
-- nome = Nome do cliente contendo no máximo 100 caracteres.
-- email = Correio eletrônico do cliente contendo no máximo 320 caracteres, incluindo nome (antes do @) e domínio (depois do @).
-- telefone = número de telefone do cliente contendo no máximo 12 caracteres, "DDD 9 0000-0000".

CREATE TABLE vendas(
    id_venda int AUTO_INCREMENT PRIMARY KEY,
    id_cliente INT,
    id_produto INT,
    quantidade INT,
    data_venda DATE,
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente),
    FOREIGN KEY (id_produto) REFERENCES produtos(id_produto)
);

-- id_venda = Referencia cada venda, ex(venda1, venda2, venda3...).
-- id_cliente = É a chave estrangeira da tabela clientes referenciando o id respectivo.
-- id_produto = É a chave estrangeira da tabela produtos referenciando o id respectivo.
-- quantidade = Referente ás unidades de um produto vendido.
-- data-venda = Referente á data de uma venda no formato (AAAA-MM-DD).

-- Inserção de dados nas tabelas (produtos, clientes e vendas)

-- Insert into = "Oque/Onde você quer inserir dados?" Se tabela "Quais serão as colunas que ela terá?"
-- values = inserir linhas de dados nas respectivas colunas. Ex: ("dado da coluna 1", "dado da coluna 2...");

insert into produtos (nome, categoria, preco, estoque)
values
('Camiseta', 'Roupas', 29.99, 100),
('Calça Jeans', 'Roupas', 79.90, 50),
('Tênis Esportivo', 'Calçados', 149.99, 30),
('Relógio Digital', 'Acessórios', 199.99, 20),
('Fone de Ouvido', 'Eletrônicos', 89.90, 75),
('Caneta Esferográfica', 'Papelaria', 2.50, 200);

insert into clientes (nome, email, telefone)
values
('João Silva', 'joao.silva@email.com', '11987654321'),
('Maria Oliveira', 'maria.oliveira@email.com', '2187654321'),
('Carlos Pereira', 'carlos.pereira@email.com', '31987654321'),
('Ana Costa', 'ana.costa@email.com', '61987654321'),
('Lucas Santos', 'lucas.santos@email.com', '11912345678');

insert into vendas (id_cliente, id_produto, quantidade, data_venda)
values
(1, 5, 2, '2023-09-10'),
(2, 2, 3, '2023-09-06'),
(4, 1, 1, '2023-08-21'),
(3, 3, 1, '2023-06-15'),
(3, 4, 2, '2022-06-15'),
(5, 1, 2, '2023-04-01'),
(2, 1, 1, '2023-03-11'),
(1, 5, 10, '2023-03-05'),
(5, 4, 1, '2015-01-01'),
(4, 3, 1, '2019-12-20'),
(4, 4, 1, '2020-12-20');

-- Atualização de dados tabela produtos

-- update = Solicitação de qual campo estou querendo atualizar "É uma tabela?", "Qual delas?".
-- set = "Qual coluna você quer alterar" e "Qual é o novo valor a ser inserido?", neste caso.
-- where = "Qual matrícula associada a esta coluna receberá esta atualização?" 

update produtos 
set preco = 1600.00 
where id_produto = 1;

-- Atualização de dados tabela clientes

update clientes
set telefone = "011963544890"
where id_cliente = 1;

-- Remoção de dados da tabela produtos

-- delete from = "O que você quer remover?". Neste caso estaremos removendo um dado de uma tabela.
-- where = "Qual dado você quer que sobre a alteração?" e "De qual coluna?".

-- solucionar problema da função delete
delete from produtos 
where id_produto = 2;

delete from vendas
where id_venda = 2; 

-- Remoção de dados da tabela clientes

delete from clientes
where id_cliente = 5;

SELECT * FROM Vendas WHERE id_cliente = 5;

-- 2. Remova as referências
DELETE FROM Vendas WHERE id_cliente = 5;

-- 3. Deletar o cliente
DELETE FROM Clientes WHERE id_cliente = 5;

delete from venda
where id_venda = 5;

-- selecionando dados


select nome preco
from produtos
where preco > 15.00;

select vendas.id_venda, clientes.nome, produtos.nome as produto, vendas.quantidade, vendas.data_venda
from vendas
join clientes on vendas.id_cliente = clientes.id_cliente
join produtos on vendas.id_produto = produtos.id_produto
where clientes.id_cliente = 4;

select data_venda, count(*) as total_vendas
from vendas
group by data_venda;

select produtos.categoria, sum(vendas.quantidade) as total_vendido
from vendas
join produtos on vendas.id_produto = produtos.id_produto
group by produtos.categoria;

-- listando os produtos de forma ascendente
 
select * from produtos
order by nome asc;

-- listando os produtos de forma descendente

select * from produtos
order by nome desc;produtos

-- DESAFIOS ADICIONAIS
    -- 1 Calcular o estoque atual de cada produto
 
select
    p.nome,
    p.estoque - coalesce(sum(v.quantidade), 0) as estoque_atual
from
    produtos p
left join
    vendas v on    p.id_produto = v.id_produto
group by
    p.id_produto, p.nome, p.estoque;

    -- 2 Identificar os produtos mais vendidos

select
    p.nome,
    sum(v.quantidade) as total_vendido
from
    produtos p
join
    vendas v on p.id_produto = v.id_produto
group by
    p.id_produto, p.nome
order by
    total_vendido desc;

    -- 3 Listar os clientes que mais compram em quantidade de produtos

SELECT 
    c.nome, 
    SUM(v.quantidade) AS total_comprado
FROM 
    clientes c
JOIN 
    vendas v ON c.id_cliente = v.id_cliente
GROUP BY 
    c.id_cliente, c.nome
ORDER BY 
    total_comprado DESC;
