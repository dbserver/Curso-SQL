### Exercício de Normalização

#### Situação:

Você está desenvolvendo um sistema bancário que armazena os dados das movimentações financeiras dos clientes. Atualmente, todos os dados estão armazenados em uma única tabela, mas essa estrutura apresenta muita redundância de informações e dificulta a manutenção e integridade dos dados. Sua tarefa é normalizar essa tabela.

Aqui está a tabela atual chamada **Movimentacoes**:

| ID  | NUMEROCONTA | NOMETITULAR   | TIPO          | VALOR  |
|-----|-------------|---------------|---------------|--------|
| 1   | 12345       | João Silva    | Depósito      | 1000   |
| 2   | 12345       | João Silva    | Saque         | 200    |
| 3   | 67890       | Maria Souza   | Depósito      | 1500   |
| 4   | 67890       | Maria Souza   | Transferência | 500    |
| 5   | 12345       | João Silva    | Transferência | 300    |

#### Pergunta:

**A partir dessa tabela, aplique o processo de normalização até a Terceira Forma Normal (3NF). O resultado final deve ser três entidades separadas: EXTRATO, TIPOREGISTRO e REGISTRO.**
