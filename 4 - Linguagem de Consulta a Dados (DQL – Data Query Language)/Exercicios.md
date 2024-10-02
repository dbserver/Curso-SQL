### Exercícios Básicos de DQL

Aqui estão exercícios de **Data Query Language (DQL)** básicos com perguntas e respostas separadas para aluno e professor, utilizando as entidades **EXTRATO**, **TIPOREGISTRO** e **REGISTRO**.

---

#### **Exercício 1: Seleção Simples**
Escreva uma consulta para exibir o número da conta e o nome do titular de todas as contas na tabela **EXTRATO**.

- **Tabelas**: EXTRATO

#### **Exercício 2: Filtro com WHERE**
Escreva uma consulta para exibir todas as movimentações (da tabela **REGISTRO**) cujo valor seja maior que 300.

- **Tabelas**: REGISTRO
- **Condições**:
  1. O valor da movimentação deve ser maior que 300.

#### **Exercício 3: Ordenação com ORDER BY**
Escreva uma consulta para exibir o nome dos titulares e o número da conta na tabela **EXTRATO**, ordenando os resultados pelo nome do titular em ordem alfabética.

- **Tabelas**: EXTRATO
- **Condições**:
  1. Ordenar os resultados pelo nome do titular em ordem ascendente (padrão).

#### **Exercício 4: Seleção com Condição**
Escreva uma consulta para exibir o nome do titular da conta e o número da conta apenas para as contas cujo número seja igual a 67890.

- **Tabelas**: EXTRATO
- **Condições**:
  1. O número da conta deve ser igual a 67890.

#### **Exercício 5: JOIN Básico**
Escreva uma consulta para exibir o nome do titular da conta e o tipo de movimentação para cada movimentação financeira.

- **Tabelas**: EXTRATO, TIPOREGISTRO, REGISTRO
- **Condições**:
  1. Fazer a junção das tabelas usando os campos relacionados.


#### **Exercício 6: Limitar Resultados com LIMIT**
Escreva uma consulta para exibir apenas os dois primeiros registros da tabela **REGISTRO**.

- **Tabelas**: REGISTRO
- **Condições**:
  1. Exibir apenas os dois primeiros resultados.


#### **Exercício 7: Contagem de Registros com COUNT**
Escreva uma consulta para contar quantas movimentações existem na tabela **REGISTRO**.

- **Tabelas**: REGISTRO

#### **Exercício 8: Função Agregada SUM**
Escreva uma consulta para calcular o valor total de todas as movimentações na tabela **REGISTRO**.

- **Tabelas**: REGISTRO