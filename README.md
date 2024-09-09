# RestauranteDB

Este projeto é um banco de dados para gerenciar um restaurante. Ele inclui tabelas para clientes, mesas, pedidos e itens de pedidos. O banco de dados é criado usando MySQL e foi projetado para armazenar e consultar informações relacionadas ao restaurante.

## Estrutura do Banco de Dados

O banco de dados `restaurantedb` é composto pelas seguintes tabelas:

1. **Clientes**: Armazena informações sobre os clientes do restaurante.
   - `id_cliente` (INT, AUTO_INCREMENT, PRIMARY KEY): Identificador único do cliente.
   - `nome` (VARCHAR(100)): Nome do cliente.
   - `telefone` (VARCHAR(20)): Número de telefone do cliente.
   - `email` (VARCHAR(100)): Email do cliente.

2. **Mesas**: Armazena informações sobre as mesas do restaurante.
   - `id_mesa` (INT, AUTO_INCREMENT, PRIMARY KEY): Identificador único da mesa.
   - `numero_mesa` (INT): Número da mesa.
   - `capacidade` (INT): Capacidade da mesa em termos de número de pessoas.

3. **Pedidos**: Armazena informações sobre os pedidos feitos pelos clientes.
   - `id_pedido` (INT, AUTO_INCREMENT, PRIMARY KEY): Identificador único do pedido.
   - `id_cliente` (INT, FOREIGN KEY): Identificador do cliente que fez o pedido.
   - `id_mesa` (INT, FOREIGN KEY): Identificador da mesa onde o pedido foi feito.
   - `data_pedido` (DATE): Data em que o pedido foi feito.
   - `total` (DECIMAL(10, 2)): Total do pedido.

4. **Itens_Pedido**: Armazena informações sobre os itens de um pedido.
   - `id_item` (INT, AUTO_INCREMENT, PRIMARY KEY): Identificador único do item.
   - `id_pedido` (INT, FOREIGN KEY): Identificador do pedido ao qual o item pertence.
   - `descricao_item` (VARCHAR(255)): Descrição do item.
   - `quantidade` (INT): Quantidade do item no pedido.
   - `preco_unitario` (DECIMAL(10, 2)): Preço unitário do item.

## Consultas SQL

1. **Listar todos os clientes:**
   ```sql
   SELECT 
       id_cliente AS ID_Cliente,
       nome AS Nome,
       telefone AS Telefone,
       email AS Email
   FROM 
       Clientes;
   
2. Listar todas as mesas:
SELECT 
    id_mesa AS ID_Mesa,
    numero_mesa AS Numero_Mesa,
    capacidade AS Capacidade
FROM 
    Mesas;

   3. Listar todos os pedidos:
   SELECT 
    id_pedido AS ID_Pedido,
    id_cliente AS ID_Cliente,
    id_mesa AS ID_Mesa,
    data_pedido AS Data_Pedido,
    total AS Total
FROM 
    Pedidos;

4. Mostrar itens de um pedido específico e o total do pedido:
SELECT 
    id_item AS ID_Item,
    descricao_item AS Descricao_Item,
    quantidade AS Quantidade,
    preco_unitario AS Preco_Unitario,
    (quantidade * preco_unitario) AS Total_Item
FROM 
    Itens_Pedido
WHERE 
    id_pedido = <id_pedido>;

SELECT 
    total AS Total_Pedido
FROM 
    Pedidos
WHERE 
    id_pedido = <id_pedido>;
    
5. Atualizar informações de um cliente:
UPDATE Clientes
SET 
    telefone = '1234-5678',
    email = 'novoemail@exemplo.com'
WHERE 
    id_cliente = <id_cliente>;
    
6. Atualizar a capacidade de uma mesa:
   UPDATE Mesas
SET 
    capacidade = 6
WHERE 
    id_mesa = <id_mesa>;

7. Excluir um pedido e todos os itens associados:
   DELETE FROM Pedidos
WHERE id_pedido = <id_pedido>;


