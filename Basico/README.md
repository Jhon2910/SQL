# 🍕 Estudos SQL - Projeto Pizzaria

Anotações básicas de SQL utilizando PostgreSQL.

---

# 📌 Criando Banco de Dados

```sql
CREATE DATABASE pizzaria;
```

---

# 📌 Criando Tabelas

## Tabela de Usuários

```sql
CREATE TABLE usuarios(
    id SERIAL PRIMARY KEY,
    nome VARCHAR(50) NOT NULL,
    email VARCHAR(50) NOT NULL,
    data_nascimento DATE NOT NULL,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Explicação

| Comando | Função |
|----------|--------|
| `SERIAL` | Cria IDs automáticos |
| `PRIMARY KEY` | Chave primária da tabela |
| `NOT NULL` | Campo obrigatório |
| `CURRENT_TIMESTAMP` | Data e hora atuais |

---

## Tabela de Pedidos

```sql
CREATE TABLE pedidos(
    codigo_pedido SERIAL PRIMARY KEY,
    usuario_id INT REFERENCES usuarios(id),
    data_pedido TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Explicação

| Comando | Função |
|----------|--------|
| `REFERENCES usuarios(id)` | Cria relacionamento entre tabelas |
| `usuario_id` | Liga o pedido ao usuário |

---

# 📌 Inserindo Dados

## Inserir Usuário

```sql
INSERT INTO usuarios(nome,email,data_nascimento)
VALUES(
    'Jonathan Alexandre',
    'jonathanalexandre2910@gmail.com',
    '2002-10-29'
);
```

## Inserir Pedido

```sql
INSERT INTO pedidos(usuario_id)
VALUES(3);
```

---

# 📌 Consultas SELECT

## Mostrar todos os usuários

```sql
SELECT * FROM usuarios;
```

---

## Selecionar colunas específicas

```sql
SELECT nome, email
FROM usuarios;
```

---

## Buscar usuários que começam com J

```sql
SELECT *
FROM usuarios
WHERE nome LIKE 'J%';
```

---

## Buscar usuários que terminam com "a"

```sql
SELECT *
FROM usuarios
WHERE nome LIKE '%a';
```

---

## Buscar usuários que possuem "an"

```sql
SELECT *
FROM usuarios
WHERE nome LIKE '%an%';
```

### Caracteres do LIKE

| Operador | Significado |
|----------|-------------|
| `%` | Qualquer quantidade de caracteres |
| `_` | Apenas um caractere |

Exemplo:

```sql
SELECT *
FROM usuarios
WHERE nome LIKE 'J_n%';
```

---

# 📌 ILIKE (PostgreSQL)

Ignora letras maiúsculas e minúsculas.

```sql
SELECT *
FROM usuarios
WHERE nome ILIKE 'j%';
```

---

# 📌 Operadores de Comparação

| Operador | Significado |
|----------|-------------|
| `=` | Igual |
| `!=` ou `<>` | Diferente |
| `>` | Maior |
| `<` | Menor |
| `>=` | Maior ou igual |
| `<=` | Menor ou igual |

Exemplo:

```sql
SELECT *
FROM usuarios
WHERE id >= 3;
```

---

# 📌 BETWEEN

Busca valores dentro de um intervalo.

```sql
SELECT *
FROM usuarios
WHERE id BETWEEN 2 AND 5;
```

Também funciona com datas.

```sql
SELECT *
FROM usuarios
WHERE data_nascimento
BETWEEN '2000-01-01' AND '2005-12-31';
```

---

# 📌 IN

Verifica se o valor pertence a uma lista.

```sql
SELECT *
FROM usuarios
WHERE id IN (1,3,5,7);
```

Equivale a:

```sql
WHERE id=1
OR id=3
OR id=5
OR id=7;
```

---

# 📌 NOT IN

```sql
SELECT *
FROM usuarios
WHERE id NOT IN (2,4,6);
```

---

# 📌 IS NULL

Busca valores nulos.

```sql
SELECT *
FROM usuarios
WHERE email IS NULL;
```

---

# 📌 IS NOT NULL

```sql
SELECT *
FROM usuarios
WHERE email IS NOT NULL;
```

---

# 📌 DISTINCT

Remove registros duplicados.

```sql
SELECT DISTINCT nome
FROM usuarios;
```

---

# 📌 ORDER BY

## Crescente

```sql
SELECT *
FROM usuarios
ORDER BY nome ASC;
```

## Decrescente

```sql
SELECT *
FROM usuarios
ORDER BY nome DESC;
```

---

# 📌 LIMIT

Retorna apenas uma quantidade específica de registros.

```sql
SELECT *
FROM usuarios
LIMIT 5;
```

---

# 📌 OFFSET

Pula registros.

```sql
SELECT *
FROM usuarios
LIMIT 5 OFFSET 5;
```

---

# 📌 COUNT

Conta registros.

```sql
SELECT COUNT(*)
FROM usuarios;
```

---

# 📌 MAX

Maior valor.

```sql
SELECT MAX(id)
FROM usuarios;
```

---

# 📌 MIN

Menor valor.

```sql
SELECT MIN(id)
FROM usuarios;
```

---

# 📌 AVG

Calcula média.

```sql
SELECT AVG(id)
FROM usuarios;
```

---

# 📌 SUM

Soma valores.

```sql
SELECT SUM(id)
FROM usuarios;
```

---

# 📌 WHERE

Filtra registros.

```sql
SELECT *
FROM usuarios
WHERE id > 3;
```

---

# 📌 AND

Todas as condições devem ser verdadeiras.

```sql
SELECT *
FROM usuarios
WHERE id > 2
AND nome LIKE 'J%';
```

---

# 📌 OR

Pelo menos uma condição deve ser verdadeira.

```sql
SELECT *
FROM usuarios
WHERE id = 1
OR id = 5;
```

---

# 📌 NOT

Inverte uma condição.

```sql
SELECT *
FROM usuarios
WHERE NOT id = 1;
```

---

# 📌 Atualizando Dados

```sql
UPDATE usuarios
SET email='jonathanalexandre@gmail.com'
WHERE id=1;
```

⚠️ Sempre utilize `WHERE` no `UPDATE`.

---

# 📌 Deletando Dados

```sql
DELETE FROM usuarios
WHERE id=2;
```

⚠️ Sempre utilize `WHERE` no `DELETE`.

---

# 📌 Alterando Tabelas

## Adicionar coluna

```sql
ALTER TABLE usuarios
ADD COLUMN idade SMALLINT DEFAULT 0;
```

---

## Alterar tipo

```sql
ALTER TABLE usuarios
ALTER COLUMN idade TYPE INT;
```

---

## Renomear coluna

```sql
ALTER TABLE usuarios
RENAME COLUMN idade TO idade_usuario;
```

---

## Remover coluna

```sql
ALTER TABLE usuarios
DROP COLUMN idade_usuario;
```

---

# 📌 Excluir Tabela

```sql
DROP TABLE usuarios;
```

---

# 📌 Excluir Banco

```sql
DROP DATABASE pizzaria;
```

---

# 📌 Conceitos Importantes

| Conceito | Explicação |
|----------|------------|
| CRUD | Create, Read, Update, Delete |
| PRIMARY KEY | Identificador único |
| FOREIGN KEY | Relacionamento entre tabelas |
| SELECT | Consulta dados |
| INSERT | Insere dados |
| UPDATE | Atualiza dados |
| DELETE | Remove dados |
| ALTER TABLE | Altera a estrutura da tabela |
| DROP | Remove banco, tabela ou coluna |
| WHERE | Filtra registros |
| LIKE | Busca padrões |
| ILIKE | Busca ignorando maiúsculas/minúsculas (PostgreSQL) |
| BETWEEN | Intervalo de valores |
| IN | Lista de valores |
| DISTINCT | Remove duplicados |
| LIMIT | Limita quantidade de registros |
| OFFSET | Pula registros |
| COUNT | Conta registros |
| AVG | Calcula média |
| SUM | Soma valores |
| MAX | Maior valor |
| MIN | Menor valor |

---

# 📌 Próximos Estudos

- JOIN
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL JOIN
- CROSS JOIN
- GROUP BY
- HAVING
- UNION
- UNION ALL
- CASE
- COALESCE
- Subqueries
- Views
- CTE (WITH)
- Procedures
- Functions
- Triggers
- Transactions
- Indexes
- Constraints
- Normalização (1FN, 2FN, 3FN)

---

# 🚀 Objetivo

Praticar SQL para desenvolvimento backend e banco de dados relacionais, dominando desde consultas básicas até recursos avançados do PostgreSQL.
