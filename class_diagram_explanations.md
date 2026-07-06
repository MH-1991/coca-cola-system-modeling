# Diagrama de Classes UML

O Diagrama de Classes UML (Unified Modeling Language) é uma representação estrutural que descreve a estrutura de um sistema, mostrando as classes do sistema, seus atributos, operações (métodos) e os relacionamentos entre elas. Para o sistema da Coca-Cola, as seguintes classes foram identificadas:

## Classes e seus Componentes:

### 1. `Produto`

Representa os produtos comercializados pela Coca-Cola.

*   **Atributos:**
    *   `ID_Produto`: Identificador único do produto (String).
    *   `Nome`: Nome do produto (String).
    *   `Descricao`: Descrição detalhada do produto (String).
    *   `Tipo`: Categoria do produto (String, ex: Refrigerante, Suco).
    *   `Tamanho_Volume`: Volume ou tamanho da embalagem (String, ex: 350ml, 1L).
    *   `Preco_Unitario`: Preço de venda por unidade (Decimal).
    *   `Status`: Status de disponibilidade do produto (String, ex: Ativo, Inativo).
*   **Operações:**
    *   `atualizarEstoque(int quantidade)`: Atualiza a quantidade do produto em estoque.
    *   `exibirDetalhes()`: Mostra os detalhes completos do produto.

### 2. `Cliente`

Representa os clientes da Coca-Cola, que podem ser distribuidores ou varejistas.

*   **Atributos:**
    *   `ID_Cliente`: Identificador único do cliente (String).
    *   `Nome_Empresa`: Nome da empresa cliente (String).
    *   `CNPJ_CPF`: Número de identificação fiscal (String).
    *   `Endereco`: Endereço do cliente (String).
    *   `Telefone`: Telefone de contato (String).
    *   `Email`: Endereço de e-mail do cliente (String).
    *   `Tipo_Cliente`: Tipo de cliente (String, ex: Distribuidor, Varejista).
*   **Operações:**
    *   `fazerPedido()`: Permite ao cliente realizar um novo pedido.
    *   `visualizarHistoricoPedidos()`: Exibe o histórico de pedidos do cliente.

### 3. `Pedido`

Representa um pedido de produtos feito por um cliente.

*   **Atributos:**
    *   `ID_Pedido`: Identificador único do pedido (String).
    *   `Data_Pedido`: Data em que o pedido foi feito (Date).
    *   `Status_Pedido`: Status atual do pedido (String, ex: Pendente, Enviado).
    *   `Valor_Total`: Valor total do pedido (Decimal).
    *   `Data_Entrega_Estimada`: Data prevista para a entrega (Date).
*   **Operações:**
    *   `adicionarItem(Produto produto, int quantidade)`: Adiciona um produto ao pedido com uma quantidade específica.
    *   `calcularValorTotal()`: Calcula o valor total do pedido com base nos itens adicionados.
    *   `atualizarStatus(String novoStatus)`: Altera o status do pedido.

### 4. `Detalhe_Pedido`

Representa um item individual dentro de um pedido, detalhando qual produto e em que quantidade foi solicitado.

*   **Atributos:**
    *   `ID_Detalhe_Pedido`: Identificador único do detalhe do pedido (String).
    *   `Quantidade`: Quantidade do produto neste item do pedido (int).
    *   `Preco_Unitario_no_Pedido`: Preço unitário do produto no momento do pedido (Decimal).
    *   `Subtotal`: Subtotal deste item do pedido (Decimal).
*   **Operações:**
    *   `calcularSubtotal()`: Calcula o subtotal para este item do pedido.

### 5. `Estoque`

Gerencia a quantidade disponível de cada produto no estoque.

*   **Atributos:**
    *   `ID_Estoque`: Identificador único do registro de estoque (String).
    *   `Quantidade_Disponivel`: Quantidade atual do produto em estoque (int).
    *   `Localizacao`: Localização física do estoque (String).
    *   `Data_Ultima_Atualizacao`: Data da última atualização do registro de estoque (DateTime).
*   **Operações:**
    *   `adicionarProduto(Produto produto, int quantidade)`: Adiciona uma quantidade de um produto ao estoque.
    *   `removerProduto(Produto produto, int quantidade)`: Remove uma quantidade de um produto do estoque.
    *   `verificarDisponibilidade(Produto produto)`: Verifica a quantidade disponível de um produto.

## Relacionamentos entre Classes:

*   **Cliente** e **Pedido**: Um `Cliente` pode fazer (`faz`) muitos `Pedidos` (1 para N).
*   **Pedido** e **Detalhe_Pedido**: Um `Pedido` pode conter (`contem`) muitos `Detalhe_Pedido` (1 para N).
*   **Produto** e **Detalhe_Pedido**: Um `Produto` pode estar em (`esta_em`) muitos `Detalhe_Pedido` (1 para N).
*   **Produto** e **Estoque**: Um `Produto` tem (`tem`) um `Estoque` (1 para 1), indicando que cada produto tem um registro de estoque correspondente.

### Diagrama de Classes:

![Diagrama de Classes UML](/home/ubuntu/class_diagram.png)
