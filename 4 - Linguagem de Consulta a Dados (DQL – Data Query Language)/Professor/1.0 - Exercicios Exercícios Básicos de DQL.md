### Exercícios Básicos de DQL

1. **Exercício 1: Seleção Básica**
   - **Resposta**:
   ```sql
   SELECT * FROM EXTRATO;
   ```

2. **Exercício 2: Seleção com WHERE**
   - **Resposta**:
   ```sql
   SELECT NUMEROCONTA, NOMETITULAR 
   FROM EXTRATO 
   WHERE NOMETITULAR = 'João Silva';
   ```

3. **Exercício 3: Operadores Lógicos**
   - **Resposta**:
   ```sql
   SELECT * 
   FROM EXTRATO 
   WHERE NUMEROCONTA = '12345' OR NOMETITULAR = 'Maria Souza';
   ```

4. **Exercício 4: ORDER BY**
   - **Resposta**:
   ```sql
   SELECT * 
   FROM EXTRATO 
   ORDER BY NOMETITULAR ASC;
   ```

5. **Exercício 5: LIMIT**
   - **Resposta**:
   ```sql
   SELECT * 
   FROM REGISTRO 
   LIMIT 3;
   ```

6. **Exercício 6: Seleção com Múltiplas Condições**
   - **Resposta**:
   ```sql
   SELECT NUMEROCONTA 
   FROM EXTRATO 
   WHERE NOMETITULAR = 'João Silva' AND ID > 1;
   ```

---