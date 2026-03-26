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
  1. Identificar Cliente  
  2. Cadastrar Cliente  
  3. Consultar Produto  
  4. Registrar Venda  
  5. Adicionar Item à Venda  
  6. Finalizar Venda  
  7. Processar Pagamento

- Cliente Participa de:  
  1. Identificar Cliente  
  2. Registrar Venda  
  3. Processar Pagamento  

---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UCXX — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.

---

> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).
