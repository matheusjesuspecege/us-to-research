## 1. Atores

Os atores representam papeis desempenhados pelos diversos usuarios que interagem com os serviços e funções do sistema.
- um ator pode representar algum hardware ou outro software que interaja com o sistema. 
- Na maioria das vezes, um ator representará uma pessoa que utilizará o sistema. 
- Cada ator deve ter um nome e um estereótipo ex `<<system>>` que torna explicito que não é um ator humano, e sim sistemas de software ou hardware.
- Em resumo um ator é um usuário que pode representar mais de um papel no sistema

**Obs.** A utilização de estereótipo de sistemas de software ou hardware não é obrigatório, é apenas recomendado para destacar a caracteristica especial que o diferencia dos atores mais comuns.

### 1.1 Como identificar atores

- Deve-se procurar e identificar as entidades externas que interagirão com o sistema, tanto usuários humanos, como também, eventualmente, softwares e/ou hardwares especiais.

- **Candidatos a atores:**
    - Que tipos de usuários poderão usar o sistema?
    - Quais usuários estão interessados ou usarão quais funcionalidades e serviços do software?
    - Quem fornecerá informações ao sistema?
    - Quem usará as informações do sistema?
    - Existe algum outro software que interagirá com o sistema?
    - Existe algum hardware especial (com oum robô, por exemplo) que interagirá com o software?

- **Exemplo de atores válidos**
    - Gerente
    - Funcionario
    - Cliente
    - Sistema Integrado
    - Medidor de Radiação

**Obs.** Os candidatos a atores devem ser listados e deve-se tantar atribuir responsabilidades e objetivos a cada um deles, ou seja, metas que cada ator poderia desejar atingir ao usar o software. Atores para os quais não é possível atribuir um objetivo dificilmente serão atores verdadeiros e deverão ser eliminados.

---

## 2. Casos de Uso

Os casos de uso são usados para capturar os requisitos funcionais do sistema (serviços, tarefas, funcionalidades) identificadas como necessários ao software e que podem ser usados de alguma maneira pelos **atores**. Descrevem e documentam os comportamentos pretendidos para as funções do software.

- Descreve de forma resumida a funcionalidade ao qual o caso de uso se refere.
- O caso de uso costuma ser descrito com um verbo que descreve a ação que será realizada quando for executado. ex: **Abrir Conta**.

### 2.1. Classificação

Os casos de uso podem ser classificados em dois tipos: **primários** ou **secundários**

- **Primários**:
    - Se refere a um processo importante, relacionado com um dos requisitos funcionais do software, ex: **Realizar um saque** ou **Emitir um extrato** em um sistema de controle bancário.
- **Secundários**:
    - Se refere a processos menos importantes, como manutençôes simples. 

**Obs.** É importante retornar o maximo de casos de uso, primários e secundários, detalhando-os o máximo possível para evitar inconsistências e frustrações com a entrega final do software.

### 2.2. Como identificar Casos de Uso

Para identificar os casos de uso, é necessário determinar as funcionalidades necessárias ao software, ou seja:
- Funçôes
- Serviços que correspondem aos requisitos funcionais declarados como necessários ao sistema

Uma maneira de auxiliar na identificação das funcionalidades é verificar a lista dos atores que comporão o sistema e quais os objetivos de cada ator. Esses objetivos muitas vezes corresponderão a uma ou mais funcionalidades. Tambem pode ser útil identificar os eventos externos que afetarão o software.Tais eventos muitas vezes acarretam a execução de uma funcionalidade ou influenciam de alguma forma seu processamento.

Outra maneira de identificar casos de uso é verificar a lista de requisitos funcionais estabelecidos e se cada um deles possui um (ou até mais) caso de uso especificando seu comportamento e, obviamente, qual ator ou atores podem utilizá-lo.

**Observações**
- Um caso de uso costuma ter uma série de passos ou etapas. Uma maneira de determinar se uma funcionalidade é real, ou seja, se realmente corresponde a um caso de uso, é verificar quais ações seriam realizadas quando o caso de uso fosse executado. Se não for possível identificar essas etapas, provavelmente não será um caso de uso real.
- Se o número de passos atribuidos a um caso de uso for muito pequeno, deve-se verificar se esse caso de uso não deveria ser englobado por outro, acrescentando seus passos ás etapas dele ou mesmo se tornando um cenário alternativo de outro caso de uso.

### 2.3. Documentação dos Casos de Uso

A documentação de caso de uso representa o comportamento de um caso de uso da maneira o mais completa possível, mas sem detalhes técnicos de implementação. 

**Exemplo de Estrutura de Documentação de um Caso de Uso**

## UC01 - Abrir Conta

- **Caso de Uso Geral:** Nome do caso de uso geral a partir do qual o caso de uso atual foi derivado
- **Ator Principal:** Funcionário
- **Atores Secundários:** Cliente (Não é obrigatório declarar um ator secundário, visto que pode existir ou não)
- **Resumo:** Esse caso de uso descreve as etapas percorridas por um cliente, intermediado por um funcionário, para abrir uma conta-corrente
- **Pré-condições:** O pedido de abertura precisa ter sido previamente aprovado
- **Pós-condições:** É necessário realizar um depósito inicial

### Cenário Principal

No cenário principal, muitas vezes se representa um "caminho feliz" onde tudo funciona conforme o esperado. 

Ações do Ator | Ações do Sistema |
  ----------------|-------------------
  | 1. O funcionário informa o CPF ou CNPJ do cliente e consulta seu registro | 2. Consultar cliente por seu CPF ou CNPJ |
  | 3. O cliente informa a senha da conta | 4. Abrir conta |
  | 5. O cliente fornece um valor a ser depositado | 6. Executar caso de uso "Realizar Depósito" para registrar o depósito do cliente. 
  | | 6.1. Emitir cartão da conta |

### Restrições/Validações

São as regras de negócio, ou seja, regras que determinam as condições para que o processo seja executado.

1. Para abrir uma conta-corrente, é preciso ser maior de idade
2. O valor mínimo de depósito é R$ 5,00
3. O cliente precisa fornecer algum comprovante de residência

### Cenário Alternativo - Manutenção do Cadastro de Cliente

Os cenários alternativos podem ser executados ou não, dependendo se uma condição for satisfeita.

Ações do Ator | Ações do Sistema |
  ----------------|-------------------
  | | 1. Executar o Caso de Uso "Gerenciar Clientes", para registrar um novo cliente ou atualizar o cadastro do cliente consultado |

### Cenário de Exceção - Cliente menor de idade

Ações que devem ser tomadas em situações em que um cenário principal ou alternativo não pode ser concluído, em razão de alguma regra de negócio ter sido transgredida, por exemplo.

Ações do Ator | Ações do Sistema |
  ----------------|-------------------
  | | 1. Comunicar ao cliente que ele não tem idade mínima para possuir uma conta-corrente |
  | | 2. Recusar o pedido |

### Requisitos Não-Funcionais

No final da documentação, insirir os **requisitos não funcionais** que especificam condições de usabilidade, desempenho, confiabilidade ou segurança, por exemplo.

**Obs.**: O detalhamento maior a nível de implementação, será feito em outra etapa posterior (**research-to-plan**). 
