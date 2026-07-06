# Atividade Avaliativa 1: Modelagem de Sistema de Informação e Banco de Dados - Coca-Cola

## Introdução

Este documento apresenta a modelagem do sistema de informação e do banco de dados para uma empresa fictícia, a Coca-Cola, conforme solicitado na Atividade Avaliativa 1 da disciplina de Práticas Extensionistas III. O objetivo é demonstrar a compreensão dos conceitos de modelagem através da criação de diversos diagramas UML e de Entidade-Relacionamento, além de uma documentação detalhada.

## Definição do Domínio do Sistema de Informação da Coca-Cola

Para a atividade avaliativa, o sistema de informação da Coca-Cola será modelado com foco nos seguintes aspectos principais:

### 1. Produtos

O sistema gerenciará uma variedade de produtos oferecidos pela Coca-Cola. Cada produto terá atributos como **ID do Produto**, **Nome**, **Descrição**, **Tipo**, **Tamanho/Volume**, **Preço Unitário** e **Status**.

### 2. Clientes

Os clientes da Coca-Cola podem ser distribuidores, varejistas ou grandes contas. Os atributos dos clientes incluirão **ID do Cliente**, **Nome da Empresa**, **CNPJ/CPF**, **Endereço**, **Telefone**, **Email** e **Tipo de Cliente**.

### 3. Pedidos

O sistema registrará os pedidos feitos pelos clientes. Um pedido pode conter múltiplos produtos. Os atributos do pedido serão **ID do Pedido**, **ID do Cliente**, **Data do Pedido**, **Status do Pedido**, **Valor Total** e **Data de Entrega Estimada**. Cada pedido terá itens detalhados, com **ID do Detalhe do Pedido**, **ID do Pedido**, **ID do Produto**, **Quantidade**, **Preço Unitário no Pedido** e **Subtotal**.

### 4. Estoque

O controle de estoque é crucial para a gestão de produtos. Os atributos do estoque incluirão **ID do Estoque**, **ID do Produto**, **Quantidade Disponível**, **Localização** e **Data da Última Atualização**.

### 5. Fornecedores (Opcional para MER, mas útil para contexto)

Embora não seja o foco principal dos diagramas iniciais, é importante considerar que a Coca-Cola interage com fornecedores de matérias-primas e embalagens. Atributos poderiam incluir **ID do Fornecedor**, **Nome do Fornecedor**, **Contato**, **Telefone** e **Endereço**.

---

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

---

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

---

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

---

# Diagrama de Sequência

O Diagrama de Sequência UML descreve a interação entre objetos em um sistema em uma ordem temporal. Ele mostra a sequência de mensagens trocadas entre os participantes para realizar uma funcionalidade específica. Abaixo, detalhamos o diagrama de sequência para o caso de uso "Fazer Pedido" no sistema da Coca-Cola.

## Caso de Uso: Fazer Pedido

Este diagrama ilustra o fluxo de eventos quando um `Cliente` realiza um pedido no sistema.

### Participantes:

*   **Cliente**: O ator que inicia o processo de fazer um pedido.
*   **Sistema de Pedidos**: A interface principal ou módulo de controle que gerencia a interação do cliente.
*   **Catálogo de Produtos**: O módulo responsável por fornecer informações sobre os produtos disponíveis.
*   **Gerenciador de Pedidos**: O módulo que lida com a criação e gestão dos pedidos.
*   **Detalhes do Pedido**: O módulo que gerencia os itens individuais dentro de um pedido.
*   **Gerenciador de Estoque**: O módulo responsável por atualizar as quantidades de produtos em estoque.

### Fluxo de Eventos:

