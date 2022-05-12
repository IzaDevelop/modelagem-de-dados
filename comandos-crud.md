## Comandos CRUD SQL

## Resumo da sigla
C -> CREAT (ISERT, inserir dados)
R -> READ (SELECT, leitura de dados)
U - UPDATE (UPDATE, atualizar dados)
D -> DELETE (DELETE, excluir dados)

## INSERT

### INSERT Fabricantes
INSERT INTO fabricantes(nome) VALUES('Asus');
INSERT INTO fabricantes(nome) VALUES('Dell');
INSERT INTO fabricantes(nome) VALUES('Apple');
INSERT INTO fabricantes(nome) VALUES('LG');

INSERT INTO fabricantes(nome) 
VALUES ('Samsung'),('MicroSoft'),('Brastemp');

### INSERT produtos
INSERT INTO produtos(nome, preco, quantidade, descricao, fabricantes_id) VALUES('TV LED', 2000, 5, 'TV de última geração', 5);

INSERT INTO produtos(nome, preco, quantidade, descricao, fabricantes_id) VALUES('Iphone XYZ', 5500.79, 8, 'Smartphone caro para caramba', 3);

INSERT INTO produtos(nome, preco, quantidade, descricao, fabricantes_id) VALUES
('Geladeira', 1500, 10, 'Refrigerador Frost-free com acesso à Internet das Coisas e bla bla bla', 7),
('iPad Mini', 5000, 8, 'Tablet Apple com tela retina display de 4k, memória interna de 64GB, acesso ao iCloud.', 3),
('Xbox', 2500, 6, 'Console de última geração com acesso aos melhores jogos e bla bla', 6),
('Ultrabook', 4500.68, 12, 'Equipamento com processador AMD Ryzen5, 12GB de RAM, placa de vídeo RTX', 1),
('Headset', 120, 9, 'Fone de ouvido USB com alta qualidade', 6),
('Tablet Android', 4999, 3, 'Tablet com a versão 12 do sistema operacional da Google, possui tela de 10 polegadas e armazenamento de 64GB.', 5);

## SELECT
SELECT nome, preco FROM produtos;
SELECT preco, nome FROM produtos;

SELECT nome, preco FROM produtos WHERE preco < 3000;

SELECT nome, preco FROM produtos 
WHERE preco < 3000 AND preco > 2000;

SELECT nome, preco FROM produtos 
WHERE fabricantes_id = 3 OR fabricantes_id = 1;

SELECT nome, quantidade FROM produtos 
WHERE fabricantes_id = 5 AND preco < 4000;

SELECT nome, descricao FROM produtos
ORDER BY nome; -- CRESCENTE (padrão)

SELECT nome, descricao FROM produtos
ORDER BY nome DESC; -- DECRESCENTE

SELECT nome, descricao, preco FROM produtos
ORDER BY preco; -- CRESCENTE (padrão)

SELECT nome, descricao, preco FROM produtos
ORDER BY preco DESC; -- DECRESCENTE

SELECT 
    produtos.nome AS Produto, 
    fabricantes.nome AS Fabricante, 
    produtos.preco AS Preço, 
    produtos.quantidade AS Quantidade
FROM produtos INNER JOIN fabricantes
ON produtos.fabricantes_id = fabricantes.id;

-- INNER JOIN é um comando que permite juntar uma ou mais tabelas
-- ON é um comando para indicar a maneira como as tabelas são juntadas
-- AS é um comando que permite dar uma apelido para as colunas 

## UPDATE
UPDATE fabricantes SET nome = 'LG do Brasil'
WHERE id = 4; -- sempre use WHERE, sempre de uma condição


## DELETE
DELETE FROM produtos
WHERE id = 5; -- sempre use WHERE, sempre de uma condição