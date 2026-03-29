# Checkout - Research

---

## 1. Contexto do Produto

O checkout do Linka Eventos é o momento mais crítico de toda a jornada do participante. É nele que a intenção de participar de um evento se converte em uma inscrição ou compra, e qualquer fricção nesse processo representa diretamente perda de conversão, abandono de carrinho e experiência negativa para o participante. A proposta é consolidar o checkout em uma tela única organizada em três blocos sequenciais e progressivos: dados dos participantes, responsável pelos ingressos e pagamento e dados do comprador.

---

## 2. Problema do Negócio

O problema central identificado está no próprio processo de checkout, que hoje apresenta fragilidades tanto do ponto de vista de arquitetura quanto de usabilidade, impactando diretamente a eficiência do fluxo e a experiência do usuário. Além da fragmentação visual, existe uma barreira crítica de acesso: atualmente, realizar qualquer compra ou inscrição na plataforma exige que o participante possua uma conta previamente criada. Esse requisito eleva o atrito no início do processo, especialmente para participantes que estão acessando o Linka pela primeira vez. Em plataformas modernas de eventos e e-commerce, a obrigatoriedade de criação de conta antes da compra é um dos principais fatores de abandono documentados.

---

## 3. Objetivo da Feature

Consolidar o checkout em uma tela única organizada em três blocos sequenciais e progressivos: dados dos participantes, responsável pelos ingressos e pagamento e dados do comprador. Essa nova estrutura reduz a percepção de complexidade, melhora a legibilidade do fluxo, elimina navegações desnecessárias entre telas e permite que o participante visualize e edite todas as informações antes de confirmar a compra. Ao mesmo tempo, a refatoração introduz a criação automática de conta para os tipos de checkout que permitem compra sem login, eliminando a barreira de entrada sem abrir mão da gestão de ingressos vinculada a um perfil na plataforma. O objetivo é que o checkout do Linka se torne referência em plataformas de eventos: rápido, seguro e com a menor quantidade possível de etapas obrigatórias para o participante.

---

## 4. Cenário de Uso

O checkout é exibido em uma tela única, com rolagem vertical contínua, organizada em três blocos sequenciais. No Bloco 1, o sistema exibe cards de preenchimento para cada ingresso selecionado com campos de nome, e-mail e celular. No Bloco 2, o participante seleciona o responsável pelos ingresso através de um dropdown. No Bloco 3, o participante seleciona o método de pagamento (Pix, Cartão de Crédito ou Boleto) e preenche os dados do comprador. Um painel lateral exibe o resumo do pedido com contador de tempo regressivo de 15 minutos. O botão "Avançar para pagamento" só é habilitado quando todos os campos obrigatórios estão válidos. Ao concluir, o sistema cria automaticamente uma conta para o responsável pelos ingressso e envia os e-mails de confirmação.

---

## 5. Atores

| Ator | Estereótipo | Descrição |
|------|-------------|-----------|
| Participante | <<actor>> | Pessoa que realiza a compra ou inscrição no evento |
| Organizador | <<actor>> | Pessoa responsável pela criação e configuração do evento e seus ingressos |
| Sistema de Pagamento | <<system>> | Sistema externo que processa os pagamentos (Pay) |
| Sistema de E-mail | <<system>> | Sistema responsável pelo envio de e-mails transacionais |

---

## 6. Casos de Uso

| UC | Nome | Tipo |
|----|------|------|
| UC01 | Realizar Checkout Nominal Pago | Primário |
| UC02 | Realizar Checkout Nominal Gratuito | Primário |
| UC03 | Realizar Checkout Não Nominal Pago | Primário |
| UC04 | Realizar Checkout Não Nominal Gratuito | Primário |
| UC05 | Criar Conta Automática | Secundário |
| UC06 | Aplicar Cupom de Desconto | Secundário |
| UC07 | Gerenciar Expiração do Checkout | Secundário |
| UC08 | Processar Pagamento com Cartão de Crédito | Primário |
| UC09 | Processar Pagamento com Pix | Primário |
| UC10 | Processar Pagamento com Boleto | Primário |
| UC11 | Confirmar Inscrição | Primário |