1.  **Cliente Acessa o Sistema**: O `Cliente` envia uma mensagem para o `Sistema de Pedidos` para acessar a funcionalidade de pedidos.
2.  **Sistema Solicita Produtos**: O `Sistema de Pedidos` solicita a lista de produtos disponíveis ao `Catálogo de Produtos`.
3.  **Catálogo Retorna Produtos**: O `Catálogo de Produtos` responde com a lista de produtos ao `Sistema de Pedidos`.
4.  **Cliente Seleciona Produtos**: O `Cliente` seleciona os produtos desejados e suas respectivas quantidades no `Sistema de Pedidos`.
5.  **Sistema Cria Pedido**: O `Sistema de Pedidos` envia uma mensagem para o `Gerenciador de Pedidos` para criar um novo pedido, passando o `ID_Cliente` e a `Data_Pedido`.
6.  **Pedido Criado**: O `Gerenciador de Pedidos` confirma a criação do pedido ao `Sistema de Pedidos`.
7.  **Loop para Cada Produto Selecionado**:
    *   **Adicionar Item ao Pedido**: Para cada produto selecionado, o `Sistema de Pedidos` envia uma mensagem ao `Detalhes do Pedido` para adicionar o item, incluindo `ID_Pedido`, `ID_Produto`, `Quantidade` e `Preço_Unitário`.
    *   **Item Adicionado**: O `Detalhes do Pedido` confirma que o item foi adicionado.
    *   **Remover Quantidade do Estoque**: O `Sistema de Pedidos` solicita ao `Gerenciador de Estoque` para remover a quantidade do produto correspondente.
    *   **Quantidade Removida**: O `Gerenciador de Estoque` confirma a remoção da quantidade.
8.  **Calcular Valor Total**: Após adicionar todos os itens, o `Gerenciador de Pedidos` calcula o `Valor_Total` do pedido.
9.  **Retornar Valor Total**: O `Gerenciador de Pedidos` retorna o `Valor_Total` ao `Sistema de Pedidos`.
10. **Confirmar Pedido ao Cliente**: O `Sistema de Pedidos` exibe a confirmação do pedido e o `Valor_Total` ao `Cliente`.

### Diagrama de Sequência:

![Diagrama de Sequência - Fazer Pedido](/home/ubuntu/sequence_diagram_fazer_pedido.png)

---

# Diagrama de Atividades

O Diagrama de Atividades UML é utilizado para modelar o fluxo de trabalho ou o processo de negócios de um sistema. Ele mostra a sequência de atividades, decisões, ramificações e junções que ocorrem durante a execução de um caso de uso. Abaixo, detalhamos o diagrama de atividades para o caso de uso "Fazer Pedido" no sistema da Coca-Cola.

## Caso de Uso: Fazer Pedido

Este diagrama ilustra o fluxo de atividades que um `Cliente` e o `Sistema de Pedidos` executam para completar um pedido.

### Fluxo de Atividades:

1.  **Início**: O processo começa.
2.  **Cliente Acessa o Sistema**: O `Cliente` inicia a interação acessando o sistema de pedidos.
3.  **Sistema Exibe Catálogo de Produtos**: O sistema apresenta ao cliente a lista de produtos disponíveis.
4.  **Decisão: Cliente Seleciona Produtos e Quantidades?**:
    *   **Sim**: Se o cliente selecionar produtos e quantidades, o fluxo continua para a criação do pedido.
    *   **Não**: Se o cliente não selecionar produtos ou decidir não continuar, o processo termina.
5.  **Sistema Cria Novo Pedido**: O sistema gera um novo registro de pedido.
6.  **Atividades Paralelas (Fork)**:
    *   **Adicionar Itens ao Pedido**: O sistema adiciona cada produto selecionado como um item individual ao pedido.
    *   **Calcular Subtotal de Cada Item**: Para cada item adicionado, o sistema calcula seu subtotal.
    *   **Atualizar Estoque (Remover Quantidade)**: Simultaneamente, o sistema atualiza o estoque, diminuindo a quantidade dos produtos que foram pedidos.
7.  **Junção (Join)**: As atividades paralelas se juntam após a conclusão de todas elas.
8.  **Calcular Valor Total do Pedido**: O sistema soma os subtotais de todos os itens para obter o valor total do pedido.
9.  **Sistema Confirma Pedido ao Cliente**: O sistema informa ao cliente que o pedido foi realizado com sucesso e apresenta o valor total.
10. **Fim**: O processo de fazer o pedido é concluído.

### Diagrama de Atividades:

![Diagrama de Atividades - Fazer Pedido](/home/ubuntu/activity_diagram_fazer_pedido.png)

---

## Repositório GitHub

Para a publicação da documentação e dos diagramas, será criado um repositório no GitHub. O link do repositório será fornecido após a sua criação e upload dos arquivos.

## Conclusão

Este relatório detalha a modelagem do sistema de informação da Coca-Cola, cobrindo os aspectos de banco de dados e UML. Os diagramas e as explicações fornecem uma visão abrangente da estrutura e do comportamento do sistema, atendendo aos requisitos da atividade avaliativa.
