# 🍕 Estudos SQL - Projeto Pizzaria

Anotações básicas de SQL utilizando o :contentReference[oaicite:1]{index=1}.

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
|---|---|
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
|---|---|
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

## Buscar usuários que começam com J

```sql
SELECT * FROM usuarios
WHERE nome LIKE 'J%' OR nome LIKE 'j%';
```

### Explicação

| Operador | Função |
|---|---|
| `LIKE` | Busca padrões |
| `%` | Representa qualquer sequência de caracteres |

---

## Ordenar por ID crescente

```sql
SELECT * FROM usuarios
ORDER BY id ASC;
```

### Ordenação

| Comando | Função |
|---|---|
| `ASC` | Crescente |
| `DESC` | Decrescente |

---

## Trazer apenas 1 registro

```sql
SELECT * FROM usuarios
ORDER BY nome ASC
LIMIT 1;
```

---

# 📌 Atualizando Dados

## Atualizar email do usuário

```sql
UPDATE usuarios
SET email = 'jonathanalexandre@gmail.com'
WHERE id = 1;
```

⚠️ Sempre utilize `WHERE` no `UPDATE` para evitar alterar todos os registros.

---

# 📌 Deletando Dados

## Remover usuário

```sql
DELETE FROM usuarios
WHERE id = 2;
```

⚠️ Sempre utilize `WHERE` no `DELETE` para evitar apagar toda a tabela.

---

# 📌 Alterando Tabelas

## Adicionar coluna

```sql
ALTER TABLE usuarios
ADD COLUMN idade SMALLINT NOT NULL DEFAULT 0;
```

---

## Remover coluna

```sql
ALTER TABLE usuarios
DROP COLUMN idade;
```

---

# 📌 Conceitos Importantes

| Conceito | Explicação |
|---|---|
| CRUD | Create, Read, Update, Delete |
| PRIMARY KEY | Identificador único |
| FOREIGN KEY | Relacionamento entre tabelas |
| SELECT | Consulta dados |
| INSERT | Insere dados |
| UPDATE | Atualiza dados |
| DELETE | Remove dados |

---

# 📌 Próximos Estudos

- JOIN
- INNER JOIN
- LEFT JOIN
- GROUP BY
- HAVING
- Subqueries
- Views
- Procedures
- Indexes
- Normalização de Banco de Dados

---

# 🚀 Objetivo

Praticar SQL para desenvolvimento backend e banco de dados relacionais.