---

## 7. Documentação dos Casos de Uso

Cada caso de uso está documentado em arquivo separado:

- [UC01 - Realizar Checkout Nominal Pago](./uc-01-checkout-nominal-pago/uc-01.md)
- [UC02 - Realizar Checkout Nominal Gratuito](./uc-02-checkout-nominal-gratuito/uc-02.md)
- [UC03 - Realizar Checkout Não Nominal Pago](./uc-03-checkout-nao-nominal-pago/uc-03.md)
- [UC04 - Realizar Checkout Não Nominal Gratuito](./uc-04-checkout-nao-nominal-gratuito/uc-04.md)
- [UC05 - Criar Conta Automática](./uc-05-criar-conta-automatica/uc-05.md)
- [UC06 - Aplicar Cupom de Desconto](./uc-06-aplicar-cupom-desconto/uc-06.md)
- [UC07 - Gerenciar Expiração do Checkout](./uc-07-gerenciar-expiracao-checkout/uc-07.md)
- [UC08 - Processar Pagamento com Cartão de Crédito](./uc-08-processar-pagamento-cartao/uc-08.md)
- [UC09 - Processar Pagamento com Pix](./uc-09-processar-pagamento-pix/uc-09.md)
- [UC10 - Processar Pagamento com Boleto](./uc-10-processar-pagamento-boleto/uc-10.md)
- [UC11 - Confirmar Inscrição](./uc-11-confirmar-inscricao/uc-11.md)

---

## 8. Associações

| Ator | Caso de Uso | Associação |
|------|-------------|------------|
| Participante | UC01 - Realizar Checkout Nominal Pago | Utiliza |
| Participante | UC02 - Realizar Checkout Nominal Gratuito | Utiliza |
| Participante | UC03 - Realizar Checkout Não Nominal Pago | Utiliza |
| Participante | UC04 - Realizar Checkout Não Nominal Gratuito | Utiliza |
| Participante | UC06 - Aplicar Cupom de Desconto | Utiliza |
| Participante | UC08 - Processar Pagamento com Cartão de Crédito | Utiliza |
| Participante | UC09 - Processar Pagamento com Pix | Utiliza |
| Participante | UC10 - Processar Pagamento com Boleto | Utiliza |
| Participante | UC11 - Confirmar Inscrição | Utiliza |
| Sistema de Pagamento | UC08 - Processar Pagamento com Cartão de Crédito | Fornece |
| Sistema de Pagamento | UC09 - Processar Pagamento com Pix | Fornece |
| Sistema de Pagamento | UC10 - Processar Pagamento com Boleto | Fornece |
| Sistema de E-mail | UC05 - Criar Conta Automática | Notifica |
| Sistema de E-mail | UC11 - Confirmar Inscrição | Notifica |

---

## 9. Generalização/Especialização

Não há generalização/especialização entre casos de uso nesta feature.

---

## 10. Inclusão

