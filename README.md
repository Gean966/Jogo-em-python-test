# Jogo-em-python-test
Aventura nas Profundezas da Masmorra.ipynb


import time
import random

class Jogador:
    def __init__(self, nome):
        self.nome = nome
        self.vida = 100
        self.inventario = []

    def exibir_status(self):
        print(f"{self.nome}, Vida: {self.vida}")
        print("Inventário:", self.inventario)

    def atacar(self, inimigo):
        ataque = random.randint(10, 20)
        print(f"{self.nome} ataca {inimigo.nome} com força {ataque}.")
        inimigo.vida -= ataque
        print(f"{inimigo.nome} perde {ataque} de vida.")

class Inimigo:
    def __init__(self, nome, vida, ataque):
        self.nome = nome
        self.vida = vida
        self.ataque = ataque

    def atacar(self, jogador):
        print(f"{self.nome} ataca {jogador.nome}!")
        jogador.vida -= self.ataque
        print(f"{jogador.nome} perde {self.ataque} de vida.")

def batalha(jogador, inimigo):
    print("Batalha começou!")
    while jogador.vida > 0 and inimigo.vida > 0:
        jogador.exibir_status()
        jogador.atacar(inimigo)
        if inimigo.vida <= 0:
            print(f"{inimigo.nome} foi derrotado!")
            return True
        time.sleep(1)
        print()
        jogador.exibir_status()
        inimigo.atacar(jogador)
        if jogador.vida <= 0:
            print("Você foi derrotado! Fim de jogo.")
            return False
        time.sleep(1)
        print()

def explorar_caverna(jogador):
    print("Você entrou na caverna escura...")
    time.sleep(2)
    print("Você se depara com uma bifurcação...")
    escolha = input("Você quer seguir para a esquerda ou para a direita? (esq/dir): ").lower()
    if escolha == "esq":
        print("Você escolheu o caminho da esquerda...")
        time.sleep(2)
        print("Você encontrou uma espada mágica!")
        jogador.inventario.append("Espada Mágica")
    elif escolha == "dir":
        print("Você escolheu o caminho da direita...")
        time.sleep(2)
        print("Você caiu em uma armadilha de espinhos!")
        jogador.vida -= 30
        print("Você perdeu 30 de vida!")
    else:
        print("Opção inválida! Tente novamente.")
        explorar_caverna(jogador)

def resolver_enigma():
    print("Você encontrou uma porta trancada com um enigma...")
    time.sleep(2)
    print("Enigma: Qual é o começo de tudo, o fim do espaço e o fim do tempo?")
    resposta = input("Digite a resposta: ").lower()
    if resposta == "a":
        print("Parabéns! A porta se abre e você pode avançar.")
        return True
    else:
        print("Resposta incorreta! Tente novamente.")
        return False

def finalizar_jogo(jogador):
    print("Você encontrou o artefato lendário e completou sua missão!")
    print("Parabéns, você é um verdadeiro aventureiro!")
    jogador.exibir_status()
    print("Fim de jogo.")

def main():
    print("Bem-vindo ao Mundo da Aventura!")
    nome = input("Digite o nome do seu personagem: ")
    jogador = Jogador(nome)

    print(f"Bem-vindo, {jogador.nome}!")
    print("Você está diante da entrada de uma misteriosa masmorra...")
    time.sleep(2)
    print("Seu objetivo é encontrar o artefato lendário escondido dentro dela.")

    while jogador.vida > 0:
        print("\nEscolha sua próxima ação:")
        print("1. Entrar na caverna escura.")
        print("2. Resolver o enigma da porta.")
        print("3. Checar status.")
        print("4. Sair do jogo.")
        escolha = input("Escolha uma opção: ")

        if escolha == "1":
            explorar_caverna(jogador)
        elif escolha == "2":
            if resolver_enigma():
                finalizar_jogo(jogador)
                break
        elif escolha == "3":
            jogador.exibir_status()
        elif escolha == "4":
            print("Você decidiu sair do jogo. Até a próxima!")
            break
        else:
            print("Opção inválida! Tente novamente.")

        if jogador.vida <= 0:
            print("Você morreu! Fim de jogo.")
            break

# Iniciar o jogo
main()


Good Lucky
