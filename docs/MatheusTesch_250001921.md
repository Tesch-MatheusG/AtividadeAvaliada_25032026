# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Matheus Gabriel de Melo Tesch  
RA: 250001921  
Data: 25/03/2026

---

# 1. Definição do MVP
Meu MVP cobre o processo de venda de produtos na farmácia, desde a identificação ou cadastro do cliente até a finalização da venda com emissão de comprovante, incluindo:

- O que está **dentro** do MVP?
  
  - Cadastro e identificação de clientes
  - Consulta de produtos
  - Verificação de estoque
  - Registro de venda
  - Venda à vista e a prazo
  - Atualização automática do estoque
  - Geração de contas a receber (para vendas a prazo)
  - Emissão de comprovante
  
- O que está **fora** do MVP?
  
  - Gestão completa de fornecedores e compras
  - Contas a pagar
  - Relatórios gerenciais avançados
  - Controle de permissões detalhado
  - Transferência entre unidades
  
- Por que você fez essas escolhas?

  O foco foi escolhido por ser o processo central da farmácia, impactando diretamente o atendimento ao cliente e o faturamento. Além disso, envolve integração com estoque e financeiro, tornando-o ideal para um MVP funcional e relevante.

---

# 2. Regras de Negócio

**RN01 — Venda somente com estoque disponível**  
Um produto só pode ser vendido se houver quantidade suficiente no estoque da unidade.  

**RN02 — Atualização automática do estoque**  
Toda venda deve reduzir automaticamente a quantidade do produto no estoque.  

**RN03 — Cadastro obrigatório para venda a prazo**  
Clientes que realizam compras a prazo devem estar cadastrados no sistema.  

**RN04 — Geração automática de contas a receber**  
Toda venda a prazo deve gerar automaticamente um lançamento financeiro.  

**RN05 — Status das contas a receber**  
As contas devem possuir status: Aberta, Recebida ou Atrasada.  

**RN06 — Produtos devem possuir informações completas**  
Todo produto deve ter descrição, preço, unidade de medida e fabricante.  

---

# 3. Requisitos Funcionais

**RF01 — Cadastrar cliente**  
O sistema deve permitir cadastrar novos clientes.  

**RF02 — Consultar cliente**  
O sistema deve permitir buscar clientes por nome ou identificação.  

**RF03 — Consultar produto**  
O sistema deve permitir buscar produtos por nome, código ou fabricante.  

**RF04 — Verificar estoque**  
O sistema deve informar a quantidade disponível do produto.  

**RF05 — Registrar venda**  
O sistema deve permitir registrar vendas com múltiplos produtos.  

**RF06 — Processar venda à vista**  
O sistema deve finalizar vendas com pagamento imediato.  

**RF07 — Processar venda a prazo**  
O sistema deve permitir vendas a prazo vinculadas ao cliente.  

**RF08 — Gerar contas a receber**  
O sistema deve gerar automaticamente registros financeiros para vendas a prazo.  

**RF09 — Atualizar estoque automaticamente**  
O sistema deve atualizar o estoque após cada venda.  

**RF10 — Emitir comprovante de venda**  
O sistema deve gerar comprovante com detalhes da operação.  

---

# 4. Requisitos Não Funcionais

**RNF01 — Desempenho**  
O sistema deve responder às consultas em até 2 segundos.  

**RNF02 — Segurança**  
O sistema deve garantir autenticação de usuários.  

**RNF03 — Disponibilidade**  
O sistema deve estar disponível durante horário comercial.  

**RNF04 — Usabilidade**  
A interface deve ser simples e intuitiva para uso dos atendentes.

---

# 5. Casos de Uso  

**Atores:**  
- Atendente  
- Cliente
- Sistema  

**Casos de Uso**  

**UC01 - Identificar Cliente**  
Ator: Atendente  

**UC02 - Cadastrar Cliente**  
Ator: Atendente  

**UC03 - Consultar Produto**  
Ator: Atendente  

**UC04 - Verificar Estoque**  
Ator: Sistema  

**UC05 - Registrar Venda**  
Ator: Atendente  

**UC06 - Adicionar Item à Venda**  
Ator: Atendente  

**UC07 - Finalizar Venda**  
Ator: Atendente  

**UC08 - Processar Pagamento**  
Ator: Atendente  

**UC09 - Gerar Conta a Receber**  
Ator: Sistema   

**UC10 - Emitir Comprovante**  
Ator: Sistema  



**Relacionamento Geral (Atores<-> Casos de Uso)**

- Atendente Interage com:  
  - Identificar Cliente  
  - Cadastrar Cliente  
  - Consultar Produto  
  - Registrar Venda  
  - Adicionar Item à Venda  
  - Finalizar Venda  
  - Processar Pagamento

- Cliente Participa de (Participação indireta):  
  - Identificar Cliente  
  - Registrar Venda  
  - Processar Pagamento

- Sistema executa:
  - Verificar Estoque
  - Gerar Conta a Receber
  - Emitir Comprovante
 

**Relacionamentos entre Casos de Uso:**  

