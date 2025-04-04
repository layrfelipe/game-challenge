# Jogo de Tradução Interativo

Este repositório contém o código base para o projeto **Jogo de Tradução Interativo**, um jogo educativo em Python onde o jogador acumula pontos traduzindo palavras ou frases de um idioma para outro. O principal objetivo deste projeto é reforçar os conceitos de Programação Orientada a Objetos (POO) e os fundamentos da linguagem Python, enquanto se pratica boas práticas de desenvolvimento com Git e Git Flow.

## Visão Geral do Projeto

O jogo consiste em:
- **Cadastro e Início de Jogo:** O jogador insere seu nome e inicia a partida.
- **Geração dos Desafios:** Desafios são gerados a partir de um dicionário interno (.txt ou .json) contendo palavras e frases para tradução.
- **Processamento e Validação:** As respostas são verificadas e a pontuação do jogador é atualizada caso tenha acertado.
- **Progresso e Níveis:** Conforme o jogador acerta os desafios, acumula pontuação e os desafios se tornam mais complexos.
- **Feedback e Finalização:** Ao final da partida, a pontuação é exibida.
- **Bônus (Opcional):** Integração com uma API de LLM (como GPT ou Gemini) para fornecer dicas inteligentes quando necessário.

## Objetivos do Projeto

- **Praticar Programação Orientada a Objetos:** Utilizar classes e objetos para estruturar o código.
- **Aplicar Fundamentos do Python:** Manipulação de strings, controle de fluxo, tratamento de exceções, entre outros.
- **Persistência de Dados:** Salvar e carregar o dicionário de traduções e o histórico do jogador usando arquivos (por exemplo, JSON).
- **Git Flow e Entregas Parciais:** Dividir o projeto em pelo menos 5 pull requests para promover ciclos curtos de feedback e prática de boas práticas com Git.

## Estrutura do Projeto

Sugiro que o projeto seja organizado em módulos para facilitar a manutenção e a clareza do código, como nos exemplos abaixo:

- **`jogador.py`**: Contém a classe **Jogador**, que gerencia as informações do jogador (nome, pontuação, nível e progresso).
- **`pergunta.py`**: Contém a classe **PerguntaTraducao**, responsável por gerar desafios e validar respostas a partir de um dicionário de traduções.
- **`logica_jogo.py`**: Implementa a classe **LogicaJogo**, que gerencia o fluxo do jogo, integrando as classes `Jogador` e `PerguntaTraducao`.
- **`api_dica.py` (Opcional/Bônus)**: Implementa a classe **ApiDica**, que integra a consulta a uma API de LLM para fornecer dicas inteligentes.
- Arquivos de dados (ex.: JSON) para armazenar o dicionário de traduções e o histórico do jogador.

## Como Começar

1. **Clone o Repositório:**
   ```bash
   git clone https://github.com/layrfelipe/game-challenge.git
   cd game-challenge
