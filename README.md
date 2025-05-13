# 🎮 Terminal Adventure

Bem-vindo ao **Terminal Adventure**, um jogo de aventura em texto no terminal feito com Python!

Você é um aventureiro perdido nas misteriosas **Terras de Podridão**. Derrote monstros, evolua seu personagem e conquiste todos os cenários para sair vivo desse lugar amaldiçoado.

---

## 🧠 Funcionalidades

- Sistema de batalhas com inimigos únicos.
- Escolhas de ação: atacar, curar, bloquear ou fugir.
- Níveis, experiência (XP), evolução de atributos (HP e dano).
- Quatro cenários principais com duas salas de batalha em cada.
- Progresso salvo automaticamente e carregado ao iniciar o jogo.
- Efeitos sonoros simples (beep via terminal).
- Finalização automática e limpa do jogo ao vencer todos os inimigos.

---

## 📁 Estrutura do Projeto

TerminalAdventure/
│
├── game/
│ ├── init.py
│ ├── engine.py # lógica principal do jogo
│ ├── player.py # dados e progresso do jogador
│ ├── battle.py # sistema de combate
│ ├── areas.py # locais e salas do jogo
│ └── save.py # sistema de salvamento
│
├── assets/
│ └── savegame.txt # arquivo de salvamento (gerado automaticamente)
│
├── main.py # ponto de entrada do jogo
└── README.md # este arquivo

---

## ▶️ Como Jogar

### Pré-requisitos

- Python 3.10 ou superior instalado no sistema.

### Executar o jogo

```bash
python main.py

Controles
Durante o jogo, você poderá:

Escolher cenários para explorar.

Lutar contra inimigos com opções de combate:

1 Atacar

2 Bloquear

3 Curar

4 Fugir da batalha

O jogo salva automaticamente seu progresso.

Quando derrotar todos os inimigos principais, o jogo termina com vitória.

💾 Salvamento
O progresso é salvo automaticamente em assets/savegame.txt.

Ao iniciar o jogo, será perguntado se deseja continuar de onde parou.
