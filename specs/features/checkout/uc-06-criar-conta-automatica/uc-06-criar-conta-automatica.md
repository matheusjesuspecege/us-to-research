## UC06 - Criar Conta Automática

- **Ator Principal:** Sistema
- **Atores Secundários:** Sistema de E-mail
- **Resumo:** Este caso de uso representa o processo de criação automática de conta na plataforma Linka Eventos quando um participante conclui um checkout que permite compra sem autenticação. A conta é criada com os dados do responsável pelos-ingressos definido no Bloco 2.
- **Pré-condições:** O checkout foi concluído com sucesso e o método de checkout permite criação automática de conta.
- **Pós-condições:** Conta criada na plataforma, e-mail de boas-vindas enviado.

### Cenário Principal

| Ações do Ator | Ações do Sistema |
|---|---|
| | 1. Recebe dados do responsável pelos-ingressos do checkout |
| | 2. Verifica se o e-mail já possui conta existente na plataforma |
| | 3. Se não existir, cria nova conta com: nome, e-mail |
| | 4. Gera senha temporária ou link de criação de senha |
| | 5. Envia e-mail de boas-vindas com link para definição de senha |
| | 6. Vincula os-ingressos adquiridos à conta criada |

### Restrições/Validações

- Conta é criada apenas quando o checkout permite compra sem login
- Em checkout não nominal gratuito, exige autenticação prévia (não cria conta automática)
- Se o e-mail já existir, usa a conta existente sem criar duplicata

### Cenário Alternativo

**A1: E-mail já possui conta**
- Sistema usa a conta existente
- Ingressos são vinculados à conta existente
- Não envia e-mail de boas-vindas

**A2: Checkout nominal - responsável é um dos participantes**
- Conta criada com nome e e-mail do participante selecionado

**A3: Checkout nominal - responsável é "Outro"**
- Conta criada com os dados informados manualmente

### Cenário de Exceção

**E1: Falha na criação de conta**
- Sistema mantém o estado do checkout
- Exibe mensagem de erro ao participante
- Não procede com a conclusão da compra

### Requisitos Não-Funcionais

- Conta deve ser criada apenas após confirmação de pagamento (em casos pagos)
- E-mail de boas-vindas deve ser enviado imediatamente após criação da conta
- Link de criação de senha deve ter tempo de expiração adequado
