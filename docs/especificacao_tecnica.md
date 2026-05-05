# Especificação Técnica da Arquitetura
## Documentação de Blocos Funcionais do Processador

Este documento detalha os componentes lógicos e estruturais da arquitetura desenvolvida, descrevendo a função de cada bloco no fluxo de dados e controle.

### 1. Fluxo de Instrução e Endereçamento
*   **PC (Program Counter):** Armazena o endereço da próxima instrução a ser executada. A cada ciclo de clock, recebe um novo valor vindo do multiplexador de próximo PC.
*   **Memória de Instruções:** Unidade de armazenamento que recebe o endereço vindo do PC e retorna a instrução correspondente para decodificação.
*   **Divisão da Instrução (Decoder):** Realiza o "parsing" da instrução em seus campos (opcode, rs, rt, rd, etc.) e distribui os sinais para o sistema.

### 2. Controle e Processamento de Dados
*   **Unidade de Controle:** O "cérebro" do processador. Recebe o opcode e gera sinais essenciais como RegWrite, ALUSrc e MemWrite.
*   **Banco de Registradores:** Realiza a leitura simultânea de rs e rt, com escrita sincronizada pelo sinal RegWrite.
*   **ULA (Unidade Lógica e Aritmética):** Executa operações como soma e subtração, gerando a flag "Zero" para desvios.
*   **Controle da ULA:** Decodificador secundário que determina a operação exata da ULA baseando-se no ALUOp e no campo funct.

### 3. Memória e Seleção de Fluxo
*   **Memória de Dados:** Interface para armazenamento de dados, operando sob os sinais MemRead e MemWrite para operações de Load/Store.
*   **Lógica de Branch e Jump:** Calcula o próximo estado do PC combinando sinais de controle com o resultado da ULA.

### 4. Multiplexadores de Decisão
*   **MUX RegDst / ALUSrc / MemToReg:** Elementos que selecionam o caminho dos dados (destino de escrita, origem do operando da ULA e fonte do dado).

---
*Nota Técnica: Esta descrição garante a integridade do ciclo de busca, decodificação e execução conforme o planejamento do projeto.*
