## UC07 - Processar Pagamento

- **Ator Principal:** Participante
- **Atores Secundários:** Sistema de Pagamento (Pay), Sistema de E-mail
- **Resumo:** Este caso de uso representa o processo de processamento do pagamento pelo sistema. Inclui os três métodos disponíveis: Pix, Cartão de Crédito e Boleto, cada um com seu fluxo específico de aprovação.
- **Pré-condições:** O participante deve ter selecionado um método de pagamento e preenchido todos os dados obrigatórios.
- **Pós-condições:** Pagamento processado e confirmado, tela de sucesso exibida ou erro apresentado.

### Cenário Principal

| Ações do Ator | Ações do Sistema |
|---|---|
| 1. Seleciona método de pagamento | 2. Exibe campos específicos do método selecionado |
| 3. Preenche dados do pagamento | 4. Valida dados fornecidos |
| 5. Confirma pagamento | 6. Envia dados ao Sistema de Pagamento |

#### Para Cartão de Crédito:

| Ações do Ator | Ações do Sistema |
|---|---|
| | 7. Processa pagamento junto à operadora |
| | 8. Se aprovado: exibe tela de confirmação |
| | 9. Se recusado: retorna ao Bloco 3 mantendo dados, exibe mensagem de erro |

#### Para Pix:

| Ações do Ator | Ações do Sistema |
|---|---|
| | 7. Gera QR Code e código Pix copia e cola |
| | 8. Exibe tempo restante para pagamento |
| | 9. Aguarda confirmação via webhook |
| | 10. Ao receber confirmação: exibe tela de confirmação completa |

#### Para Boleto:

| Ações do Ator | Ações do Sistema |
|---|---|
| | 7. Gera boleto e exibe tela de "Aguardando pagamento" |
| | 8. Permite visualização de instruções e download do boleto |
| | 9. Aguarda compensação do pagamento |
| | 10. Ao confirmar: exibe tela de confirmação |

### Restrições/Validações

- Apenas métodos de pagamento habilitados pelo organizador são exibidos
- Em checkout gratuito, Bloco 3 não exibe opções de pagamento
- Tempo de expiração do Pix e do checkout (15 min) devem ser considerados

### Cenário Alternativo

**A1: Usuário logado com cartão salvo**
- Exibe cartão salvo como opção de pagamento
- Participante precisa apenas inserir CVV para confirmar

### Cenário de Exceção

**E1: Cartão recusado**
- Mantém todos os dados preenchidos no Bloco 3
- Exibe mensagem de erro retornada pela operadora
- Participante pode tentar novamente ou alterar método

**E2: Timeout na comunicação com sistema de pagamento**
- Exibe mensagem de erro genérica
- Permite retry do pagamento

**E3: Pagamento não confirmado (Pix/Boleto)**
- Sistema mantém-ingressos reservados até expiração
- Após expiração,-ingressos são liberados

### Requisitos Não-Funcionais

- Tela de confirmação deve ser a mesma já existente no sistema
- E-mails transacionais devem ser enviados conforme regras do Tópico 9.5 do PRD
- Webhook de pagamento confirmado é necessário para conclusão do fluxo em Pix e Boleto
