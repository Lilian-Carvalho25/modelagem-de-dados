# Comandos SQL para operações de dados (CRUD)

## Resumo

C: CREATE (criar dados usando o comando INSERT)
R: READ (ler os dados usando o comando SELECT)
U: UPDATE (atualizar os dados usando o comando UPDATE)
D: DELETE (excluir os dados usando o comando DELETE)

## INSERT
### Tabela fabricantes

```sql
INSERT INTO fabricantes (nome) VALUES('Microsoft');
INSERT INTO fabricantes (nome) VALUES('Asus');
INSERT INTO fabricantes (nome) VALUES('Dell');

INSERT INTO fabricantes (nome) 
VALUES('Apple'), ('LG'), ('Samsung'), ('Brastemp');
```

### Tabela produtos

```sql
INSERT INTO produtos (nome, descricao, fabricante_id)
VALUES('Ultrabook', 'Laptop de última geração com processador Intel Core i9 e memória de 16 GB RAM.', 3)

INSERT INTO produtos (nome, descricao, fabricante_id)
VALUES('Tablet Android', 'Tablet com a versão 13 do sistema Android, com tela de 10 polegadas e 64 GB de armazenamento.', 6)

INSERT INTO produtos (nome, descricao, fabricante_id)
VALUES('Iphone 13 Pro Max', 'Alta durabilidade, processador XYZ 14, 128 GB de armazenamento, 6 GB de RAM e caro pra caramba.', 4)

INSERT INTO produtos (nome, descricao, fabricante_id)
VALUES('Geladeira', 'Refrigerador frost-free com acesso à internet e bla bla bla.', 7)

INSERT INTO produtos (nome, descricao, fabricante_id)
VALUES('Xbox 123', 'Vídeo-game de última geração.', 1)

INSERT INTO produtos (nome, descricao, fabricante_id)
VALUES('iPad Mini', 'Tablet Apple com tela retina de 4k.', 4)

INSERT INTO produtos (nome, descricao, fabricante_id)
VALUES('Ultrabook', 'Equipamento com processador AMD Ryzen, 12 GB de RAM.', 2)
```

### Ler dados da tabela Produtos

```sql
SELECT * FROM produtos;

SELECT nome FROM produtos;

SELECT nome, descricao FROM produtos;

/* Trazer o nome dos produtos apenas da Apple. WHERE (ONDE) indica a condição */
SELECT nome FROM produtos WHERE fabricante_id = 4;

/*OPERADOR DIFERENTE: != ou <> */
SELECT nome FROM produtos WHERE fabricante_id != 4;
SELECT nome FROM produtos WHERE fabricante_id <> 4;

/* OPERADOR OU: OR */
SELECT nome, descricao FROM produtos
WHERE fabricante_id = 2 OR fabricante_id = 3;

/* ORDEM CRESCENTE (ASC - padrão) */
SELECT nome, descricao FROM produtos ORDER BY nome; 
/* ORDEM DECRESCENTE (DESC) */
SELECT nome, descricao FROM produtos ORDER BY nome DESC; 
/* COUNT(campo especial) é uma função de contagem de registros */
SELECT COUNT(id) FROM produtos;

/* Usando AS para definir um apelido para a coluna de resultados */
SELECT COUNT(id) AS Quantidade FROM produtos;
```

## UPDATE (SEMPRE COM WHERE!!)
```sql
UPDATE fabricantes SET nome = 'Asus do Brasil' WHERE id = 2;

/* Primeiro exercício = Mudando o fabricante da geladeira de Brastemp para Samsung*/
UPDATE produtos SET fabricante_id = 6 WHERE id = 4;
/* Segundo exercício = Mudando o nome de "Xbox 123" para "Xbox One" e mudando a descrição. */
UPDATE produtos SET nome = 'Xbox One', descricao = 'Novo lançamento com parcelamento em 256x.' WHERE id = 5;
```

## DELETE (SEMPRE COM WHERE!!)
```sql
DELETE FROM produtos WHERE id = 3;

--ERRO! Pois já tem produtos relacionados a esse fabricante, para apagar, você tem que se livar dos produtos dependentes.
DELETE FROM fabricantes WHERE id = 1;
```