| Caso de Uso Include | Caso de Uso Included | Descrição |
|---------------------|----------------------|------------|
| UC01 - Realizar Checkout Nominal Pago | UC05 - Criar Conta Automática | O checkout nominal pago inclui a criação automática de conta |
| UC01 - Realizar Checkout Nominal Pago | UC06 - Aplicar Cupom de Desconto | O checkout nominal pago pode incluir aplicação de cupom |
| UC01 - Realizar Checkout Nominal Pago | UC07 - Gerenciar Expiração do Checkout | O checkout inclui controle de tempo |
| UC01 - Realizar Checkout Nominal Pago | UC08 - Processar Pagamento com Cartão de Crédito | O checkout inclui processamento de cartão |
| UC01 - Realizar Checkout Nominal Pago | UC09 - Processar Pagamento com Pix | O checkout inclui processamento Pix |
| UC01 - Realizar Checkout Nominal Pago | UC10 - Processar Pagamento com Boleto | O checkout inclui processamento de boleto |
| UC01 - Realizar Checkout Nominal Pago | UC11 - Confirmar Inscrição | O checkout inclui confirmação final |
| UC02 - Realizar Checkout Nominal Gratuito | UC05 - Criar Conta Automática | O checkout nominal gratuito inclui criação automática de conta |
| UC02 - Realizar Checkout Nominal Gratuito | UC06 - Aplicar Cupom de Desconto | O checkout nominal gratuito pode incluir aplicação de cupom |
| UC02 - Realizar Checkout Nominal Gratuito | UC07 - Gerenciar Expiração do Checkout | O checkout inclui controle de tempo |
| UC02 - Realizar Checkout Nominal Gratuito | UC11 - Confirmar Inscrição | O checkout inclui confirmação final |
| UC03 - Realizar Checkout Não Nominal Pago | UC05 - Criar Conta Automática | O checkout não nominal pago inclui criação automática de conta |
| UC03 - Realizar Checkout Não Nominal Pago | UC06 - Aplicar Cupom de Desconto | O checkout não nominal pago pode incluir aplicação de cupom |
| UC03 - Realizar Checkout Não Nominal Pago | UC07 - Gerenciar Expiração do Checkout | O checkout inclui controle de tempo |
| UC03 - Realizar Checkout Não Nominal Pago | UC08 - Processar Pagamento com Cartão de Crédito | O checkout inclui processamento de cartão |
| UC03 - Realizar Checkout Não Nominal Pago | UC09 - Processar Pagamento com Pix | O checkout inclui processamento Pix |
| UC03 - Realizar Checkout Não Nominal Pago | UC10 - Processar Pagamento com Boleto | O checkout inclui processamento de boleto |
| UC03 - Realizar Checkout Não Nominal Pago | UC11 - Confirmar Inscrição | O checkout inclui confirmação final |
| UC04 - Realizar Checkout Não Nominal Gratuito | UC06 - Aplicar Cupom de Desconto | O checkout não nominal gratuito pode incluir aplicação de cupom |
| UC04 - Realizar Checkout Não Nominal Gratuito | UC07 - Gerenciar Expiração do Checkout | O checkout inclui controle de tempo |
| UC04 - Realizar Checkout Não Nominal Gratuito | UC11 - Confirmar Inscrição | O checkout inclui confirmação final |

---

## 11. Extensão

| Caso de Uso Extendido | Caso de Uso de Extensão | Ponto de Extensão | Condição |
|-----------------------|------------------------|-------------------|-----------|
| UC08 - Processar Pagamento com Cartão de Crédito | UC08-E1 - Cartão Recusado | Após envio dos dados do cartão | Cartão recusado pela operadora |
| UC11 - Confirmar Inscrição | UC11-E1 - Enviar E-mail de Boas-Vindas | Após confirmação da inscrição | Conta criada automaticamente |

---

## 12. Restrições em Associações de Extensão

| Extensão | Restrição |
|----------|-----------|
| UC08-E1 - Cartão Recusado | O sistema deve retornar ao bloco de pagamento mantendo todos os dados preenchidos e exibir a mensagem de erro retornada de forma clara e com instruções para o participante |
| UC11-E1 - Enviar E-mail de Boas-Vindas | O e-mail deve ser enviado apenas quando uma nova conta for criada automaticamente |

---

## 13. Estereótipos

| Estereótipo | Aplicação |
|-------------|-----------|
| <<actor>> | Participante, Organizador |
| <<system>> | Sistema de Pagamento, Sistema de E-mail |
| <<include>> | Associações de inclusão entre casos de uso |
| <<extend>> | Associações de extensão entre casos de uso |

---

## 14. Pontos de Extensão

| Caso de Uso | Ponto de Extensão | Descrição |
|-------------|-------------------|-----------|
| UC08 - Processar Pagamento com Cartão de Crédito | Após envio dos dados do cartão | Permite tratar cenário de cartão recusado |
| UC11 - Confirmar Inscrição | Após confirmação da inscrição | Permite enviar e-mail de boas-vindas para novas contas |

---

## 15. Multiplicidade

| Associação | Multiplicidade |
|------------|----------------|
| Participante - UC01 a UC04 | 1:N (um participante pode realizar múltiplos checkouts) |
| Participante - UC06 | 1:1 (um participante aplica um cupom por checkout) |
| Sistema de Pagamento - UC08, UC09, UC10 | N:1 (múltiplos participantes podem usar o mesmo sistema de pagamento) |

