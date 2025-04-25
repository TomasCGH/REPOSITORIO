# REPOSITORIO
Trabajo de clase DOO

import java.util.Scanner;

public class Ahorcado {

    private static final String[] AHORCADO_DIBUJO = {
            """
          +---+
          |   |
          O   |
         /|\\  |
         / \\  |
              |
        =========""",
            """
          +---+
          |   |
          O   |
         /|\\  |
         /    |
              |
        =========""",
            """
          +---+
          |   |
          O   |
         /|\\  |
              |
              |
        =========""",
            """
          +---+
          |   |
          O   |
         /|   |
              |
              |
        =========""",
            """
          +---+
          |   |
          O   |
          |   |
              |
              |
        =========""",
            """
          +---+
          |   |
          O   |
              |
              |
              |
        =========""",
            """
          +---+
          |   |
              |
              |
              |
              |
        ========="""
    };

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);


        System.out.print("Jugador 1, ingresa la palabra secreta: ");
        String palabraSecreta = scanner.nextLine().toLowerCase();


        System.out.println("\n".repeat(50));


        char[] palabraOculta = new char[palabraSecreta.length()];
        for (int i = 0; i < palabraOculta.length; i++) {
            palabraOculta[i] = '*';
        }

        int intentos = 6;
        boolean palabraAdivinada = false;

        while (intentos > 0 && !palabraAdivinada) {
            System.out.println(AHORCADO_DIBUJO[intentos]);
            System.out.println("Palabra: " + String.valueOf(palabraOculta));
            System.out.println("Intentos restantes: " + intentos);
            System.out.print("Jugador 2, ingresa una letra: ");
            char letra = scanner.next().toLowerCase().charAt(0);

            boolean acierto = false;
            for (int i = 0; i < palabraSecreta.length(); i++) {
                if (palabraSecreta.charAt(i) == letra) {
                    palabraOculta[i] = letra;
                    acierto = true;
                }
            }

            if (!acierto) {
                intentos--;
                System.out.println("Letra incorrecta.");
            }

            if (String.valueOf(palabraOculta).equals(palabraSecreta)) {
                palabraAdivinada = true;
            }
        }


        System.out.println(AHORCADO_DIBUJO[intentos]);
        if (palabraAdivinada) {
            System.out.println("¡Felicidades! Has adivinado la palabra: " + palabraSecreta);
        } else {
            System.out.println("¡Perdiste! La palabra era: " + palabraSecreta);
        }

        scanner.close();
    }
}
