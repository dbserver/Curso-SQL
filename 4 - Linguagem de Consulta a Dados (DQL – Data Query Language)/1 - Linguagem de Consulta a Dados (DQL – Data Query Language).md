### Linguagem de Consulta a Dados (DQL – Data Query Language)

A **Data Query Language (DQL)** é uma parte da SQL (Structured Query Language) usada para realizar consultas em bancos de dados. Enquanto outros subconjuntos da SQL (como DML, DDL e DCL) lidam com manipulação de dados, definição de esquemas e controle de acesso, a DQL é focada especificamente na **recuperação de dados**.

A instrução principal da DQL é o comando `SELECT`, que permite consultar os dados de uma ou mais tabelas em um banco de dados. Vamos entender a estrutura básica da DQL e como ela pode ser aplicada com as entidades **EXTRATO**, **TIPOREGISTRO** e **REGISTRO**.

---


### 1. O Comando SELECT

A consulta `SELECT` é usada para recuperar dados de uma ou mais tabelas. A sintaxe básica do `SELECT` é:

```sql
SELECT [colunas]
FROM [tabela]
WHERE [condições];
```

- **`SELECT`**: Especifica as colunas que você deseja exibir.
- **`FROM`**: Define a tabela de onde os dados serão obtidos.
- **`WHERE`**: Define as condições para filtrar os dados (opcional).

#### Exemplo Simples de Consulta

Vamos consultar todos os registros da entidade **EXTRATO**:

```sql
SELECT ID, NUMEROCONTA, NOMETITULAR
FROM EXTRATO;
```

**Resultado:**

| ID  | NUMEROCONTA | NOMETITULAR   |
|-----|-------------|---------------|
| 1   | 12345       | João Silva    |
| 2   | 67890       | Maria Souza   |

---

![alt text](../assets/sql%20joins.png)

### 2. Filtros com a Cláusula WHERE

A cláusula `WHERE` permite restringir os resultados com base em uma ou mais condições. Por exemplo, podemos consultar apenas os registros de um titular específico.

#### Exemplo:

Vamos buscar o extrato do titular **João Silva**:

```sql
SELECT ID, NUMEROCONTA, NOMETITULAR
FROM EXTRATO
WHERE NOMETITULAR = 'João Silva';
```

**Resultado:**

| ID  | NUMEROCONTA | NOMETITULAR   |
|-----|-------------|---------------|
| 1   | 12345       | João Silva    |

---

### 3. Operadores Lógicos e Comparativos

A consulta DQL permite o uso de operadores para filtrar e combinar múltiplas condições:

- **Operadores Lógicos**: `AND`, `OR`, `NOT`
- **Operadores Comparativos**: `=`, `>`, `<`, `>=`, `<=`, `<>`

#### Exemplo:

Vamos consultar os registros de movimentações financeiras (entidade **REGISTRO**) onde o valor da transação é maior que 500:

```sql
SELECT ID, VALOR, TIPOID, EXTRATOID
FROM REGISTRO
WHERE VALOR > 500;
```

**Resultado:**

| ID  | VALOR  | TIPOID | EXTRATOID |
|-----|--------|--------|-----------|
| 1   | 1000   | 1      | 1         |
| 3   | 1500   | 1      | 2         |

---

### 4. Ordenação com ORDER BY

Para ordenar os resultados, usamos a cláusula `ORDER BY`, que pode ser aplicada em uma ou mais colunas. Você pode ordenar os resultados de forma ascendente (`ASC`, que é o padrão) ou descendente (`DESC`).

#### Exemplo:

Vamos ordenar os registros de movimentações financeiras (entidade **REGISTRO**) pelo valor da transação, em ordem decrescente:

```sql
SELECT ID, VALOR, TIPOID, EXTRATOID
FROM REGISTRO
ORDER BY VALOR DESC;
```

**Resultado:**

| ID  | VALOR  | TIPOID | EXTRATOID |
|-----|--------|--------|-----------|
| 3   | 1500   | 1      | 2         |
| 1   | 1000   | 1      | 1         |
| 4   | 500    | 3      | 2         |

---

### 5. Limitação de Resultados com LIMIT

Em alguns casos, você pode querer limitar o número de resultados retornados por uma consulta. O comando `LIMIT` é útil para restringir a quantidade de registros recuperados.

