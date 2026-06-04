# 🔒 Simulador de Criptografia: Simétrica & Assimétrica

Este é um projeto web interativo e de código aberto desenvolvido para fins **didáticos e acadêmicos**. O objetivo é facilitar a compreensão prática e visual dos dois principais modelos de criptografia estudados em disciplinas de Segurança da Informação, Redes de Computadores e Sistemas de Informação: a **Criptografia Simétrica** (representada pela Cifra de Vigenère) e a **Criptografia Assimétrica** (representada pelo algoritmo RSA didático).

O simulador é executado inteiramente no navegador (client-side), oferecendo explicações matemáticas em tempo real e permitindo que estudantes experimentem e contrastem os dois modelos de maneira intuitiva.

---

## 🚀 Funcionalidades Principais

O projeto é dividido em duas abas didáticas que separam claramente os conceitos:

### 1. Aba 1: Criptografia Assimétrica (RSA Didático)
*   **Cartão de Conceitos Teóricos:** Um cartão explicativo integrado explica os fundamentos do algoritmo RSA e como o par de chaves pública/privada funciona para garantir a confidencialidade sem o compartilhamento prévio de segredos.
*   **Chaves de Texto Personalizadas:** Permite simular o uso de chaves a partir de palavras amigáveis para fins conceituais (ex: `CHAVE_PUBLICA_UEMG` para cifrar e `SEGREDOPRIVADO123` para decifrar).
*   **Sincronização Dinâmica:** O painel de cifragem consome automaticamente a chave pública configurada, simulando um cenário em que a chave pública está disponível a todos em um repositório ou diretório.
*   **Segurança Visual:** A chave privada é mascarada por padrão (campo do tipo `password`), com opção de exibição (👁️) para reforçar o conceito de sigilo da chave.
*   **Simulação de Ataques/Falhas Conceituais:** Se o usuário tentar descriptografar a mensagem usando a chave pública, o simulador acusa erro e demonstra que a via é de mão única, gerando dados corrompidos.
*   **Matemática Detalhada (Passo a Passo):** Um console integrado exibe os cálculos de potência modular para cada caractere da mensagem (Tabela ASCII ➔ Aritmética Modular RSA ➔ Números Cifrados).

### 2. Aba 2: Criptografia Simétrica (Cifra de Vigenère)
*   **Cartão de Conceitos Teóricos:** Um cartão explicativo integrado ensina a mecânica da criptografia simétrica através da Cifra de Vigenère, abordando a necessidade e os riscos do compartilhamento de uma única chave secreta.
*   **Chave Única Compartilhada:** Demonstra o conceito clássico onde remetente e destinatário precisam combinar previamente o mesmo segredo (ex: `tecnologia`).
*   **Processamento Alfabético (A-Z):** Limpa o texto original (removendo acentos, números e caracteres especiais) e aplica o deslocamento com base no alfabeto padrão de 26 letras.
*   **Matemática de Deslocamento:** Exibe o passo a passo de como as letras da mensagem e as letras da chave são pareadas e somadas modularmente sob a base 26.

---

## 🧮 Funcionamento Matemático e Fórmulas

Para permitir que os cálculos ocorram instantaneamente no navegador sem travar a interface, o simulador adota modelos reduzidos de ambos os algoritmos:

### Aritmética do RSA Didático
O simulador utiliza valores primos pequenos para configurar o par de chaves RSA:
*   **Números Primos Iniciais:** $p = 11$ e $q = 23$
*   **Módulo base ($N$):** $11 \times 23 = 253$ (suficiente para abranger toda a tabela ASCII estendida de 0 a 252)
*   **Função Totiente de Euler ($\phi(N)$):** $(11 - 1) \times (23 - 1) = 220$
*   **Expoente Público ($e$):** $7$ (primo em relação a 220)
*   **Expoente Privado ($d$):** $63$ (pois $(7 \times 63) \pmod{220} = 1$)

