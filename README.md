# 🧩 Case SQL: Gerenciamento de Dados com Foreign Keys no MySQL

Este projeto simula um cenário real de banco de dados de um restaurante com múltiplas tabelas relacionadas por chaves estrangeiras. Ele foi criado com o objetivo de exercitar habilidades práticas em modelagem relacional, inserção de dados consistentes e resolução de erros comuns no MySQL.

## 📌 Tabelas envolvidas

- clientes
- funcionarios
- produtos
- info_produtos
- pedidos (com foreign keys para outras tabelas)

## 🧪 Desafios enfrentados

- Criar estrutura relacional com várias chaves estrangeiras
- Inserir dados em ordem correta para respeitar integridade referencial
- Resetar o AUTO_INCREMENT corretamente
- Diagnosticar e resolver erros como:
  - `1452: Cannot add or update a child row`
  - `1292: Incorrect value for column`

## 📂 Arquivos incluídos

- `definicao.sql` — Criação das tabelas (`CREATE TABLE`) sem dados
- `manipulacao.sql` — Inserção de registros + definição de FOREIGN KEYS
- `troubleshooting.md` — Erros enfrentados e soluções aplicadas

## ✨ Aprendizados

- Compreensão profunda da ordem correta de inserção de dados quando há dependências
- Boa prática com `DELETE`, `TRUNCATE`, `SET FOREIGN_KEY_CHECKS`, `JOIN` investigativo
- Uso consciente de tipos de dados (`VARCHAR`, `INT`, `DECIMAL`)
- Diagnóstico rápido de erros de integridade referencial com `SELECT` e `LEFT JOIN`

---