***include***  
- Registrar Venda -> Identificar Cliente  
- Registrar Venda -> Adicionar Item à Venda  
- Registrar Venda -> Consultar Produto  
- Finalizar Venda -> Emitir Comprovante  

***extend***  
- Identificar Cliente -> Cadastrar Cliente (se cliente não existir)  
- Processar Pagamento -> Gerar Conta a Receber (se venda a prazo)  
- Registrar Venda -> Verificar Estoque (validação durante inclusão de itens)  

---

# 6. Documentação dos Casos de Uso

---

## **UC01 — Identificar Cliente**
**Ator(es):** Atendente    
**Descrição:** Identifica cliente no sistema    
**Pré-condições:** Sistema Ativo    
**Pós-condições:** Cliente Identificado ou não encontrado    

### Fluxo Principal  
1.  Atendente informa nome ou CPF  
2.  Sistema busca cliente  
3.  Sistema exibe dados do cliente   

### Fluxos Alternativos / Exceções
- FA01 —  Cliente não encontrado
  Sistema permite Cadastro

### Relacionamentos
- **Extend:** Cadastrar Cliente  

---

## **UC02 — Cadastrar Cliente**  
**Ator(es):** Atendente    
**Descrição:** Cadastra um novo cliente no sistema    
**Pré-condições:** Sistema Ativo, Cliente não cadastrado.  
**Pós-condições:** Cliente cadastrado com sucesso  

### Fluxo Principal  
1.  Atendente insere os dados do Cliente
2.  Sistema valida dados
3.  Sistema salva cliente

---

## **UC03 — Consultar Produto**  
**Ator(es):** Atendente    
**Descrição:** Consulta um produto no sistema    
**Pré-condições:** Sistema Ativo.  
**Pós-condições:** Produto Encontrado ou não  

### Fluxo Principal   
1.  Atendente informa produto  
2.  Sistema exibe resultados

---

## **UC04 — Verificar Estoque**  
**Ator(es):** Sistema     
**Descrição:** Verifica o estoque de determinado produto   
**Pré-condições:** Sistema Ativo  
**Pós-condições:** Quantidade do produto no estoque  

### Fluxo Principal   
1.  Sistema verifica quantidade disponível

### Fluxos Alternativos / Exceções
- FA01 —  Estoque insuficiente
  Sistema informa indisponibilidade

---

## **UC05 — Registrar Venda**  
**Ator(es):** Atendente     
**Descrição:** Registra a Venda de produto(s)   
**Pré-condições:** Sistema Ativo, produto em estoque  
**Pós-condições:** Registra a venda e saída do produto do estoque  

### Fluxo Principal   
1.  Inicia venda
2.  Identifica cliente
3.  Adiciona itens

### Relacionamentos
- **Include:** Identificar Cliente, Adicionar Item.
- **Extend:** Verificar Estoque

---

## **UC06 — Adicionar Item à Venda**
**Ator(es):** Atendente     
**Descrição:** Adiciona um item (produto) à venda   
**Pré-condições:** Sistema Ativo, produto em estoque, Venda iniciada  
**Pós-condições:** Saída do produto do estoque, Item adicionado à venda.  

### Fluxo Principal   
1. Seleciona produto  
2. Informa quantidade  
3. Sistema valida estoque  

---

## **UC07 — Finalizar Venda**
**Ator(es):** Atendente     
**Descrição:** Finaliza a Venda, Confirma a quantidade de itens a remover do estoque   
**Pré-condições:** Sistema Ativo, Venda iniciada.  
**Pós-condições:** Confirmação da saída do produto do estoque, Venda Finalizada.  

### Fluxo Principal   
1. Confirma itens
2. Escolhe forma de pagamento
3. Finaliza venda

### Relacionamentos
- **Include:** Emitir Comprovante.


---

## **UC08 — Processar Pagamento**
**Ator(es):** Sistema     
**Descrição:** Confirma o pagamento da venda   
**Pré-condições:** Sistema Ativo, Venda Finalizada  
**Pós-condições:** Pagamento efetivado com sucesso.  

### Fluxo Principal   
1. Seleciona produto  
2. Informa quantidade  
3. Sistema valida estoque

### Relacionamentos
- **Extend:** Gerar Conta a Receber.

---

## **UC09 — Gerar contas a receber**
**Ator(es):** Sistema     
**Descrição:** Gera um resumo das contas a receber  
**Pré-condições:** Sistema Ativo, Venda A prazo finalizada  
**Pós-condições:** Listagem de Contas a receber  

### Fluxo Principal   
1. Cria registro financeiro
2. Define vencimento
3. Marca como aberta


---

## **UC10 — Emitir Comprovante**  
**Ator(es):** Sistema    
**Descrição:** Emite um comprovante de pagamento da venda   
**Pré-condições:** Sistema Ativo, Venda Finalizada, pagamento efetivado  
**Pós-condições:** Gera um comprovante de pagamento da compra.  

### Fluxo Principal   
1. Gera comprovante
2. Exibe/imprime
