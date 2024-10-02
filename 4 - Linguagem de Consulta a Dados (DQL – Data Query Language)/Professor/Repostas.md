### Exercícios Básicos de DQL

Aqui estão exercícios de **Data Query Language (DQL)** básicos com perguntas e respostas separadas para aluno e professor, utilizando as entidades **EXTRATO**, **TIPOREGISTRO** e **REGISTRO**.

---

#### **Exercício 1: Seleção Simples**
##### Pergunta para o Aluno:
Escreva uma consulta para exibir o número da conta e o nome do titular de todas as contas na tabela **EXTRATO**.

- **Tabelas**: EXTRATO

##### Resposta para o Professor:
```sql
SELECT NUMEROCONTA, NOMETITULAR
FROM EXTRATO;
```

**Resultado Esperado:**

| NUMEROCONTA | NOMETITULAR |
|-------------|-------------|
| 12345       | João Silva  |
| 67890       | Maria Souza |

---

#### **Exercício 2: Filtro com WHERE**
##### Pergunta para o Aluno:
Escreva uma consulta para exibir todas as movimentações (da tabela **REGISTRO**) cujo valor seja maior que 300.

- **Tabelas**: REGISTRO
- **Condições**:
  1. O valor da movimentação deve ser maior que 300.

##### Resposta para o Professor:
```sql
SELECT ID, VALOR, TIPOID, EXTRATOID
FROM REGISTRO
WHERE VALOR > 300;
```

**Resultado Esperado:**

| ID  | VALOR | TIPOID | EXTRATOID |
|-----|-------|--------|-----------|
| 1   | 1000  | 1      | 1         |
| 3   | 1500  | 1      | 2         |

---

#### **Exercício 3: Ordenação com ORDER BY**
##### Pergunta para o Aluno:
Escreva uma consulta para exibir o nome dos titulares e o número da conta na tabela **EXTRATO**, ordenando os resultados pelo nome do titular em ordem alfabética.

- **Tabelas**: EXTRATO
- **Condições**:
  1. Ordenar os resultados pelo nome do titular em ordem ascendente (padrão).

##### Resposta para o Professor:
```sql
SELECT NOMETITULAR, NUMEROCONTA
FROM EXTRATO
ORDER BY NOMETITULAR;
```

**Resultado Esperado:**

| NOMETITULAR | NUMEROCONTA |
|-------------|-------------|
| João Silva  | 12345       |
| Maria Souza | 67890       |

---

#### **Exercício 4: Seleção com Condição**
##### Pergunta para o Aluno:
Escreva uma consulta para exibir o nome do titular da conta e o número da conta apenas para as contas cujo número seja igual a 67890.

- **Tabelas**: EXTRATO
- **Condições**:
  1. O número da conta deve ser igual a 67890.

##### Resposta para o Professor:
```sql
SELECT NOMETITULAR, NUMEROCONTA
FROM EXTRATO
WHERE NUMEROCONTA = 67890;
```

**Resultado Esperado:**

| NOMETITULAR | NUMEROCONTA |
|-------------|-------------|
| Maria Souza | 67890       |

---

#### **Exercício 5: JOIN Básico**
##### Pergunta para o Aluno:
Escreva uma consulta para exibir o nome do titular da conta e o tipo de movimentação para cada movimentação financeira.

- **Tabelas**: EXTRATO, TIPOREGISTRO, REGISTRO
- **Condições**:
  1. Fazer a junção das tabelas usando os campos relacionados.

##### Resposta para o Professor:
```sql
SELECT E.NOMETITULAR, T.TIPO
FROM REGISTRO R
INNER JOIN EXTRATO E ON R.EXTRATOID = E.ID
INNER JOIN TIPOREGISTRO T ON R.TIPOID = T.ID;
```

**Resultado Esperado:**

| NOMETITULAR | TIPO          |
|-------------|---------------|
| João Silva  | Depósito      |
| João Silva  | Saque         |
| Maria Souza | Depósito      |
| Maria Souza | Transferência |

---

#### **Exercício 6: Limitar Resultados com LIMIT**
##### Pergunta para o Aluno:
Escreva uma consulta para exibir apenas os dois primeiros registros da tabela **REGISTRO**.

- **Tabelas**: REGISTRO
- **Condições**:
  1. Exibir apenas os dois primeiros resultados.

##### Resposta para o Professor:
```sql
SELECT ID, VALOR, TIPOID, EXTRATOID
FROM REGISTRO
LIMIT 2;
```

**Resultado Esperado:**

| ID  | VALOR | TIPOID | EXTRATOID |
|-----|-------|--------|-----------|
| 1   | 1000  | 1      | 1         |
| 2   | 200   | 2      | 1         |

---

#### **Exercício 7: Contagem de Registros com COUNT**
##### Pergunta para o Aluno:
Escreva uma consulta para contar quantas movimentações existem na tabela **REGISTRO**.

- **Tabelas**: REGISTRO

##### Resposta para o Professor:
```sql
SELECT COUNT(*) AS QuantidadeMovimentacoes
FROM REGISTRO;
```

**Resultado Esperado:**

| QuantidadeMovimentacoes |
|-------------------------|
| 5                       |

---

#### **Exercício 8: Função Agregada SUM**
##### Pergunta para o Aluno:
Escreva uma consulta para calcular o valor total de todas as movimentações na tabela **REGISTRO**.

- **Tabelas**: REGISTRO

##### Resposta para o Professor:
```sql
SELECT SUM(VALOR) AS TotalMovimentacoes
FROM REGISTRO;
```

**Resultado Esperado:**

| TotalMovimentacoes |
|--------------------|
| 3500               |

---

### Conclusão

Esses exercícios básicos de **DQL** oferecem uma boa introdução às consultas SQL, permitindo que os alunos pratiquem o uso de `SELECT`, `WHERE`, `ORDER BY`, `JOIN` e funções agregadas simples como `COUNT` e `SUM`.