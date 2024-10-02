#### Respostas

1. **Exercício 1: INNER JOIN**
   - **Resposta**: 
   ```sql
   SELECT E.NUMEROCONTA, R.VALOR
   FROM EXTRATO E
   INNER JOIN REGISTRO R ON E.ID = R.EXTRATOID;
   ```

2. **Exercício 2: LEFT JOIN**
   - **Resposta**:
   ```sql
   SELECT E.NUMEROCONTA, R.VALOR
   FROM EXTRATO E
   LEFT JOIN REGISTRO R ON E.ID = R.EXTRATOID;
   ```

3. **Exercício 3: RIGHT JOIN**
   - **Resposta**:
   ```sql
   SELECT E.NUMEROCONTA, R.VALOR
   FROM EXTRATO E
   RIGHT JOIN REGISTRO R ON E.ID = R.EXTRATOID;
   ```

4. **Exercício 4: FULL OUTER JOIN**
   - **Resposta**:
   ```sql
   SELECT E.NUMEROCONTA, R.VALOR
   FROM EXTRATO E
   FULL JOIN REGISTRO R ON E.ID = R.EXTRATOID;
   ```

5. **Exercício 5: CROSS JOIN**
   - **Resposta**:
   ```sql
   SELECT E.NUMEROCONTA, TIPO.TIPO
   FROM EXTRATO E
   CROSS JOIN TIPOREGISTRO TIPO;
   ```

---