#### Exemplo:

Vamos buscar apenas os dois primeiros registros da entidade **REGISTRO**:

```sql
SELECT ID, VALOR, TIPOID, EXTRATOID
FROM REGISTRO
LIMIT 2;
```

**Resultado:**

| ID  | VALOR  | TIPOID | EXTRATOID |
|-----|--------|--------|-----------|
| 1   | 1000   | 1      | 1         |
| 2   | 200    | 2      | 1         |

---

### 6. Junção de Tabelas (JOIN)

Um dos recursos mais poderosos da DQL é a capacidade de realizar consultas em várias tabelas ao mesmo tempo. Para isso, utilizamos o conceito de **JOIN**, que permite combinar dados de tabelas relacionadas.

#### Tipos de JOIN:

- **INNER JOIN**: Retorna apenas os registros que têm correspondência em ambas as tabelas.
- **LEFT JOIN**: Retorna todos os registros da tabela à esquerda, mesmo que não haja correspondência na tabela à direita.
- **RIGHT JOIN**: Retorna todos os registros da tabela à direita, mesmo que não haja correspondência na tabela à esquerda.
- **FULL JOIN**: Retorna todos os registros quando há correspondência em uma das tabelas ou em ambas.

#### Exemplo com INNER JOIN:

Vamos consultar as movimentações financeiras (entidade **REGISTRO**) e, ao mesmo tempo, trazer o nome do tipo de movimentação (entidade **TIPOREGISTRO**) e os detalhes do titular da conta (entidade **EXTRATO**).

```sql
SELECT R.ID, R.VALOR, T.TIPO, E.NOMETITULAR
FROM REGISTRO R
INNER JOIN TIPOREGISTRO T ON R.TIPOID = T.ID
INNER JOIN EXTRATO E ON R.EXTRATOID = E.ID;
```

**Resultado:**

| ID  | VALOR  | TIPO          | NOMETITULAR   |
|-----|--------|---------------|---------------|
| 1   | 1000   | Depósito      | João Silva    |
| 2   | 200    | Saque         | João Silva    |
| 3   | 1500   | Depósito      | Maria Souza   |
| 4   | 500    | Transferência | Maria Souza   |
| 5   | 300    | Transferência | João Silva    |

---

### 7. Funções Agregadas

As funções agregadas são usadas para realizar cálculos sobre um conjunto de valores. As funções mais comuns incluem:

- **COUNT**: Conta o número de registros.
- **SUM**: Soma os valores de uma coluna.
- **AVG**: Calcula a média dos valores.
- **MAX**: Retorna o maior valor.
- **MIN**: Retorna o menor valor.

#### Exemplo de SUM e AVG:

Vamos calcular o valor total de todas as movimentações financeiras e a média dessas transações:

```sql
SELECT SUM(VALOR) AS TotalMovimentacoes, AVG(VALOR) AS MediaMovimentacoes
FROM REGISTRO;
```

**Resultado:**

| TotalMovimentacoes | MediaMovimentacoes |
|--------------------|--------------------|
| 3500               | 700                |

---

### 8. Agrupamento de Resultados com GROUP BY

O comando `GROUP BY` permite agrupar os dados com base em um ou mais atributos e realizar cálculos agregados em cada grupo.

#### Exemplo:

Vamos agrupar as movimentações financeiras por tipo de movimentação e calcular o valor total de cada tipo:

```sql
SELECT T.TIPO, SUM(R.VALOR) AS TotalPorTipo
FROM REGISTRO R
INNER JOIN TIPOREGISTRO T ON R.TIPOID = T.ID
GROUP BY T.TIPO;
```

**Resultado:**

| TIPO          | TotalPorTipo |
|---------------|--------------|
| Depósito      | 2500         |
| Saque         | 200          |
| Transferência | 800          |

---

### Conclusão

A **Linguagem de Consulta a Dados (DQL)** é essencial para recuperar informações de forma eficiente em um banco de dados. Utilizando comandos como `SELECT`, `WHERE`, `JOIN`, e funções agregadas, é possível extrair e analisar dados de diversas maneiras. A prática dessas consultas é fundamental para o uso eficaz de bancos de dados relacionais.