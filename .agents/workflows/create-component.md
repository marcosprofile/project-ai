---
description: Agente especializado em converter designs do Figma em código semântico. Ele inspeciona seleções via MCP, mapeia estilos para variáveis CSS existentes, garante 100% de acessibilidade (A11y) e integra HTML/CSS seguindo os padrões do seu projeto.
---

# 🛠️ Workflow: Agente Designer-to-Developer
------------------------------------------

### 1\. Entrada de Dados (Input)

-   **Recebimento do Link:** O usuário fornece o link direto da seleção ou do frame específico no Figma.

-   **Identificação do Contexto:** O agente acessa o arquivo `components.css` local e os arquivos HTML de referência para absorver o "estilo de escrita" (coding style) do projeto.

### 2\. Inspeção Técnica (Figma MCP)

-   **Extração de Atributos:** Uso do MCP para ler propriedades de cor, tipografia, bordas e espaçamento do componente selecionado.

-   **Mapeamento de Tokens:** Comparação dos valores brutos do Figma (ex: `#FFFFFF`) com as variáveis CSS existentes no projeto (ex: `var(--white)`).

    -   *Regra de Ouro:* Se um valor não possuir variável correspondente, a IA deve usar a variável mais próxima ou sinalizar, mas nunca criar uma nova.

### 3\. Planejamento de Acessibilidade (A11y)

-   **Semântica HTML:** Escolha de tags apropriadas (ex: `<main>`, `<section>`, `<button>`, `<a>`).

-   **Atributos ARIA:** Definição de `aria-label`, `aria-expanded` ou `role` conforme a função do componente.

-   **Estados de Interação:** Definição obrigatória de estilos para `:hover`, `:focus-visible` e `:active`.

### 4\. Desenvolvimento e Escrita

-   **Construção do HTML:** Geração da marcação seguindo fielmente a hierarquia e as classes de componentes já existentes no projeto.

-   **Codificação do CSS:** Inserção das novas regras ao final do arquivo `components.css`.

-   **Validação de Escopo:** Garantia de que o novo CSS não quebre estilos globais ou outros componentes.

### 5\. Entrega e Resumo (Output)

-   **Resumo de Alterações:** Apresentação de uma lista sucinta com o que foi feito.

-   **Log de Decisões:** Justificativa de quais variáveis foram usadas e quais medidas de acessibilidade foram implementadas.

* * * * *

📋 Checklist de Execução do Agente
----------------------------------

O Agente **deve** validar cada item abaixo antes de finalizar a tarefa:

-   [ ] **Leitura de Contexto:** Analisei os componentes existentes para manter o padrão de nomenclatura?

-   [ ] **Uso de Variáveis:** Verifiquei se 100% das cores e espaçamentos utilizam as variáveis CSS do projeto? (Proibido valores *hard-coded*).

-   [ ] **Integridade do Arquivo:** Adicionei o código ao `components.css` sem corromper ou apagar o conteúdo anterior?

-   [ ] **Acessibilidade:**

    -   [ ] O componente é navegável via teclado (`Tab`)?

    -   [ ] Existe contraste suficiente entre texto e fundo?

    -   [ ] Usei tags semânticas em vez de `<div>` genéricas?

-   [ ] **HTML Estrutural:** A estrutura do código reflete o padrão de "esqueleto" dos outros arquivos do projeto?

-   [ ] **Resumo de Entrega:** Escrevi o relatório final explicando as variáveis utilizadas e as melhorias de acessibilidade?