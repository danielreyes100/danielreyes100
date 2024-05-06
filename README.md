#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <time.h>
#include <conio.h>
#include <string.h>

//librerias

#define MAX_ARF 3
#define MAX_ARC 3
#define MAX_TEMPO 8
// definiciones

char tablero[MAX_ARF][MAX_ARC];
// funciones globales



void tablero_inicial();
void inicial();
void turno_usuario(int pos);
void turno_maquina();
void pos(int pos, int *fila, int *columna);
// Prototipos de funciones

int main() {

	tablero_inicial();
	inicial();		    
    
    return 0;
}
// FunciÃ³n principal 
void inicial() {
    int pos = 0;
    int contador = 0;
    
    // Bucle principal del juego
    do {
        /*system("cls"); // Limpia la pantalla*/ 
        tablero_inicial(); // Muestra el tablero actual
        
        // Turno del usuario si el contador es par, de lo contrario, turno de la máquina
	        if (contador % 2 == 0) {
	            printf("Turno del usuario (X).\n");
	            printf("Ingrese un numero del 1 al 9 para colocar su X: ");
	            scanf("%d", &pos);
	        do{
				
	            // Valida la entrada del usuario
	            if (pos < 1 || pos > 9) {
	                printf("\n El valor ingresado no es valido. Inténtelo de nuevo.\n ");
	                // Reinicia el bucle si la entrada no es válida
	            }
	        }while(pos<1 || pos >9);
	            turno_usuario(pos); // Realiza el movimiento del usuario
        } else {
            printf("Turno de la máquina (O).\n");
            turno_maquina(); // Realiza el movimiento de la máquina
        }
        
        contador++; // Incrementa el contador de movimientos
    } while (contador <= 9); // Continúa hasta que se completen 9 movimientos
}
	// Imprimir el tablero actual
	void tablero_inicial() {
	    int filas=0;
		int columnas=0;
	    for (filas= 0; filas < MAX_ARF; filas++) {
	        for ( columnas = 0; columnas < MAX_ARC; columnas++) {
	            tablero[filas][columnas] = '1' + filas * MAX_ARC + columnas; 
	        }
	    }//NÃºmeros del 1 al 9 
		printf(" Tablero Triqui\n");
	    printf("-------------\n");
	    int fila=0;
		int columna=0;
	    for ( fila = 0; fila < MAX_ARF; fila ++) {
	        for ( columna= 0; columna < MAX_ARC; columna++) {
	            printf("| %c ", tablero[fila][columna]);
	        }
	        printf("|\n");
	        printf("-------------\n");
	    }//creaciÃ³n del tablero 
	}//fin

// Realizar el turno del usuario
void turno_usuario(int pos) {
    int fila, columna;
    fila = (pos - 1) / MAX_ARC;
    columna = (pos - 1) % MAX_ARC;
    
    printf("Fila: %d, Columna: %d\n", fila, columna); // Mensaje de depuración
    
    if (fila < 0 || fila >= MAX_ARF || columna < 0 || columna >= MAX_ARC || tablero[fila][columna] == 'X' || tablero[fila][columna] == 'O') {
        printf("La casilla ya está ocupada o la posición es inválida. Por favor, elija otra.\n");
    } else {
        tablero[fila][columna] = 'X';
    }
}
// Convertir un número de posición a fila y columna en el tablero
void pos(int pos, int *fila, int *columna) {
    *fila = (pos - 1) / MAX_ARC;
    *columna = (pos - 1) % MAX_ARC;
}
// Realizar el turno de la mÃ¡quina
void turno_maquina() {

            if (tablero[1][1] == 'X') { // Comprueba si la posición 5 está disponible
                tablero[0][2] = 'O'; // Coloca la ficha de la máquina en la posición 3
            }
        /*
            break;
        case 7: // Si el jugador ha jugado en la posición 7
        case 1: // o en la posición 1
            if (tablero[2][0] == 'X' || tablero[0][0] == 'X') {
                tablero[2][2] = 'O'; // Coloca la ficha de la máquina en la posición 9
            }
            break;
        case 9: // Si el jugador ha jugado en la posición 9
            if (tablero[2][2] == 'X') {
                tablero[0][0] = 'O'; // Coloca la ficha de la máquina en la posición 1
            }
            break;
        case 8: // Si el jugador ha jugado en la posición 8
            if (tablero[2][1] == 'X') {
                tablero[0][1] = 'O'; // Coloca la ficha de la máquina en la posición 2
            }
            break;
        case 6: // Si el jugador ha jugado en la posición 6
            if (tablero[1][2] == 'X') {
                tablero[1][0] = 'O'; // Coloca la ficha de la máquina en la posición 4
            }
            break;
        case 4: // Si el jugador ha jugado en la posición 4
            if (tablero[1][0] == 'X') {
                tablero[1][2] = 'O'; // Coloca la ficha de la máquina en la posición 6
            }
            break;
        case 2: // Si el jugador ha jugado en la posición 2
            if (tablero[0][1] == 'X') {
                tablero[2][1] = 'O'; // Coloca la ficha de la máquina en la posición 8
            }
            break;
        case 3: // Si el jugador ha jugado en la posición 3
            if (tablero[0][2] == 'X') {
                tablero[2][0] = 'O'; // Coloca la ficha de la máquina en la posición 7
            }
            break;
            */
    
}