---

## 16. Fronteira de Sistema

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         CHECKOUT LINKA EVENTOS                          │
│  ┌─────────────────────────────────────────────────────────────────────┐ │
│  │  BLOCO 1: Dados dos Participantes                                  │ │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐                   │ │
│  │  │ Ingresso 1  │ │ Ingresso 2  │ │ Ingresso N  │                   │ │
│  │  │ - Nome      │ │ - Nome      │ │ - Nome      │                   │ │
│  │  │ - E-mail    │ │ - E-mail    │ │ - E-mail    │                   │ │
│  │  │ - Celular   │ │ - Celular   │ │ - Celular   │                   │ │
│  │  │ - Campos    │ │ - Campos    │ │ - Campos    │                   │ │
│  │  │   customiz. │ │   customiz. │ │   customiz. │                   │ │
│  │  └─────────────┘ └─────────────┘ └─────────────┘                   │ │
│  └─────────────────────────────────────────────────────────────────────┘ │
│  ┌─────────────────────────────────────────────────────────────────────┐ │
│  │  BLOCO 2: Recebimento do Ingresso                                  │ │
│  │  - Dropdown: Responsável pelos Ingressos                            │ │
│  │  - Campos: Nome, E-mail, Celular (se "Outro")                      │ │
│  │  - Checkbox: Termos e Condições                                    │ │
│  │  - Checkbox: Receber contato (opcional)                            │ │
│  └─────────────────────────────────────────────────────────────────────┘ │
│  ┌─────────────────────────────────────────────────────────────────────┐ │
│  │  BLOCO 3: Pagamento e Dados do Comprador                           │ │
│  │  - Seleção: Método de pagamento (Pix, Cartão, Boleto)              │ │
│  │  - Dropdown: Responsável pelo pagamento                             │ │
│  │  - Dados do comprador (pré-preenchidos ou manuais)                  │ │
│  │  - Checkbox: Salvar dados para futuras compras                     │ │
│  │  - Botão: Avançar para pagamento                                    │ │
│  └─────────────────────────────────────────────────────────────────────┘ │
│                                                                         │
│  ┌──────────────────────┐                                               │
│  │  RESUMO DO PEDIDO    │                                               │
│  │  - Nome do evento    │                                               │
│  │  - Data(s)           │                                               │
│  │  - Ingressos         │                                               │
│  │  - Cupom (se aplic.) │                                               │
│  │  - Total             │                                               │
│  │  - Tempo restante    │                                               │
│  └──────────────────────┘                                               │
│                                                                         │
│  ┌─────────────────────────────────────────────────────────────────────┐ │
│  │  ATORES EXTERNOS                                                    │ │
│  │  <<system>> Sistema de Pagamento                                    │ │
│  │  <<system>> Sistema de E-mail                                       │ │
│  │  <<actor>> Participante                                             │ │
│  │  <<actor>> Organizador                                              │ │
│  └─────────────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 17. Jobs To Be Done

- **Job principal:** Realizar a compra ou inscrição em um evento de forma rápida, segura e com o menor número de etapas obrigatórias possíveis, sem necessidade de criar conta previamente.

- **Jobs secundários:**
  - Visualizar e editar todas as informações do checkout antes de confirmar
  - Aplicar cupons de desconto para obter redução no valor
  - Escolher o método de pagamento preferido (Pix, Cartão de Crédito, Boleto)
  - Receber os ingressos por e-mail após a confirmação
  - Ter uma conta automaticamente criada para gestão dos ingressos
  - Receber confirmação da compra por e-mail

---

## 18. Métricas de Sucesso

- **Métrica de produto:**
  - Taxa de conversão do checkout (inscrições/concluídas vs iniciadas)
  - Taxa de abandono em cada bloco do checkout
  - Tempo médio para conclusão do checkout

- **Métrica técnica:**
  - Tempo de resposta do processo de checkout
  - Taxa de erros em processamento de pagamento
  - Disponibilidade do sistema de checkout

---

## Output

```markdown
Research foi criado com sucesso!
UC gerados: 11
UC afetados: 0
```
