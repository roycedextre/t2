import random

class Entrenador:
    def __init__(self, nombre):
        self.nombre = nombre

class Pokemon:
    def __init__(self, nombre):
        self.nombre = nombre
        self.max_ataque = random.randint(20, 100)
        self.vida_max = random.randint(150, 400)
        self.vida_actual = self.vida_max

    def recuperar(self):
        self.vida_actual = self.vida_max

# Variables globales
ganadas = 0
perdidas = 0

# Funciones
def crearEntrenadorPokemon(num):
    if num == 1:
        print("\n--- Creando tu entrenador ---")
    else:
        print("\n--- Creando entrenador rival ---")

    nombre_entrenador = input("Nombre del entrenador: ")
    nombre_pokemon = input("Nombre del Pokémon: ")

    entrenador = Entrenador(nombre_entrenador)
    pokemon = Pokemon(nombre_pokemon)

    print(f"\nEntrenador {entrenador.nombre} con Pokémon {pokemon.nombre} creado.")
    print(f"Ataque: {pokemon.max_ataque}, Vida máxima: {pokemon.vida_max}")
    return entrenador, pokemon

def valorDeAtaque(pokemon):
    return random.randint(0, pokemon.max_ataque)

def defender(pokemon, ataque):
    dado = random.randint(1, 6)
    if dado == 6:
        print("🛡️ El ataque fue esquivado!")
        ataque = 0
    pokemon.vida_actual -= ataque
    if pokemon.vida_actual < 0:
        pokemon.vida_actual = 0
    return pokemon.vida_actual

# Programa principal
print("=== Juego Pokémon ===")
entrenador1, pokemon1 = crearEntrenadorPokemon(1)

while True:
    print("\n1) Pelear")
    print("2) Mostrar estadísticas de mi Pokémon")
    print("3) Salir")

    opcion = input("Elige una opción: ")

    if opcion == "1":
        # Recuperar vida antes de empezar
        pokemon1.recuperar()

        # Crear rival
        entrenador2, pokemon2 = crearEntrenadorPokemon(2)

        # Pelea por turnos
        turno = 1
        while pokemon1.vida_actual > 0 and pokemon2.vida_actual > 0:
            print(f"\n--- Turno {turno} ---")

            # Ataque jugador
            ataque = valorDeAtaque(pokemon1)
            print(f"{pokemon1.nombre} ataca con {ataque}")
            defender(pokemon2, ataque)
            print(f"Vida de {pokemon2.nombre}: {pokemon2.vida_actual}")

            if pokemon2.vida_actual <= 0:
                print(f"\n🏆 Ganaste! {entrenador1.nombre} y {pokemon1.nombre} vencieron a {entrenador2.nombre}")
                ganadas += 1
                break

            # Ataque rival
            ataque = valorDeAtaque(pokemon2)
            print(f"{pokemon2.nombre} ataca con {ataque}")
            defender(pokemon1, ataque)
            print(f"Vida de {pokemon1.nombre}: {pokemon1.vida_actual}")

            if pokemon1.vida_actual <= 0:
                print(f"\n❌ Perdiste! {entrenador2.nombre} y {pokemon2.nombre} vencieron a {entrenador1.nombre}")
                perdidas += 1
                break

            turno += 1

    elif opcion == "2":
        print("\n📋 Estadísticas de tu Pokémon:")
        print(f"Nombre: {pokemon1.nombre}")
        print(f"Ataque máximo: {pokemon1.max_ataque}")
        print(f"Vida máxima: {pokemon1.vida_max}")
        print(f"Vida actual: {pokemon1.vida_actual}")
        print(f"Batallas ganadas: {ganadas}, Perdidas: {perdidas}")

    elif opcion == "3":
        print("\n👋 Fin del juego")
        print(f"Resumen de {pokemon1.nombre}:")
        print(f"Ataque: {pokemon1.max_ataque}, Vida máxima: {pokemon1.vida_max}")
        print(f"Ganadas: {ganadas}, Perdidas: {perdidas}")
        break

    else:
        print("❌ Opción inválida.")
