---
name: us-to-research-fe-v2
description: "Converte requisitos abstratos escritos por Product Owners em um research.md estruturado para desenvolvimento Frontend. Gera contrato de integração com o Backend. Use esta skill quando receber uma User Story para desenvolvimento frontend."
license: MIT
---

Esta SKILL converte requisitos abstratos escritos por Product Owners em um research.md estruturado para desenvolvimento frontend.

- O usuário fornece o nome da feature e a skill verifica a existencia da feature e seu arquivo **research.md** na pasta, para saber se é para 'atualizar' ou 'criar' um novo research.md.
- Caso a feature não exista, é criada a pasta da feature com um arquivo **prd.md** onde será adicionado o conteudo do requisito escrito pelo Product Owner para conversão.
- O usuário é avisado que o arquivo foi criado e a skill irá aguardar a confirmação de que o conteudo do requisito foi adicionado no prd.md.
- Após a confirmação do usuário, a skill irá ler o conteudo do arquivo prd.md e caso o requisito esteja vago, irá realizar perguntas especificas para remover 'ambiguidades e ruídos' da especificação.
- No final, o arquivo research.md é gerado ou atualizado na pasta da feature seguindo a estrutura, padrôes e especificações definidas nesta skill.

# Regra Fundamental

- **SIGA O REQUISITO ORIGINAL EXATAMENTE COMO FORNECIDO. NÃO INVENTE, NÃO ADICIONE E NÃO SUPONHA NADA QUE NÃO ESTEJA EXPRESSAMENTE DEFINIDO NA US.**
- Se a US não menciona algo, não inclua no research. Se há ambiguidade, pergunte ao usuário antes de supor.

## Passo a Passo

### 1. Receber o requisito

- Solicite ao usuário (se não fornecido) o **nome da feature** no formato `nome-da-feature`

### 2. Verificar a existencia da feature

- Verique a existencia do **prd.md** e **research.md** da feature que está localizada em **/specs/features/[nome-da-feature]/*.md**
- Se a feature NÃO existir, execute a etapa **2.2 Criar uma nova feature**
- Se a feature existir, execute a etapa **2.3 Atualizar feature existente**

### 2.2 Criar uma nova feature

- Crie o arquivo **prd.md** na pasta da feature e informe ao usuário que o arquivo foi criado na pasta
- Solicite ao usuário que adicione o conteúdo do requisito para que possa iniciar o processo de geração do **research.md**
- Execute **Opcoes do terminal** que está localizado na seção **Carregado sob demanda** com a intenção de **criar uma nova feature**

### 2.3 Atualizar feature existente

- Primeiro, leia o conteúdo atual da feature para obter contexto.
- Execute **Opcoes do terminal** que está localizado na seção **Carregado sob demanda** com a intenção de **criar ou atualizar a feature**

---

## Gravando os dados no arquivo

### Gravar em uma nova feature

- Exiba a mensagem "Está no modo nova feature"
- encerrar

### Gravar em uma feature existente

- Exiba a mensagem "Está no modo feature existente"
- encerrar


---
## Estrutura do arquivo

---

## Carregado sob demanda

### Opcoes do terminal

- Mostre as seguintes opções obrigatórias no terminal e aguarde a resposta do usuário:
  - 1. Adicionei o conteudo do requisito e quero continuar (execute a etapa **Gravando os dados no arquivo**) com a intenção correta (**criar ou atualizar a feature**).
  - 2. Encerrar (**encerra a operação**).