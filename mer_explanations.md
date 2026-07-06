# Modelagem de Entidade e Relacionamento (Conceitual e Lógico)

Esta seção detalha a modelagem do banco de dados para o sistema da Coca-Cola, apresentando os diagramas Conceitual e Lógico de Entidade e Relacionamento (MER).

## 1. Modelo Entidade-Relacionamento Conceitual

O Modelo Entidade-Relacionamento Conceitual (MER Conceitual) representa uma visão de alto nível das entidades e seus relacionamentos, sem se preocupar com os detalhes de implementação do banco de dados. Ele foca na identificação das principais entidades do sistema e como elas se conectam logicamente.

### Entidades e Atributos Principais:

*   **Produto**: Representa os diferentes produtos que a Coca-Cola oferece. Atributos incluem `ID_Produto`, `Nome`, `Descrição`, `Tipo`, `Tamanho_Volume`, `Preço_Unitário` e `Status`.
*   **Cliente**: Representa os clientes da Coca-Cola (distribuidores, varejistas). Atributos incluem `ID_Cliente`, `Nome_Empresa`, `CNPJ_CPF`, `Endereço`, `Telefone`, `Email` e `Tipo_Cliente`.
*   **Pedido**: Representa as ordens de compra feitas pelos clientes. Atributos incluem `ID_Pedido`, `Data_Pedido`, `Status_Pedido`, `Valor_Total` e `Data_Entrega_Estimada`.
*   **Detalhe_Pedido**: Representa os itens individuais dentro de um pedido, conectando produtos a pedidos específicos. Atributos incluem `ID_Detalhe_Pedido`, `Quantidade`, `Preço_Unitário_no_Pedido` e `Subtotal`.
*   **Estoque**: Representa o controle de inventário dos produtos. Atributos incluem `ID_Estoque`, `Quantidade_Disponível`, `Localização` e `Data_Última_Atualização`.

### Relacionamentos:

*   Um **Cliente** `faz` muitos **Pedidos** (1:N).
*   Um **Pedido** `contém` muitos **Detalhes_Pedido** (1:N).
*   Um **Produto** `está em` muitos **Detalhes_Pedido** (1:N).
*   Um **Produto** `tem` um **Estoque** (1:1), indicando que cada produto tem um registro de estoque correspondente.

### Diagrama Conceitual:

![Modelo Entidade-Relacionamento Conceitual](/home/ubuntu/conceptual_mer.png)

## 2. Modelo Entidade-Relacionamento Lógico

O Modelo Entidade-Relacionamento Lógico (MER Lógico) refina o modelo conceitual, adicionando detalhes específicos de implementação que são relevantes para um banco de dados relacional. Ele define tipos de dados, chaves primárias (PK), chaves estrangeiras (FK) e restrições de integridade.

### Entidades e Atributos com Detalhes Lógicos:

*   **Produto**:
    *   `ID_Produto`: `varchar` (Chave Primária - PK)
    *   `Nome`: `varchar(255)` (Não Nulo)
    *   `Descrição`: `text`
    *   `Tipo`: `varchar(100)`
    *   `Tamanho_Volume`: `varchar(50)`
    *   `Preço_Unitário`: `decimal(10, 2)` (Não Nulo)
    *   `Status`: `varchar(50)`

*   **Cliente**:
    *   `ID_Cliente`: `varchar` (PK)
    *   `Nome_Empresa`: `varchar(255)` (Não Nulo)
    *   `CNPJ_CPF`: `varchar(20)` (Único, Não Nulo)
    *   `Endereço`: `text`
    *   `Telefone`: `varchar(20)`
    *   `Email`: `varchar(255)`
    *   `Tipo_Cliente`: `varchar(50)`

*   **Pedido**:
    *   `ID_Pedido`: `varchar` (PK)
    *   `ID_Cliente`: `varchar` (Chave Estrangeira - FK para Cliente.ID_Cliente)
    *   `Data_Pedido`: `date` (Não Nulo)
    *   `Status_Pedido`: `varchar(50)`
    *   `Valor_Total`: `decimal(10, 2)`
    *   `Data_Entrega_Estimada`: `date`

*   **Detalhe_Pedido**:
    *   `ID_Detalhe_Pedido`: `varchar` (PK)
    *   `ID_Pedido`: `varchar` (FK para Pedido.ID_Pedido)
    *   `ID_Produto`: `varchar` (FK para Produto.ID_Produto)
    *   `Quantidade`: `int` (Não Nulo)
    *   `Preço_Unitário_no_Pedido`: `decimal(10, 2)`
    *   `Subtotal`: `decimal(10, 2)`

*   **Estoque**:
    *   `ID_Estoque`: `varchar` (PK)
    *   `ID_Produto`: `varchar` (FK para Produto.ID_Produto, Único)
    *   `Quantidade_Disponível`: `int` (Não Nulo)
    *   `Localização`: `varchar(255)`
    *   `Data_Última_Atualização`: `datetime`

### Diagrama Lógico:

![Modelo Entidade-Relacionamento Lógico](/home/ubuntu/logical_mer.png)