**Fórmulas Utilizadas:**
*   **Cifragem (Pública):** $C = M^{7} \pmod{253}$
*   **Decifragem (Privada):** $M = C^{63} \pmod{253}$
    *(onde $M$ é o código ASCII decimal do caractere e $C$ é o valor numérico cifrado resultante).*

### Aritmética da Cifra de Vigenère
Os caracteres são mapeados de $A = 0$ a $Z = 25$. A chave secreta é repetida ciclicamente sobre a mensagem.

**Fórmulas Utilizadas:**
*   **Cifragem:** $Posição\_Cifrada = (Posição\_Original + Deslocamento\_Chave) \pmod{26}$
*   **Decifragem:** $Posição\_Original = (Posição\_Cifrada - Deslocamento\_Chave + 26) \pmod{26}$

---

## 🛠️ Tecnologias Utilizadas

O simulador foi construído de forma totalmente estática e nativa, com foco em simplicidade de execução:
*   **HTML5:** Estrutura semântica dos painéis de entrada e resultado.
*   **CSS3:** Estilização com design moderno (limpo e responsivo), usando Flexbox e Grid Layout para organizar as duas colunas (Cifragem vs. Decifragem).
*   **JavaScript (ES6+):** Lógica matemática de cifragem, aritmética modular, limpeza de strings e manipulação dinâmica da interface. Utiliza a biblioteca nativa `BigInt` para suportar grandes potências computadas no RSA sem perda de precisão matemática.

---

## 📦 Como Executar

Por ser um projeto puramente estático (front-end), não é necessária a instalação de dependências ou servidores locais.

1.  Baixe ou clone este repositório:
    ```bash
    git clone https://github.com/niltonfjunior2/simulador_criptografia.git
    ```
2.  Navegue até a pasta do projeto.
3.  Dê um duplo clique no arquivo [index.html](index.html) ou abra-o em seu navegador de preferência.

---

## 👨‍🏫 Roteiro de Aula Prática Sugerido

Para professores ou palestrantes que queiram utilizar esta ferramenta em aula, recomenda-se o seguinte roteiro:

### Atividade 1: Entendendo a Criptografia Simétrica (Aba 2)
1.  **O Segredo Compartilhado:** Defina a palavra-chave secreta (ex: `UEMG`) e explique que ambos os lados precisam conhecê-la antecipadamente.
2.  **Cifragem e Transmissão:** Escreva um texto original (ex: `SEGURANCA`), clique em **Cifrar** e veja o texto resultante.
3.  **Matemática:** Clique em **Mostrar Matemática Aplicada** e demonstre como o algoritmo soma as posições das letras da mensagem com as letras da chave no alfabeto.
4.  **O Problema da Chave:** Altere uma única letra da chave no painel de decifragem e tente decifrar. Mostre aos alunos que qualquer divergência na chave de segurança gera um resultado incompreensível. Discuta com a turma: *Como enviar a chave de forma segura para o receptor sem que um intruso a intercepte?*

### Atividade 2: Entendendo a Criptografia Assimétrica e o RSA (Aba 1)
1.  **Pares de Chaves:** Explique o conceito de chave pública (conhecida por todos) e chave privada (secreta do receptor).
2.  **Cifragem Segura:** Escreva uma mensagem no painel do Remetente e clique em **Cifrar**. O resultado será uma sequência de números separados por vírgula.
3.  **A Unidirecionalidade (O Teste do Invasor):** Copie a sequência numérica gerada, cole-a no painel de decifragem do receptor e tente usar a **chave pública** para decifrar. O sistema irá falhar e retornar caracteres aleatórios. Mostre que a chave pública **apenas cifra** dados e não pode reverter a cifragem.
4.  **A Abertura com a Chave Privada:** Insira a **chave privada** correta no painel de decifragem e clique em **Decifrar**. O texto original é restaurado com sucesso.
5.  **Aprofundamento Teórico:** Expanda o painel de matemática do RSA e discuta como o cálculo modular de potências ($C = M^e \pmod N$) funciona como uma função de "via de mão única com alçapão", onde a chave privada é o segredo do alçapão que simplifica a operação reversa.

---

## 📄 Licença

Este projeto está licenciado sob a Licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.