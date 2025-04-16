n=int(input("numero de intentos:"))
import random

def elegir_palabra():
    """Elige una palabra secreta al azar de una lista."""
    palabras = ["manzana", "banana", "cereza", "datil", "uva", "kiwi"]
    return random.choice(palabras)

def mostrar_tablero(palabra_oculta, letras_adivinadas):
    """Muestra el tablero con las letras adivinadas y guiones para las no adivinadas."""
    tablero = ""
    for letra in palabra_oculta:
        if letra in letras_adivinadas:
            tablero += letra + " "
        else:
            tablero += "_ "
    print(tablero.strip())

def jugar_ahorcado():
    """Función principal para ejecutar el juego del ahorcado."""
    palabra_secreta = elegir_palabra()f
    letras_adivinadas = set()
    vidas = n

    print("¡Bienvenido al juego del Ahorcado!")
    print(f"La palabra secreta tiene {len(palabra_secreta)} letras.")

    while vidas > 0:
        mostrar_tablero(palabra_secreta, letras_adivinadas)
        print(f"Vidas restantes: {vidas}")
        print(f"Letras adivinadas: {', '.join(sorted(list(letras_adivinadas)))}")

        intento = input("Ingresa una letra: ").lower()

        if len(intento) != 1 or not intento.isalpha():
            print("Por favor, ingresa una única letra válida.")
            continue

        if intento in letras_adivinadas:
            print("Ya has intentado esa letra. Intenta con otra.")
            continue

        letras_adivinadas.add(intento)

        if intento in palabra_secreta:
            print("¡Correcto!")
            if all(letra in letras_adivinadas for letra in palabra_secreta):
                print(f"¡Felicidades! Adivinaste la palabra: {palabra_secreta}")
                break
        else:
            vidas -= 1
            print(f"Incorrecto. Pierdes una vida.")
            if vidas == 0:
                print(f"¡Perdiste! La palabra secreta era: {palabra_secreta}")

    if vidas == 0:
        print("¡Fin del juego!")

if __name__ == "__main__":
    jugar_ahorcado()
