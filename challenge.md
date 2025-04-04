# Desafio: Jogo de Tradução Interativo + Integração com APIs de LLMs (Bônus)

## Visão Geral do Projeto

Desenvolva um jogo educativo em Python onde o jogador acumula pontos traduzindo palavras e frases de um inglês para português. O projeto será estruturado utilizando Programação Orientada a Objetos (POO) e abordará conceitos fundamentais da linguagem Python, como encapsulamento, modularização e persistência de dados. Além disso, o projeto incluirá desafios extras, como a implementação de um sistema de níveis e a integração opcional com uma API de LLM para fornecer dicas inteligentes.

O intuito do jogo é que seja jogado por pessoas iniciantes no inglês e é muito básico: chegar o mais longe que conseguir no número de acertos. Toda vez que o usuário erra, ele volta pro início. Por isso, para que o jogo não fique repetitivo ele deve sempre trazer palavras aleatórias.

## Objetivos

- **Praticar Programação Orientada a Objetos:** Criação e utilização de classes e objetos.
- **Aplicar os Fundamentos do Python:** Manipulação de strings, controle de fluxo, tratamento de exceções, etc.
- **Gerenciar Persistência de Dados:** Utilizar arquivos de texto para armazenar o dicionário de traduções e o histórico do jogador.
- **Compreender o Git Flow:** Dividir o projeto em partes menores e criar pelo menos 5 pull requests para promover entregas parciais e ciclos curtos de feedback.
- **(Bônus) Integrar API de LLM:** Opcionalmente, implementar uma classe para consultar uma API (como GPT ou Gemini) e oferecer dicas quando necessário.

## Estrutura do Projeto

### 1. Classes Principais

#### **Jogador**
- **Responsabilidades:**
  - Armazenar informações do jogador nome e pontuação.
  - Atualizar a pontuação conforme o desempenho.
  - Registrar e exibir o progresso e feedback.
- **Exemplos de métodos sugeridos:**
  - `adicionar_pontos(qtd)`: Incrementa a pontuação.
  - `mostrar_status()`: Exibe as informações atuais do jogador.

#### **PerguntaTraducao**
- **Responsabilidades:**
  - Gerar desafios utilizando um dicionário interno de traduções.
  - Oferecer dicas, se solicitado, seja a partir de um dicionário de dicas ou via API de LLM (opcional).
- **Atributos:**
  - `texto_origem`: Palavra ou frase a ser traduzida.
  - `traducao_correta`: Tradução correta para validação.
  - `dica`: Dica opcional para auxiliar na tradução.
- **Exemplos de métodos sugeridos:**
  - `validar_resposta(resposta)`: Verifica se a resposta do jogador está correta.
  - `gerar_dica()`: Retorna uma dica baseada na palavra/frase ou invoca a API de LLM para sugestão.

#### **LogicaJogo**
- **Responsabilidades:**
  - Gerenciar o fluxo do jogo: apresentar desafios, coletar e validar respostas, e atualizar o status do jogador.
  - Controlar a sequência dos desafios.
  - Orquestrar a interação entre as demais classes.
- **Exemplos de métodos sugeridos:**
  - `iniciar_jogo()`: Inicia a sequência dos desafios.
  - `apresentar_desafio()`: Seleciona e apresenta uma nova pergunta de tradução.
  - `processar_resposta(resposta, pergunta)`: Valida a resposta e atualiza o status do jogador.
  - `mostrar_resultados()`: Exibe a pontuação final e feedback do desempenho.

#### **ApiDica (Opcional/Bônus)**
- **Responsabilidades:**
  - Encapsular a lógica de comunicação com uma API de LLM para oferecer dicas ou feedback inteligente.
  - Processar a resposta da API e integrá-la à lógica de dicas do jogo.
- **Exemplos de métodos sugeridos:**
  - `solicitar_dica(texto)`: Realiza a chamada à API e retorna uma dica útil.

## Funcionalidades do Jogo

1. **Cadastro e Início de Jogo**
   - O jogador insere seu nome, e uma instância da classe `Jogador` é criada com pontuação zero.
   
