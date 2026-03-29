# Research - Checkout

---

## 1. Contexto do Produto

O checkout do Linka Eventos é o momento mais crítico da jornada do participante, onde a intenção de participar de um evento se converte em inscrição ou compra. O problema central identificado está no próprio processo de checkout, que apresenta fragilidades tanto de arquitetura quanto de usabilidade, impactando diretamente a eficiência do fluxo e a experiência do usuário. Além da fragmentação visual, existe uma barreira crítica: realizar qualquer compra exige conta previamente criada, elevando o atrito para participantes de primeira viagem. A proposta é consolidar o checkout em tela única organizada em três blocos sequenciais.

---

## 2. Problema do Negócio

O checkout atual do Linka Eventos apresenta múltiplos problemas: fragmentação visual com múltiplas telas, barreira de acesso exigindo criação de conta obrigatória antes da compra, e fricção que resulta em abandono de carrinho e perda de conversão. Em plataformas modernas de eventos e e-commerce, a obrigatoriedade de criação de conta antes da compra é um dos principais fatores de abandono documentados.

---

## 3. Objetivo da Feature

Consolidar o checkout em tela única com três blocos sequenciais e progressivos: dados dos participantes, recebimento do ingresso e pagamento. Reduzir a percepção de complexidade, melhorar a legibilidade do fluxo, eliminar navegações desnecessárias e introduzir criação automática de conta para checkouts que permitem compra sem login. O objetivo é tornar o checkout do Linka referência em plataformas de eventos: rápido, seguro e com menor quantidade possível de etapas obrigatórias.

---

## 4. Cenário de Uso

O participante acessa o checkout com-ingressos selecionados e visualiza uma tela única organizada em três blocos. No Bloco 1, preenche os dados de cada participante (para-ingressos nominais). No Bloco 2, define o responsável pelos-ingressos e aceita termos. No Bloco 3, seleciona método de pagamento, define comprador e confirma a compra. Durante todo o processo, visualiza o resumo do pedido no painel lateral direito. Ao concluir, recebe confirmação por e-mail e os-ingressos são vinculados à sua conta (criada automaticamente se necessário).

---

## 5. Atores

| Ator | Descrição | Estereótipo |
|------|-----------|-------------|
| Participante | Usuário que realiza a compra ou inscrição em um evento | - |
| Sistema de Pagamento | Sistema externo (Pay) que processa transações de pagamento | **<<system>>** |
| Sistema de E-mail | Sistema responsável pelo envio de e-mails transacionais | **<<system>>** |

---

## 6. Casos de Uso

| Código | Nome | Tipo |
|--------|------|------|
| UC01 | Realizar Checkout Nominal Pago | Primário |
| UC02 | Realizar Checkout Nominal Gratuito | Primário |
| UC03 | Realizar Checkout Não Nominal Pago | Primário |
| UC04 | Realizar Checkout Não Nominal Gratuito | Primário |
| UC05 | Aplicar Cupom de Desconto | Secundário |
| UC06 | Criar Conta Automática | Secundário |
| UC07 | Processar Pagamento | Secundário |

---

## 7. Documentação dos Casos de Uso

Consulte os arquivos individuais de cada caso de uso:

- [UC01 - Realizar Checkout Nominal Pago](./uc-01-checkout-nominal-pago/uc-01-checkout-nominal-pago.md)
- [UC02 - Realizar Checkout Nominal Gratuito](./uc-02-checkout-nominal-gratuito/uc-02-checkout-nominal-gratuito.md)
- [UC03 - Realizar Checkout Não Nominal Pago](./uc-03-checkout-nao-nominal-pago/uc-03-checkout-nao-nominal-pago.md)
- [UC04 - Realizar Checkout Não Nominal Gratuito](./uc-04-checkout-nao-nominal-gratuito/uc-04-checkout-nao-nominal-gratuito.md)
- [UC05 - Aplicar Cupom de Desconto](./uc-05-aplicar-cupom-desconto/uc-05-aplicar-cupom-desconto.md)
- [UC06 - Criar Conta Automática](./uc-06-criar-conta-automatica/uc-06-criar-conta-automatica.md)
- [UC07 - Processar Pagamento](./uc-07-processar-pagamento/uc-07-processar-pagamento.md)

---

## 8. Associações

### UC01 - Realizar Checkout Nominal Pago

| Ator | Associação |
|------|------------|
| Participante | Realiza o checkout |
| Sistema de Pagamento | **<<include>>** Processa pagamento |
| Sistema de E-mail | Envia e-mails transacionais |

| Caso de Uso | Associação | Tipo |
|-------------|------------|------|
| UC01 | **<<include>>** UC05 - Aplicar Cupom de Desconto | Inclusão |
| UC01 | **<<include>>** UC06 - Criar Conta Automática | Inclusão |
| UC01 | **<<include>>** UC07 - Processar Pagamento | Inclusão |

### UC02 - Realizar Checkout Nominal Gratuito

| Ator | Associação |
|------|------------|
| Participante | Realiza o checkout |
| Sistema de E-mail | Envia e-mails transacionais |

| Caso de Uso | Associação | Tipo |
|-------------|------------|------|
| UC02 | **<<include>>** UC06 - Criar Conta Automática | Inclusão |

