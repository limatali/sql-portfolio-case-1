# 🚨 Troubleshooting de Erros no Projeto SQL com Foreign Keys

Durante a criação e manipulação do banco de dados relacional, enfrentei alguns erros comuns — e reais — ao lidar com integridade referencial e tipos de dados. Abaixo estão os principais problemas encontrados e como eles foram solucionados.

---

## ❌ Erro 1452: FOREIGN KEY constraint fails

**Mensagem:**  
Cannot add or update a child row: a foreign key constraint fails


**Causa:**  
Tentei inserir um pedido (`INSERT INTO pedidos`) usando um `id_cliente` que não existia na tabela `clientes`.

**Exemplo real:**  
Havia apenas 25 clientes, mas tentei inserir um `id_cliente = 28`.

**Solução aplicada:**  
- Verifiquei a quantidade real de clientes usando `SELECT COUNT(*) FROM clientes;`
- Corrigi o valor do `id_cliente` para um que realmente existia na tabela

---

## ❌ Erro 1292: Incorrect value for column

**Mensagem:**  
Incorrect value: '12345678900' for column 'cpf'


**Causa:**  
O campo `cpf` na tabela `funcionarios` era numérico (`INT` ou `BIGINT`), mas eu passei o valor entre aspas, como se fosse texto (`'12345678900'`), o que causou erro de tipo.

**Solução aplicada:**  
- Passei o CPF sem aspas no `WHERE cpf = 12345678900`
- Também revisei o tipo da coluna para considerar usar `VARCHAR(11)` no futuro, por segurança

---

## ⚠️ DELETE impedido por integridade referencial

**Cenário:**  
Tentei deletar um funcionário com `DELETE FROM funcionarios WHERE cpf = ...`, mas ele estava vinculado à tabela `pedidos`.

**Mensagem esperada:**  
Cannot delete or update a parent row: a foreign key constraint fails


**Solução aplicada:**  
- Primeiro deletei os pedidos associados:
```sql
DELETE FROM pedidos WHERE id_funcionario = (SELECT id_funcionario FROM funcionarios WHERE cpf = 12345678900);

Depois, consegui apagar o funcionário com segurança
