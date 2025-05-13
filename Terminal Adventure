import random

print("🌪️ Bem-vindo ao Terminal Adventure!")
print("Você está perdido nas Terras de Podridão e precisa sobreviver.")
player_name = input("Qual o seu nome, aventureiro? ")

# STATUS DO JOGADOR
player_hp = 100
player_max_hp = 100
player_xp = 0
player_level = 1
player_dano = 15

# INIMIGOS VENCIDOS
vencidos = {
    "floresta": False,
    "ruinas": False,
    "caverna": False,
    "torre": False
}
salas = {
    "floresta": False,
    "ruinas": False,
    "caverna": False,
    "torre": False
}

# FUNÇÕES AUXILIARES
def mostrar_status():
    print(f"\n📊 {player_name} — HP: {player_hp}/{player_max_hp} | XP: {player_xp} | Nível: {player_level} | Dano: {player_dano}")

def subir_nivel():
    global player_level, player_max_hp, player_hp, player_dano
    novo_nivel = player_xp // 50 + 1
    if novo_nivel > player_level:
        print(f"\n🆙 {player_name} subiu para o Nível {novo_nivel}!")
        player_level = novo_nivel
        player_max_hp += 20
        player_dano += 5
        player_hp = player_max_hp

# BATALHA
def batalha(nome_inimigo, vida_base, xp):
    global player_hp, player_xp

    vida_inimigo = vida_base + (player_level - 1) * 10
    dano_inimigo = 10 + (player_level - 1) * 3

    print(f"\n⚔️ Você encontrou {nome_inimigo}! Prepare-se!")

    while player_hp > 0 and vida_inimigo > 0:
        mostrar_status()
        print(f"{nome_inimigo} HP: {vida_inimigo}")
        print("O que deseja fazer?" \
              "\n1. Atacar" \
              "\n2. Bloquear" \
              "\n3. Curar" \
              "\n4. Fugir")
        acao = input("> ")

        if acao == "1":
            dano = random.randint(player_dano - 5, player_dano + 5)
            vida_inimigo -= dano
            print(f"Você causou {dano} de dano!")
        elif acao == "2":
            dano_sofrido = max(0, random.randint(dano_inimigo - 5, dano_inimigo + 5) - 10)
            player_hp -= dano_sofrido
            print(f"Você bloqueou! Sofreu {dano_sofrido} de dano.")
            continue
        elif acao == "3":
            cura = random.randint(10, 25)
            player_hp = min(player_max_hp, player_hp + cura)
            print(f"Você se curou em {cura}.")
        elif acao == "4":
            print("🏃 Você fugiu da batalha!")
            return False
        else:
            print("Ação inválida.")
            continue

        if vida_inimigo > 0:
            dano = random.randint(dano_inimigo - 5, dano_inimigo + 5)
            player_hp -= dano
            print(f"O inimigo atacou e causou {dano} de dano!")

    if player_hp <= 0:
        print("☠️ Você foi derrotado! Fim de jogo.")
        exit()
    else:
        print(f"🎉 Você venceu {nome_inimigo} e ganhou {xp} XP!")
        player_xp += xp
        subir_nivel()
        return True

# EXPLORAR SALAS
def explorar_salas(nome):
    if salas[nome]:
        return True
    print(f"\n🔍 Explorando as salas de {nome.title()}...")

    inimigos = [("Sentinela", 30), ("Bicho Sombrio", 35), ("Criatura Perdida", 30), ("Espírito Errante", 35)]
    for i in range(0, 4, 2):
        print(f"\nSala {(i//2)+1}")
        if not batalha(inimigos[i][0], inimigos[i][1], 10): return False
        if not batalha(inimigos[i+1][0], inimigos[i+1][1], 10): return False

    salas[nome] = True
    print("✅ Salas limpas!")
    return True

# CENÁRIOS
def floresta():
    if vencidos["floresta"]:
        print("🌲 A floresta já está em paz.")
    else:
        if explorar_salas("floresta"):
            if batalha("Lobo das Sombras", 60, 20):
                vencidos["floresta"] = True
    menu()

def ruinas():
    if vencidos["ruinas"]:
        print("🏛️ As ruínas estão vazias.")
    else:
        if explorar_salas("ruinas"):
            if batalha("Guardião de Pedra", 70, 25):
                vencidos["ruinas"] = True
    menu()

def caverna():
    if vencidos["caverna"]:
        print("🕳️ A caverna já está segura.")
    else:
        if explorar_salas("caverna"):
            if batalha("Aranha Gigante", 65, 25):
                vencidos["caverna"] = True
    menu()

def torre():
    if vencidos["torre"]:
        print("🗼 Você já venceu o jogo.")
        fim()
    else:
        if explorar_salas("torre"):
            if batalha("Feiticeiro Fantasma", 80, 40):
                vencidos["torre"] = True
                fim()

# FIM DO JOGO
def fim():
    print("\n🏆 Você venceu todos os desafios das Terras de Podridão!")
    mostrar_status()
    print("\nDigite 1 para encerrar o jogo.")
    while True:
        fim = input("> ")
        if fim == "1":
            print("👋 Obrigado por jogar! Até a próxima aventura.")
            exit()
        else:
            print("Digite apenas 1 para encerrar.")

# MENU
def menu():
    mostrar_status()
    print("\nEscolha para onde ir:")
    print("1. Floresta Misteriosa")
    print("2. Ruínas Antigas")
    print("3. Caverna Escura")
    print("4. Torre Abandonada")
    escolha = input("> ")

    if escolha == "1":
        floresta()
    elif escolha == "2":
        ruinas()
    elif escolha == "3":
        caverna()
    elif escolha == "4":
        torre()
    else:
        print("Caminho desconhecido...")
        menu()

# INÍCIO
menu()