### UC03 - Realizar Checkout Não Nominal Pago

| Ator | Associação |
|------|------------|
| Participante | Realiza o checkout |
| Sistema de Pagamento | **<<include>>** Processa pagamento |
| Sistema de E-mail | Envia e-mails transacionais |

| Caso de Uso | Associação | Tipo |
|-------------|------------|------|
| UC03 | **<<include>>** UC05 - Aplicar Cupom de Desconto | Inclusão |
| UC03 | **<<include>>** UC06 - Criar Conta Automática | Inclusão |
| UC03 | **<<include>>** UC07 - Processar Pagamento | Inclusão |

### UC04 - Realizar Checkout Não Nominal Gratuito

| Ator | Associação |
|------|------------|
| Participante (autenticado) | Realiza o checkout |
| Sistema de E-mail | Envia e-mails transacionais |

---

## 9. Generalização/Especialização

Não se aplica. Não há casos de uso generalizados ou especializados nesta feature.

---

## 10. Inclusão

Os seguintes casos de uso são incluídos via **<<include>>** em outros casos de uso:

| Caso de Uso Include | Incluído em |
|---------------------|-------------|
| UC05 - Aplicar Cupom de Desconto | UC01, UC03 |
| UC06 - Criar Conta Automática | UC01, UC02, UC03 |
| UC07 - Processar Pagamento | UC01, UC03 |

---

## 11. Extensão

Os cenários alternativos são documentados dentro de cada caso de uso específico. Não há extensões formais entre casos de uso distintos.

---

## 12. Restrições em Associações de Extensão

Não se aplica.

---

## 13. Estereótipos

| Estereótipo | Uso |
|-------------|-----|
| **<<system>>** | Utilizado para identificar atores que são sistemas de software ou hardware externos (Sistema de Pagamento, Sistema de E-mail) |
| **<<include>>** | Utilizado para indicar que um caso de uso é obrigatoriamente incluído no fluxo de outro caso de uso |
| **<<extend>>** | Não utilizado nesta feature |

---

## 14. Pontos de Extensão

Não há pontos de extensão formais definidos nesta feature.

---

## 15. Multiplicidade

| Associação | Multiplicidade | Descrição |
|------------|----------------|-----------|
| Participante - UC01 | 1:N | Um participante pode realizar múltiplos checkouts |
| Participante - UC02 | 1:N | Um participante pode realizar múltiplas inscrições gratuitas |
| Participante - UC03 | 1:N | Um participante pode realizar múltiplos checkouts |
| Participante - UC04 | 1:1 | Participante deve estar autenticado |

---

## 16. Fronteira de Sistema

```
+----------------------------------------------------------+
|                    CHECKOUT LINKA EVENTOS                |
|                                                          |
|  +------------------+  +-----------------------------+  |
|  |     BLOCO 1     |  |                             |  |
|  | Dados dos       |  |     PAINEL LATERAL           |  |
|  | Participantes   |  |     RESUMO DO PEDIDO         |  |
|  |                 |  |                             |  |
|  +------------------+  |  - Nome do evento           |  |
|  +------------------+  |  - Data                     |  |
|  |     BLOCO 2     |  |  - Ingressos                |  |
|  | Recebimento do  |  |  - Desconto (se aplicável)  |  |
|  | Ingresso        |  |  - Total                    |  |
|  |                 |  |  - Tempo restante            |  |
|  +------------------+  |                             |  |
|  +------------------+  +-----------------------------+  |
|  |     BLOCO 3     |                                    |
|  | Pagamento e     |                                    |
|  | Dados do        |                                    |
|  | Comprador       |                                    |
|  +------------------+                                    |
|                                                          |
+----------------------------------------------------------+

  ATORES EXTERNOS:
  +------------------+     +------------------+
  | PARTICIPANTE    |     | SISTEMA DE       |
  | (não autenticado|     | PAGAMENTO        |
  |  ou autenticado)|     | (Pay)            |
  +------------------+     +------------------+
                                    
  +------------------+
  | SISTEMA DE      |
  | E-MAIL          |
  +------------------+
```

---

## 17. Jobs To Be Done

### Job principal:
Comprar ou'inscrire-se em um evento de forma rápida, segura e sem fricções desnecessárias, obtendo os-ingressos imediatamente após a confirmação.

### Jobs secundários:
- Aplicar cupom de desconto para obter redução no valor da compra
- Receber-ingressos por e-mail após confirmação
- Criar conta automaticamente para futuras compras
- Salvar dados para compras futuras
- Acompanhar tempo restante para conclusão da compra

---

## 18. Métricas de Sucesso

### Métrica de produto:
- Taxa de conversão do checkout (compras iniciadas / compras concluídas)
- Taxa de abandono de checkout
- Tempo médio para conclusão do checkout
- Taxa de utilização de cupons de desconto

### Métrica técnica:
- Tempo de resposta do checkout
- Taxa de sucesso de processamento de pagamento
- Tempo de expiração de sessão (15 minutos)
- Taxa de criação automática de conta vs login

---

## Output

```markdown
Research foi criado com sucesso!
UC gerados: 7
UC afetados: 0
```
