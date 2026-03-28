# Checkout - Research

## 1. Atores

| Ator | Descrição | Estéreo tipo |
|------|-----------|--------------|
| Participante | Usuário que está realizando a compra de ingressos em um evento | |
| Sistema de Pagamento | Sistema externo que processa os pagamentos (Pix, Cartão, Boleto) | <system> |

## 2. Casos de Uso

| UC | Nome | Ator Principal | Tipo |
|----|------|----------------|------|
| UC01 | Preencher dados dos participantes | Participante | Primário |
| UC02 | Selecionar responsável pelos ingressos | Participante | Primário |
| UC03 | Selecionar método de pagamento | Participante | Primário |
| UC04 | Preencher dados do comprador | Participante | Primário |
| UC05 | Aplicar cupom de desconto | Participante | Secundário |
| UC06 | Finalizar compra | Participante | Primário |
| UC07 | Criar conta automaticamente | Participante | Primário |
| UC08 | Processar pagamento via cartão | Participante | Primário |
| UC09 | Processar pagamento via Pix | Participante | Primário |
| UC10 | Processar pagamento via boleto | Participante | Primário |
| UC11 | Exibir tela de confirmação | Participante | Primário |

## 3. Documentação dos Casos de Uso

Consulte os arquivos individuais na pasta `./uc/` para detalhamento de cada caso de uso.

### 3.1 Casos de Uso Gerados

- [UC01 - Preencher dados dos participantes](./uc/uc-01.md)
- [UC02 - Selecionar responsável pelos ingressos](./uc/uc-02.md)
- [UC03 - Selecionar método de pagamento](./uc/uc-03.md)
- [UC04 - Preencher dados do comprador](./uc/uc-04.md)
- [UC05 - Aplicar cupom de desconto](./uc/uc-05.md)
- [UC06 - Finalizar compra](./uc/uc-06.md)
- [UC07 - Criar conta automaticamente](./uc/uc-07.md)
- [UC08 - Processar pagamento via cartão](./uc/uc-08.md)
- [UC09 - Processar pagamento via Pix](./uc/uc-09.md)
- [UC10 - Processar pagamento via boleto](./uc/uc-10.md)
- [UC11 - Exibir tela de confirmação](./uc/uc-11.md)

## 4. Associações

| Ator | Caso de Uso | Associação |
|------|--------------|------------|
| Participante | UC01 | |
| Participante | UC02 | |
| Participante | UC03 | |
| Participante | UC04 | |
| Participante | UC05 | |
| Participante | UC06 | |
| Participante | UC07 | |
| Participante | UC08 | |
| Participante | UC09 | |
| Participante | UC10 | |
| Participante | UC11 | |
| Sistema de Pagamento | UC08 | <include> |
| Sistema de Pagamento | UC09 | <include> |
| Sistema de Pagamento | UC10 | <include> |

## 5. Inclusão

| Caso de Uso | Include |
|-------------|---------|
| UC06 - Finalizar compra | UC08, UC09 ou UC10 (dependendo do método de pagamento) |
| UC06 - Finalizar compra | UC07 - Criar conta automaticamente |
| UC06 - Finalizar compra | UC11 - Exibir tela de confirmação |
