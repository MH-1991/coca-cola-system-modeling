# Diagrama de Caso de Uso Geral

O Diagrama de Caso de Uso Geral é uma ferramenta UML que descreve a funcionalidade de um sistema do ponto de vista do usuário. Ele ilustra os atores (quem interage com o sistema) e os casos de uso (as funções que o sistema pode realizar). Para o sistema da Coca-Cola, identificamos os seguintes atores e seus respectivos casos de uso:

## Atores e seus Casos de Uso Principais:

### 1. Cliente

Representa os distribuidores, varejistas ou grandes contas que compram produtos da Coca-Cola.

*   **Casos de Uso:**
    *   **Fazer Pedido**: O cliente inicia um processo de compra de produtos.
    *   **Visualizar Histórico de Pedidos**: O cliente pode consultar seus pedidos anteriores e seus status.

### 2. Gerente de Vendas

Responsável pela gestão de produtos, clientes e pedidos, além de análise de vendas.

*   **Casos de Uso:**
    *   **Gerenciar Produtos**: Inclui adicionar, editar e remover produtos do catálogo.
    *   **Gerenciar Clientes**: Permite adicionar, editar e remover informações de clientes.
    *   **Gerenciar Pedidos**: Abrange a visualização e atualização do status dos pedidos.
    *   **Visualizar Relatórios de Vendas**: Acessa relatórios para análise de desempenho de vendas.

### 3. Gerente de Estoque

Encarregado do controle e manutenção do inventário de produtos.

*   **Casos de Uso:**
    *   **Gerenciar Estoque**: Supervisiona as operações de entrada e saída de produtos no estoque.
    *   **Atualizar Quantidade de Produtos**: Modifica a quantidade disponível de um produto específico.
    *   **Verificar Disponibilidade de Produtos**: Consulta a quantidade de produtos em estoque.

### 4. Administrador do Sistema

Responsável pela configuração e manutenção geral do sistema, incluindo gerenciamento de usuários.

*   **Casos de Uso:**
    *   **Gerenciar Usuários**: Adiciona, edita e remove contas de usuários do sistema.
    *   **Configurar Sistema**: Ajusta as configurações gerais do sistema.

## Detalhamento dos Casos de Uso (Inclusões):

Alguns casos de uso são mais complexos e podem incluir outros casos de uso menores para completar sua funcionalidade. Estes são representados pelas relações de `inclusão`:

*   **Fazer Pedido** `inclui`:
    *   **Selecionar Produtos**: O cliente escolhe os produtos desejados.
    *   **Informar Quantidade**: O cliente especifica a quantidade de cada produto.
    *   **Confirmar Pedido**: O cliente finaliza o processo de compra.

*   **Gerenciar Pedidos** `inclui`:
    *   **Atualizar Status do Pedido**: O gerente de vendas altera o estado de um pedido (ex: de Pendente para Enviado).
    *   **Visualizar Detalhes do Pedido**: O gerente de vendas acessa informações detalhadas sobre um pedido.

*   **Gerenciar Estoque** `inclui`:
    *   **Adicionar Produto ao Estoque**: Registra a entrada de novos produtos no estoque.
    *   **Remover Produto do Estoque**: Registra a saída de produtos do estoque.

*   **Gerenciar Produtos** `inclui`:
    *   **Adicionar Produto**: Inclui um novo produto no catálogo.
    *   **Editar Produto**: Modifica as informações de um produto existente.
    *   **Remover Produto**: Exclui um produto do catálogo.

*   **Gerenciar Clientes** `inclui`:
    *   **Adicionar Cliente**: Cadastra um novo cliente no sistema.
    *   **Editar Cliente**: Modifica as informações de um cliente existente.
    *   **Remover Cliente**: Exclui um cliente do sistema.

### Diagrama de Caso de Uso Geral:

![Diagrama de Caso de Uso Geral](/home/ubuntu/use_case_diagram.png)