2. **Geração dos Desafios**
   - A classe `PerguntaTraducao` seleciona palavras ou frases de um dicionário interno (ou arquivo JSON) para formar os desafios.
   - Cada desafio pode vir acompanhado de uma dica, gerada localmente ou via `ApiDica` (se implementado).

3. **Processamento e Validação**
   - O `LogicaJogo` apresenta os desafios, coleta as respostas e utiliza o método `validar_resposta()` para conferir a correção.
   - Respostas corretas resultam em aumento de pontuação.
   - Em caso de erro, o sistema pode oferecer a opção de tentar novamente ou solicitar uma dica.

4. **Progresso**
   - Desafios podem se tornar progressivamente mais difíceis (palavras/frases mais complexas).

5. **Feedback e Finalização**
   - Ao término do jogo, um resumo com a pontuação e sugestões de melhoria é exibido.
   - O jogador pode optar por reiniciar o jogo para tentar melhorar seu desempenho.

## Persistência e Modularização

- **Persistência de Dados:**  
  Utilize arquivos txt para salvar o dicionário de traduções e o histórico de pontuações, permitindo que o progresso seja mantido entre sessões.
  
- **Modularização:**  
  Organize o projeto em diferentes módulos/arquivos Python, por exemplo:
  - `jogador.py` para a classe **Jogador**.
  - `pergunta.py` para a classe **PerguntaTraducao**.
  - `logica_jogo.py` para a classe **LogicaJogo**.
  - `api_dica.py` para a classe **ApiDica** (opcional).

## Fluxo do Jogo

1. **Tela Inicial:**
   - Exibição de uma mensagem de boas-vindas e solicitação do nome do jogador.
2. **Desafio:**
   - Apresentação de uma palavra ou frase a ser traduzida (ex.: "Traduza a palavra: 'hello'").
   - Coleta da resposta do jogador e validação.
   - Se a resposta estiver correta, exibição de mensagem de acerto e incremento da pontuação.
   - Se incorreta, opção de solicitar uma dica (se a funcionalidade bônus estiver implementada).
3. **Progresso e Níveis:**
   - Após um número predefinido de acertos, o nível é incrementado e desafios mais difíceis são apresentados.
4. **Finalização:**
   - Exibição de um resumo final com pontuação, nível alcançado e feedback do desempenho.

## Controle de Versão e Git Flow

Para que você entenda a importância de entregas parciais e do ciclo de feedback, o projeto deverá ser dividido em pelo menos **5 pull requests**. Cada pull request deve representar uma parte funcional do sistema e conter uma descrição detalhada das alterações implementadas. Essa prática permitirá:

- Compreensão do fluxo de trabalho com Git.
- Facilitação da revisão e correção de erros.
- Aprendizado sobre a importância de entregas incrementais em projetos de desenvolvimento.

**Exemplo de Divisão:**
1. **PR 1:** Configuração do repositório, criação do ambiente inicial e implementação da classe `Jogador`.
2. **PR 2:** Desenvolvimento da classe `PerguntaTraducao` e criação do dicionário de traduções.
3. **PR 3:** Implementação da classe `LogicaJogo` e integração básica com `Jogador` e `PerguntaTraducao`.
4. **PR 4:** Adição da funcionalidade de persistência de dados (salvar e carregar histórico/dicionário).
5. **PR 5:** Implementação da classe `ApiDica` para dicas (opcional) e refinamento da integração geral do jogo.

## Desafios Bônus

- **Integração com API de LLM:**  
  Se desejar, implemente a classe `ApiDica` para realizar chamadas a uma API (como GPT ou Gemini) e oferecer dicas quando o jogador solicitar ajuda.
  
## Considerações Finais

Este desafio não só ajudará a solidificar seus conhecimentos em Programação Orientada a Objetos e Python, como também introduzirá boas práticas de desenvolvimento, como a modularização do código e o uso de Git para versionamento. A divisão do projeto em pull requests menores garantirá que você receba feedback contínuo e possa ajustar o curso do desenvolvimento de forma eficiente.

Bom trabalho e mãos à obra!