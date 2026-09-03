# 📚 Banco de Dados I

> Material de revisão baseado nas aulas e exercícios de **Banco de Dados I**.  
> Foco: conceitos iniciais, MER/DER, restrições, MER estendido e mapeamento para o modelo relacional.

---

## 📑 Sumário

1. [Dado x Informação](#1-dado-x-informação)
2. [Banco de Dados](#2-banco-de-dados)
3. [SGBD](#3-sgbd)
4. [Mini-Mundo](#4-mini-mundo)
5. [Modelos de Dados](#5-modelos-de-dados)
6. [Esquema x Instância](#6-esquema-x-instância)
7. [Linguagens de Banco de Dados](#7-linguagens-de-banco-de-dados)
8. [MER / DER](#8-mer--der)
9. [Entidades](#9-entidades)
10. [Atributos](#10-atributos)
11. [Relacionamentos](#11-relacionamentos)
12. [Cardinalidade](#12-cardinalidade)
13. [Participação](#13-participação)
14. [Notação (min,max)](#14-notação-minmax)
15. [MER Estendido — EER](#15-mer-estendido--eer)
16. [Superclasse e Subclasse](#16-superclasse-e-subclasse)
17. [Especialização e Generalização](#17-especialização-e-generalização)
18. [Disjunção e Sobreposição](#18-disjunção-e-sobreposição)
19. [Completude Total e Parcial](#19-completude-total-e-parcial)
20. [Agregação](#20-agregação)
21. [Mapeamento MER → Modelo Relacional](#21-mapeamento-mer--modelo-relacional)
22. [Como resolver um Mini-Mundo](#22-como-resolver-um-mini-mundo)
23. [Pegadinhas para a prova](#23-pegadinhas-para-a-prova)
24. [Mnemônicos rápidos](#24-mnemônicos-rápidos)

---

# 1. Dado x Informação

### Dado
É o **registro de alguma entidade**.

Exemplos:
- `João`
- `23`
- `1234`
- `abc`

### Informação
É um **dado depois de processado e contextualizado**.

Exemplo:

`João` → dado

`João é aluno do IFMG.` → informação

### 🧠 Para memorizar

**DADO = bruto**

**INFORMAÇÃO = dado + contexto**

---

# 2. Banco de Dados

Um banco de dados é uma **coleção de dados logicamente coerente, com significado implícito**, projetada, construída e preenchida para uma finalidade específica.

Ele representa algum aspecto do mundo real, chamado de **Mini-Mundo** ou **Universo de Discurso (UD)**.

### Exemplo

Um banco de dados de uma universidade pode armazenar:

- alunos
- cursos
- disciplinas
- professores
- matrículas

### 🧠 Para memorizar

**BD = coleção organizada de dados com significado.**

---

# 3. SGBD

**SGBD = Sistema Gerenciador de Banco de Dados.**

É o software que facilita:

1. **Definir**
2. **Construir**
3. **Manipular**
4. **Compartilhar**

um banco de dados.

## Funções do SGBD

| Função | O que significa |
|---|---|
| Definir | Especificar tipos, estruturas e restrições |
| Construir | Armazenar os dados |
| Manipular | Consultar, atualizar e gerar relatórios |
| Compartilhar | Permitir acesso simultâneo |

### 🧠 Mnemônico

**D → C → M → C**

**Define → Constrói → Manipula → Compartilha**

O SGBD também ajuda com:
- integridade
- segurança
- controle de inconsistências e redundância
- isolamento
- atomicidade
- abstração dos dados

---

# 4. Mini-Mundo

O **Mini-Mundo** é uma descrição breve, clara e sem ambiguidades de como as coisas funcionam na realidade, especialmente das **regras de negócio** que serão representadas pelo banco.

Também é chamado de **Universo de Discurso (UD)**.

## Como obter informações do Mini-Mundo?

Podem ser usados:
- documentos existentes
- entrevistas com especialistas
- levantamento dos requisitos

### ⚠️ Importante

Se o projetista entender os requisitos de forma errada, o projeto pode fracassar.

### Exemplo

Mini-Mundo:

> "Um aluno está inscrito em um curso. Um curso possui várias disciplinas."

Possíveis entidades:

- ALUNO
- CURSO
- DISCIPLINA

Possíveis relacionamentos:

- ALUNO está inscrito em CURSO
- CURSO possui DISCIPLINA

### 🧠 Para memorizar

**Mini-Mundo = recorte da realidade que o banco vai representar.**

---

# 5. Modelos de Dados

Existem diferentes níveis de abstração.

## 5.1 Modelo Conceitual

É o modelo de **alto nível**, próximo da realidade.

Representa:
- entidades
- atributos
- relacionamentos
- restrições

O **MER/DER** é usado nesse nível.

### Característica importante

É **independente do SGBD**.

---

## 5.2 Modelo Lógico / Representativo

Representa os dados de uma forma mais próxima da implementação.

Exemplos:

| Modelo | Representação |
|---|---|
| Rede | Registros e ponteiros |
| Hierárquico | Árvores |
| Relacional | Tabelas |

O modelo relacional representa os dados através de **tabelas**.

---

## 5.3 Modelo Físico / Baixo Nível

Descreve a **estrutura de armazenamento físico** dos dados.

### 🧠 Para memorizar

**Conceitual → realidade**

**Lógico → estrutura/tabelas**

**Físico → armazenamento**

---

# 6. Esquema x Instância

## Esquema

É a **estrutura do banco de dados**.

É definido durante o projeto e não muda com frequência.

Exemplo:

```text
ALUNO
----------------
id
nome
idade
```

## Instância / Estado

É o **conjunto de dados existente no banco em determinado momento**.

Exemplo:

```text
1 | João | 23
2 | Maria | 21
```

A instância muda frequentemente.

### 🧠 Mnemônico

**ESQUEMA = estrutura**

**INSTÂNCIA = dados naquele momento**

---

# 7. Linguagens de Banco de Dados

## DDL — Data Definition Language

Usada para **definir os esquemas/estruturas** do banco.

Exemplos:

```sql
CREATE TABLE
ALTER TABLE
DROP TABLE
```

### 🧠 DDL = Definition

---

## DML — Data Manipulation Language

Usada para **manipular os dados**.

Exemplos:

```sql
INSERT
UPDATE
DELETE
```

### 🧠 DML = Manipulation

---

## DQL — Data Query Language

Relacionada às **consultas** aos dados.

Exemplo:

```sql
SELECT
```

> O escopo da disciplina também inclui SQL, DDL, DML e DQL.

---

# 8. MER / DER

**MER = Modelo Entidade-Relacionamento**

**DER = Diagrama Entidade-Relacionamento**

O MER representa:
- entidades
- atributos
- relacionamentos
- restrições

É o modelo conceitual de alto nível.

### 🧠 Ideia básica

**Entidade = coisa**

**Atributo = característica**

**Relacionamento = associação**

---

# 9. Entidades

Uma **entidade** representa um objeto ou conceito do mundo real que será representado no banco.

Exemplos:

- ALUNO
- PROFESSOR
- CURSO
- CLIENTE
- PRODUTO
- FUNCIONÁRIO

## Entidade forte

É uma entidade que possui identificação própria e não depende de outra entidade para sua identificação.

## Entidade fraca

É uma entidade que depende de outra entidade para sua identificação/existência.

### 🧠 Para memorizar

**Forte = independente**

**Fraca = dependente**

---

# 10. Atributos

Atributos representam as **características de uma entidade**.

Exemplo:

```text
ALUNO
- matrícula
- nome
- idade
- telefone
```

## 10.1 Atributo simples / atômico

Não pode ser dividido em partes menores relevantes.

Exemplo:

```text
idade
```

---

## 10.2 Atributo composto

Pode ser dividido em outros atributos.

Exemplo:

```text
endereço
├── rua
├── número
├── bairro
└── cidade
```

---

## 10.3 Atributo monovalorado

Possui **um único valor** para uma entidade.

Exemplo:

```text
CPF
```

---

## 10.4 Atributo multivalorado

Pode possuir **mais de um valor** para a mesma entidade.

Exemplo:

```text
Telefone
```

Um aluno pode ter:

```text
(31) 99999-1111
(31) 98888-2222
```

### 🧠 Pegadinha

**Mais de um valor = MULTIVALORADO.**

---

## 10.5 Atributo derivado

Seu valor pode ser obtido/calculado a partir de outros dados.

Exemplo:

```text
idade
```

pode ser calculada a partir da data de nascimento.

---

## 10.6 Atributo identificador / chave

Identifica **unicamente** uma instância da entidade.

Exemplo:

```text
ALUNO
matricula ← identificador
```

Uma chave também pode ser **composta**, utilizando mais de um atributo.

### 🧠 Para memorizar

**Chave = identifica unicamente.**

---

# 11. Relacionamentos

Um relacionamento representa uma **associação entre instâncias de entidades**.

Exemplo:

```text
ALUNO ─── está inscrito ─── CURSO
```

## Graus de relacionamento

### Unário

Uma entidade se relaciona consigo mesma.

```text
FUNCIONÁRIO
     ↕
supervisiona
```

### Binário

Envolve **duas entidades**.

```text
ALUNO ─── CURSO
```

### Ternário

Envolve **três entidades simultaneamente**.

### 🧠 Mnemônico

**Unário = 1**

**Binário = 2**

**Ternário = 3**

---

## Atributo de relacionamento

É um atributo que pertence à **associação**, e não diretamente a uma das entidades.

Exemplo:

```text
ALUNO ─── MATRÍCULA ─── DISCIPLINA
                    |
              data_matricula
```

`data_matricula` descreve a matrícula/associação.

---

# 12. Cardinalidade

A cardinalidade especifica o **número máximo de instâncias** de relacionamento em que uma entidade pode participar.

## 1:1 — um para um

Uma entidade se relaciona com no máximo uma entidade do outro lado.

```text
A 1 ───── 1 B
```

---

## 1:N — um para muitos

Uma entidade pode se relacionar com várias do outro lado.

```text
A 1 ───── N B
```

Exemplo:

```text
DEPARTAMENTO 1 ───── N FUNCIONÁRIOS
```

Um departamento pode ter vários funcionários.

---

## N:1 — muitos para um

É o sentido inverso do 1:N.

```text
A N ───── 1 B
```

---

## N:M — muitos para muitos

Várias instâncias de A podem se relacionar com várias instâncias de B.

```text
A N ───── M B
```

Exemplo:

```text
ALUNO N ───── M DISCIPLINA
```

Um aluno pode cursar várias disciplinas e uma disciplina pode possuir vários alunos.

### 🧠 Para memorizar

**Cardinalidade = QUANTOS?**

---

# 13. Participação

A participação indica se a associação é **obrigatória ou opcional**.

## Participação total

Toda entidade deve estar associada à outra entidade da qual depende através do relacionamento.

### Ideia

**Obrigatório.**

---

## Participação parcial

Nem todas as instâncias precisam estar associadas.

### Ideia

**Opcional.**

### 🧠 Para memorizar

**Total = obrigatório**

**Parcial = opcional**

---

# 14. Notação (min,max)

Quando aparece:

```text
(min,max)
```

- primeiro número = **mínimo**
- segundo número = **máximo**

## Exemplos

| Notação | Significado |
|---|---|
| (1,1) | exatamente 1 |
| (0,1) | de 0 até 1 |
| (0,N) | de 0 até muitos |
| (1,N) | de 1 até muitos |

### 🧠 Regra

**MIN = mínimo de participação**

**MAX = máximo de participação**

---

# 15. MER Estendido — EER

**EER = Extended Entity-Relationship model**

O MER estendido adiciona conceitos ao MER básico:

- subclasses
- superclasses
- especialização
- generalização
- herança de atributos e relacionamentos
- agregação

---

# 16. Superclasse e Subclasse

## Superclasse

É o grupo mais geral.

Exemplo:

```text
FUNCIONÁRIO
```

## Subclasse

É um subgrupo específico da superclasse.

```text
FUNCIONÁRIO
├── SECRETÁRIO
├── TÉCNICO
└── ENGENHEIRO
```

### IS-A

O relacionamento entre superclasse e subclasse também é chamado de **IS-A (É um)**.

Exemplo:

```text
ENGENHEIRO IS-A FUNCIONÁRIO
```

Uma entidade pertencente a uma subclasse **herda os atributos e relacionamentos da superclasse**.

A subclasse também pode possuir atributos e relacionamentos próprios.

### 🧠 Para memorizar

**Superclasse = geral**

**Subclasse = específica**

**IS-A = É UM**

---

# 17. Especialização e Generalização

## Especialização

Vai do **geral para o específico**.

Define subclasses e suas características específicas.

```text
FUNCIONÁRIO
   ↓
ENGENHEIRO
TÉCNICO
SECRETÁRIO
```

### 🧠 Especialização = especializar

**GERAL → ESPECÍFICO**

---

## Generalização

Vai do **específico para o geral**.

Identifica características comuns de entidades e agrupa essas características em uma superclasse.

### 🧠 Generalização = generalizar

**ESPECÍFICO → GERAL**

---

# 18. Disjunção e Sobreposição

## Disjunta — `d`

Uma entidade pode ser membro de **no máximo uma subclasse**.

Exemplo:

```text
FUNCIONÁRIO
├── ENGENHEIRO
├── TÉCNICO
└── SECRETÁRIO
```

Com `d`, uma pessoa não pode pertencer a duas dessas subclasses ao mesmo tempo.

### 🧠 `d` = disjoint / disjunta

---

## Sobreposição — `o`

Uma entidade pode pertencer a **mais de uma subclasse**.

Exemplo:

Uma pessoa pode ser simultaneamente:

```text
FUNCIONÁRIO
├── PROFESSOR
└── PESQUISADOR
```

### 🧠 `o` = overlap / sobreposição

---

# 19. Completude Total e Parcial

## Total

Toda entidade da superclasse deve pertencer a **pelo menos uma subclasse**.

Representação:

**linha dupla**

### Ideia

**Obrigatório.**

---

## Parcial

Uma entidade da superclasse pode não pertencer a nenhuma subclasse.

Representação:

**linha simples**

### Ideia

**Opcional.**

### 🧠 Não confundir

**Disjunção/sobreposição → quantas subclasses pode pertencer?**

**Completude → precisa pertencer a alguma subclasse?**

---

# 20. Agregação

Agregação é uma abstração em que um **relacionamento é tratado como uma entidade de nível superior**.

Essa nova entidade pode participar de outro relacionamento como qualquer outra entidade.

### Ideia simples

Se temos:

```text
A ─── relacionamento ─── B
```

podemos tratar esse relacionamento como uma unidade para relacioná-lo com outra entidade.

### 🧠 Para memorizar

**Agregação = relacionamento tratado como entidade de nível superior.**

---

# 21. Mapeamento MER → Modelo Relacional

Uma das partes mais importantes para exercícios.

## Entidade → Tabela

```text
ALUNO
```

vira:

```text
ALUNO(...)
```

---

## Atributo → Coluna

```text
ALUNO
- matrícula
- nome
- idade
```

vira:

```text
ALUNO(
    matricula,
    nome,
    idade
)
```

---

## Identificador → Chave Primária

```text
matricula
```

vira:

```text
PRIMARY KEY
```

---

## Atributo composto → seus componentes

Exemplo:

```text
endereco
├── rua
├── numero
├── bairro
└── cidade
```

No modelo relacional, os componentes podem virar colunas:

```text
rua
numero
bairro
cidade
```

---

## Atributo multivalorado → tabela própria

Exemplo:

```text
ALUNO
- matrícula
- nome
- telefone {vários}
```

Pode ser representado como:

```text
ALUNO
-----------
matricula PK
nome
```

e:

```text
TELEFONE_ALUNO
----------------
matricula FK
telefone
```

---

## Relacionamento 1:N

Normalmente, a chave estrangeira fica no lado **N**.

Exemplo:

```text
DEPARTAMENTO 1 ───── N FUNCIONÁRIO
```

A tabela FUNCIONÁRIO recebe a FK do departamento:

```text
FUNCIONARIO
----------------
id PK
nome
id_departamento FK
```

### 🧠 Regra

**1:N → FK no lado N**

---

## Relacionamento N:M

Cria-se uma **tabela associativa**.

Exemplo:

```text
ALUNO N ───── M DISCIPLINA
```

vira:

```text
ALUNO
DISCIPLINA
ALUNO_DISCIPLINA
```

A tabela associativa possui as FKs:

```text
ALUNO_DISCIPLINA
---------------------
id_aluno FK
id_disciplina FK
```

Essas FKs podem formar uma chave primária composta.

---

## Atributos do relacionamento N:M

Se o relacionamento possui atributos, eles normalmente vão para a **tabela associativa**.

Exemplo:

```text
ALUNO ─── MATRÍCULA ─── DISCIPLINA
                 |
            data_matricula
```

No relacional:

```text
ALUNO_DISCIPLINA
---------------------
id_aluno
id_disciplina
data_matricula
```

---

# 22. Como resolver um Mini-Mundo

Quando receber um texto na prova, procure:

## 1️⃣ Substantivos → possíveis entidades

Exemplo:

> "Um aluno está inscrito em um curso."

Substantivos:

- aluno
- curso

Possíveis entidades:

```text
ALUNO
CURSO
```

---

## 2️⃣ Características → atributos

Exemplo:

> "Para cada cliente precisamos saber nome, CPF e endereço."

Entidade:

```text
CLIENTE
```

Atributos:

```text
nome
cpf
endereco
```

---

## 3️⃣ Verbos → relacionamentos

Exemplo:

> "Aluno está inscrito em curso."

Relacionamento:

```text
ALUNO ─── está inscrito ─── CURSO
```

---

## 4️⃣ Quantidades → cardinalidades

Palavras importantes:

- um
- vários
- muitos
- somente um
- pode ter vários
- no mínimo
- no máximo

Exemplo:

> "Um departamento possui vários funcionários."

Provavelmente:

```text
DEPARTAMENTO 1 ───── N FUNCIONÁRIO
```

---

# 23. Pegadinhas para a prova

## ❌ Cardinalidade ≠ Participação

### Cardinalidade

Pergunta:

> **QUANTOS?**

Exemplos:

```text
1:1
1:N
N:M
```

### Participação

Pergunta:

> **É obrigatório?**

Exemplos:

```text
Total
Parcial
```

---

## ❌ Dado ≠ Informação

```text
João
```

é dado.

```text
João é aluno do IFMG.
```

é informação.

---

## ❌ Banco de Dados ≠ SGBD

**Banco de dados** = dados organizados.

**SGBD** = software que gerencia esses dados.

---

## ❌ Esquema ≠ Instância

**Esquema** = estrutura.

**Instância** = dados atuais.

---

## ❌ Conceitual ≠ Físico

**Conceitual** = representação da realidade.

**Físico** = armazenamento físico.

---

## ❌ Disjunção ≠ Completude

**Disjunção `d`**:

> Pode estar em quantas subclasses?

No máximo uma.

**Sobreposição `o`**:

> Pode estar em várias subclasses?

Sim.

**Totalidade**:

> Toda entidade da superclasse precisa estar em uma subclasse?

Sim.

**Parcial**:

> Pode não estar em nenhuma?

Sim.

---

# 24. Mnemônicos rápidos

## 🧠 Conceitos iniciais

```text
DADO → bruto
INFORMAÇÃO → dado + contexto
```

## 🧠 SGBD

```text
D C M C

Definir
Construir
Manipular
Compartilhar
```

## 🧠 Modelos

```text
CONCEITUAL → realidade
LÓGICO → tabelas/estrutura
FÍSICO → armazenamento
```

## 🧠 Esquema e instância

```text
ESQUEMA → estrutura
INSTÂNCIA → estado atual
```

## 🧠 MER

```text
ENTIDADE → coisa
ATRIBUTO → característica
RELACIONAMENTO → associação
```

## 🧠 Cardinalidade

```text
1:1 → um para um
1:N → um para muitos
N:M → muitos para muitos
```

**Cardinalidade = QUANTOS?**

## 🧠 Participação

```text
TOTAL → obrigatório
PARCIAL → opcional
```

## 🧠 Atributos

```text
SIMPLES → não divide
COMPOSTO → divide
MONOVALORADO → 1 valor
MULTIVALORADO → vários valores
DERIVADO → calculado
CHAVE → identifica
```

## 🧠 EER

```text
SUPERCLASSE → geral
SUBCLASSE → específica
IS-A → é um
```

## 🧠 Especialização

```text
GERAL → ESPECÍFICO
```

## 🧠 Generalização

```text
ESPECÍFICO → GERAL
```

## 🧠 Disjunção

```text
d → no máximo uma subclasse
o → pode estar em várias
```

## 🧠 Completude

```text
TOTAL → precisa estar em alguma
PARCIAL → pode não estar em nenhuma
```

## 🧠 Mapeamento

```text
ENTIDADE → TABELA
ATRIBUTO → COLUNA
IDENTIFICADOR → PK
1:N → FK no lado N
N:M → TABELA ASSOCIATIVA
```

---

# 🎯 Resumo de 1 minuto antes da prova

Se você tiver pouquíssimo tempo, memorize isto:

```text
DADO = bruto
INFORMAÇÃO = dado + contexto

BD = coleção organizada de dados
SGBD = software que gerencia o BD

Mini-Mundo = recorte da realidade + regras de negócio

CONCEITUAL = MER/DER
LÓGICO = tabelas
FÍSICO = armazenamento

ESQUEMA = estrutura
INSTÂNCIA = dados atuais

DDL = estrutura
DML = dados

ENTIDADE = coisa
ATRIBUTO = característica
RELACIONAMENTO = associação

CARDINALIDADE = quantos?
PARTICIPAÇÃO = obrigatório ou opcional

1:1 = um para um
1:N = um para muitos
N:M = muitos para muitos

TOTAL = obrigatório
PARCIAL = opcional

SUPERCLASSE = geral
SUBCLASSE = específica
IS-A = é um

ESPECIALIZAÇÃO = geral → específico
GENERALIZAÇÃO = específico → geral

d = disjunta
o = sobreposição

TOTAL = toda entidade deve estar em alguma subclasse
PARCIAL = pode não estar em nenhuma

ENTIDADE → TABELA
ATRIBUTO → COLUNA
CHAVE → PK
1:N → FK no lado N
N:M → tabela associativa
```

---

## 📝 Questões que aparecem nos exercícios

Os exercícios da disciplina cobram, entre outros pontos:

- finalidade da chave primária;
- construção de DER a partir de Mini-Mundo;
- transformação do DER para o Modelo Relacional;
- identificação de atributo multivalorado;
- mapeamento de atributo complexo (composto + multivalorado);
- identificação de atributos simples/compostos;
- identificação de atributos monovalorados/multivalorados;
- identificação de atributos obrigatórios/opcionais;
- criação de entidades, atributos, relacionamentos e cardinalidades.

---

## 📚 Conteúdo da disciplina

O escopo apresentado para Banco de Dados I inclui:

- Conceitos Iniciais
- MER
- Modelo Relacional
- Modelo Físico
- SQL
- DDL
- DML
- DQL

O material da disciplina também prevê trabalho envolvendo:

- MER
- MR
- SQL

---

> **Boa prova! 🚀**
>
> Use principalmente as seções **12, 13, 14, 21 e 23** para uma revisão rápida.
