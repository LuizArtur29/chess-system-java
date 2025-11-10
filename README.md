# Sistema de Jogo de Xadrez em Java

Este projeto é um jogo de xadrez completo, jogável via console, desenvolvido inteiramente em Java. O foco principal é a aplicação profunda dos conceitos de Programação Orientada a Objetos (POO) — como encapsulamento, herança e polimorfismo — para criar um sistema lógico, coeso e bem estruturado.

Este projeto foi desenvolvido como parte integrante do curso "Java COMPLETO Programação Orientada a Objetos +Projetos" do professor Nélio Alves.

## Conceitos e Arquitetura

O projeto é construído sobre uma arquitetura em camadas que separa claramente as responsabilidades, facilitando a manutenção e a compreensão do código:

### Camada boardgame (Núcleo do Tabuleiro):

- Contém as classes genéricas para um jogo de tabuleiro, como Board (Tabuleiro), Piece (Peça) e Position (Posição).

- Esta camada não sabe nada sobre "xadrez"; ela apenas gerencia um tabuleiro com linhas, colunas e peças.

### Camada chess (Regras do Xadrez):

- Contém as classes e lógicas específicas do xadrez.

### ChessMatch (Partida de Xadrez): 

- É o coração do jogo, gerenciando turnos, estado de "check" e "checkmate", e regras especiais.

### ChessPiece (Peça de Xadrez):

- Uma classe abstrata que herda de Piece e adiciona o conceito de Color (Cor).

### Peças Concretas (/pieces):

- Classes como King, Rook, Pawn, Bishop, Knight e Queen herdam de ChessPiece.

### Camada main (Aplicação):

- Contém a classe Application, que possui o game loop principal.

### UI (User Interface):

- Responsável por imprimir o tabuleiro no console (incluindo cores) e ler a entrada do usuário (ex: "e2", "e4").

## Destaques da Implementação (POO)

### Polimorfismo: 

- O método possibleMoves() é abstrato na classe Piece. Cada peça concreta (Rei, Torre, Peão, etc.) implementa sua própria versão desse método, permitindo que a classe ChessMatch trate todas as peças de forma genérica sem precisar saber o tipo específico de cada uma.

### Encapsulamento: 

- A lógica de validação de movimentos e o estado interno do tabuleiro (Board) e da partida (ChessMatch) estão protegidos. As classes externas (como a UI) apenas solicitam ações (ex: performChessMove), e a própria partida se encarrega de validar e executar.

### Tratamento de Exceções: 

- O projeto utiliza exceções customizadas (BoardException, ChessException) para lidar com erros de regras de negócio, como tentar mover uma peça para uma posição inválida ou fornecer uma coordenada inexistente.

## Funcionalidades Implementadas
O jogo inclui todas as regras fundamentais do xadrez:

### Movimentação Completa: 

- Todas as peças (Rei, Rainha, Bispo, Cavalo, Torre e Peão) se movem de acordo com suas regras oficiais.

### Lógica de Captura: 

- Implementação correta da captura de peças adversárias.

### Estado de "Check": 

- O sistema identifica ativamente quando um rei está em "check".

### Estado de "Checkmate": 

- O jogo termina quando um jogador aplica "checkmate" no adversário.

## Movimentos Especiais:

### Roque (Castling): 

- Implementação do Roque pequeno (lado do rei) e do Roque grande (lado da rainha).

### En Passant: 

- Lógica completa para a captura especial en passant do peão.

### Promoção (Promotion): 

- Quando um peão alcança o final do tabuleiro, o jogador é solicitado a promovê-lo (para Rainha, Torre, Bispo ou Cavalo).

## Como Executar o Projeto
### Pré-requisitos:

- **JDK 17 ou superior.**

- **Uma IDE Java (como IntelliJ IDEA ou Eclipse).**

### Clonar o Repositório:
```
Bash

git clone https://github.com/LuizArtur29/chess-system-java.git
```
### Executar:

- **Abra o projeto na sua IDE.**

- **Localize e execute o método main na classe src/main/Application.java.**

- **O jogo será iniciado no seu console.**

## Estrutura de Pacotes
```
src
├── boardgame       # Camada base (genérica) do tabuleiro
│   ├── Board.java
│   ├── BoardException.java
│   ├── Piece.java
│   └── Position.java
│
├── chess           # Camada de regras e peças do xadrez
│   ├── pieces      # Implementação de cada peça (King, Rook, Pawn, etc.)
│   ├── ChessException.java
│   ├── ChessMatch.java
│   ├── ChessPiece.java
│   ├── ChessPosition.java
│   └── Color.java
│
└── main            # Camada de aplicação (execução e UI)
    ├── Application.java
    └── UI.java
```
