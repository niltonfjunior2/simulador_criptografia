# 🔒 Simulador de Criptografia Assimétrica (RSA Didático)

Este é um projeto de código aberto desenvolvido para fins puramente **didáticos e acadêmicos**. O objetivo é tangibilizar os conceitos abstratos de criptografia de chaves públicas (assimétrica) para estudantes de graduação em Computação, Engenharia e Sistemas de Informação, utilizando uma interface visual interativa executada diretamente no navegador.

O simulador implementa uma versão reduzida e simplificada do algoritmo **RSA**, permitindo que os usuários configurem suas próprias chaves em formato de texto, cifrem mensagens em tempo real e analisem detalhadamente o "alçapão matemático" por trás da operação através da aritmética modular.

---

## 🚀 Funcionalidades

- **Chaves Baseadas em Palavras:** Permite que o Receptor cadastre strings de texto personalizadas para funcionar como as "âncoras" de sua Chave Pública e Chave Privada.
- **Entrada Oculta e Revelável:** A Chave Privada utiliza mascaramento nativo (type="password") com a opção de revelação (👁️) para demonstrar o controle de privacidade.
- **Sincronização Dinâmica:** O painel do Remetente lê automaticamente a chave pública ativa do Receptor, simulando um ambiente de rede real onde chaves públicas são consumidas de um repositório central.
- **Suporte Total a Caracteres:** Aceita qualquer caractere (letras maiúsculas, minúsculas, números, acentuação e símbolos) através do mapeamento direto na tabela ASCII estendida.
- **Simulação de Falha Conceitual (Ataque):** Se o usuário tentar descriptografar uma mensagem utilizando a chave pública, o sistema demonstra visualmente a quebra do cálculo e gera dados corrompidos propositalmente.
- **Matemática Sob Demanda:** Paineis expansíveis revelam o passo a passo matemático de cada caractere processado e fornecem uma explicação teórica robusta sobre as fórmulas aplicadas.

---

## 🧮 Parâmetros Matemáticos Aplicados

Para viabilizar o cálculo em tempo real em navegadores sem sobrecarga computacional, o simulador utiliza chaves reduzidas estruturadas sob os seguintes critérios algébricos:

- **Números Primos de Base (p, q):** 11 e 23
- **Módulo (N):** 11 x 23 = **253** (Permite codificar o escopo da tabela ASCII)
- **Função Totiente de Euler (Fi de N):** (11 - 1) x (23 - 1) = **220**
- **Expoente Público (e):** **7** (Primo entre si com 220)
- **Expoente Privado (d):** **63** (O inverso multiplicativo modular de e, pois (7 x 63) mod 220 = 1)

### Fórmulas Executadas
- **Cifragem (Remetente):** C = (M elevado a 7) mod 253
- **Decifragem (Receptor):** M = (C elevado a 63) mod 253
*(Onde M é o código ASCII do caractere original e C é o bloco numérico cifrado).*

---

## 🛠️ Tecnologias Utilizadas

O projeto foi construído utilizando exclusivamente tecnologias web front-end nativas, sem dependências externas ou necessidade de servidores (overhead zero):

- **HTML5:** Estruturação semântica da interface.
- **CSS3:** Layout responsivo baseado em CSS Grid, Flexbox e design focado em UI/UX para estudantes.
- **JavaScript (ES6):** Manipulação de DOM, escuta de eventos em tempo real e implementação aritmética com suporte a números inteiros gigantescos (BigInt) para precisão nas potências.

---

## 📦 Como Executar o Projeto

Como o projeto é estritamente client-side, não há necessidade de instalar o Node.js, Docker ou qualquer servidor web:

1. Faça o clone deste repositório:
   
   git clone [https://github.com/niltonfjunior2/chaves_assimetricas.git](https://github.com/niltonfjunior2/chaves_assimetricas.git)
   
2. Navegue até a pasta do projeto.

3. Abra o arquivo correspondente em qualquer navegador moderno (Chrome, Edge, Firefox, Safari).

## 👨‍🏫 Sugestão de Roteiro Pedagógico para Sala de Aula

1. **Definição de Identidade**: Peça para o aluno assumindo o papel de Receptor inventar uma string para sua chave pública (ex: UEMG_CAMPUS) e outra para sua privada.

2. **O Fluxo Tradicional**: Digite uma mensagem no painel do Remetente e clique em Cifrar. Mostre à turma a cadeia de números gerada e explique que aquilo é o que transita de forma exposta na rede.

3. **O Teste do Hacker (Falha de Conceito)**: Copie o texto cifrado gerado, cole no painel de decifragem e tente usar a Chave Pública para abrir. O sistema gerará um aviso laranja e caracteres corrompidos. Explique que a chave pública serve apenas para cifrar, ela é uma via de mão única.

4. **Quebra do Segredo**: Insira a Chave Privada correta e veja o texto original reaparecer em verde.

5. **Aprofundamento Teórico**: Clique nos botões roxos "Mostrar Matemática Aplicada" para expor as potências modulares e a tabela ASCII aos alunos, conectando a prática à teoria de Segurança da Informação.

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo LICENSE para obter mais detalhes.