# Gauss-Jordan-en-C

Programa en lenguaje C, que permite realizar la reduccion por Gauss Jordan de matrices cuadradas de hasta 3x3

	```
		
		#include <stdio.h>
    
    #include <stdlib.h>
    
		#define F 100
    
    #define C 100
	
	int n,cont=1,sumador=0,aux;
	float A [F][C];
	
	
	int main(int argc, char *argv[]) {
		
		
		printf ("\n------------------------------------------------\n\n");
		puts ("Programa que reducira matrices de tamaño nxm\n");
		puts ("Por medio del metodo de Gauss Jordan\n");
		puts ("++++++++++++++++++++++++++++++++++++++++++\n");
		puts ("Recuerde que las matrices para poder ser reducidas\n ");
		puts ("deben tener su determinante (D) distinto de 0\n");
		puts ("++++++++++++++++++++++++++++++++++++++++++\n");
		puts ("Con fines educativos solamente se permitira reducir\n");
		puts ("Matrices cuadradas de 3 variables unicamente [3x3]\n\n");
		printf ("\n-----------------------------------------------\n\n");	
    
     	printf ("\n-----------------------------------------------\n\n");
      printf ("\n PROGRAMA REALIZADO POR MATIAS CABRERA - EN OUER3D \n\n");
      printf ("\n-----------------------------------------------\n\n");
		
		system ("PAUSE");
   	system("cls");
		
		printf ("\nIngrese la cantidad de variables para su matriz ( Max 3): ");
		scanf ("%d",&n);
		
		for (int i=0;i<3;i++){
			
			printf("\n X=");
			scanf ("%f",&A[i][0]);
			printf(" Y=");
			scanf ("%f",&A[i][1]);
			printf(" Z=");
			scanf ("%f",&A[i][2]);       //Escribir variables ( X, Y , Z )
			printf(" Resultado=");
			scanf ("%f",&A[i][3]);
			printf("\n");
		}
		
		printf ("\n--------------------------------------------------\n\n\n");
		for (int i=0;i<n;i++){
			printf ("%.0f x %.0f y %.0f z = %.0f\n",A[i][0],A[i][1],A[i][2],A[i][3]); // Escribir en forma de matriz
		}
		printf("\n");
		
		printf ("\n\n--------------------------------------------------\n\n");
		for (int i=0;i<n;i++){                                                       // Imprimo en forma de matriz
			printf ("%.f   %.f   %.f   | %.0f\n",A[i][0],A[i][1],A[i][2],A[i][3]); // Matriz A
		}
		printf ("\n\n--------------------------------------------------\n\n");
		
		system ("PAUSE");
		
		if (A[0][0] == 0){
			
			if (A[1][0] == 1 && A[2][0] != 1){
				
				cont = 1;
			}
			if (A[2][0] >= 1 && A[1][0] != 1){
				
				cont = 2;	
				}
				
			if (A[1][0] == 1 && A[2][0] == 1){
				
				cont = 1;	
			}
		}
		if (cont == 1){
		  
		  for (int i=0;i<n+1;i++){
			aux = A[0][i];
			A[0][i] = A[1][i];
			A[1][i] = aux;
		  }
		}
		else {
			if (cont == 2){
				for (int i=0;i<n+1;i++){
					aux = A[0][i];
					A[0][i] = A[2][i];
					A[2][i] = aux;
				}
			}
		}
		
		// Comienza a volverse 1 0 0 la columna primera	
		
		aux = A[0][0];
		if ( aux != 1){
		for (int i=0;i<n+1;i++){                                                      // se vuelve 1 la posicion 22 de la matriz 
			
			A [0][i] = (A[0][i] / aux);
		} 
		}
		
		aux      = A[1] [0] * (-1) ;
		for (int i=0;i<n+1;i++){                                                      // Vuelvo 0 la posicion 02
			
			A [1][i] = A [1][i] + (A[0][i] * aux);
		}
		
		aux      = A[2][0] * (-1) ;
		for (int i=0;i<n+1;i++){                                                      // Vuelvo 0 la posicion 12
			
			A [2][i] = A [2][i] +  (A[0][i] * aux);
		}
		
				
		// Imprimo resultado de la primera operacion 1 0 0
		printf ("\n\n--------------------------------------------------\n\n");
		for (int i=0;i<n;i++){                                                       // Imprimo en forma de matriz
			printf ("%.f   %.f   %.f   | %.f\n",A[i][0],A[i][1],A[i][2],A[i][3]); // Matriz A
		}
		printf ("\n\n--------------------------------------------------\n\n");

		
		// Comienza a volverse 0 1 0 la columna segunda
		
		aux = A[1][1];
		if ( aux != 1){
		for (int i=0;i<n+1;i++){                                                      // se vuelve 1 la posicion 11 de la matriz 
			
			A [1][i] = A [1][i] / aux; 
		} 
		}
		aux      = A[0][1] * (-1) ;
		for (int i=0;i<n+1;i++){                                                      // Vuelvo 0 la posicion 01
					
			A [0][i] = A [0][i] + ( A[1][i] * aux);
		}
		
		aux      = A[2][1] * (-1) ;
		for (int i=0;i<n+1;i++){                                                      // Vuelvo 0 la posicion 21
						
			A [2][i] = A [2][i] + ( A[1][i] * aux);
		}
						
		// Imprimo resultado de la primera operacion 0 1 0
		printf ("\n\n--------------------------------------------------\n\n");
		for (int i=0;i<n;i++){                                                       // Imprimo en forma de matriz
			printf ("%.f   %.f   %.f   | %.2f\n",A[i][0],A[i][1],A[i][2],A[i][3]); // Matriz A
		}
		printf ("\n\n--------------------------------------------------\n\n");

	
		// Comienza a volverse 0 0 1 la columna tercera
		aux = A[2][2];
		if ( aux != 1){
		for (int i=0;i<n+1;i++){                                                      // se vuelve 1 la posicion 22 de la matriz 
			
			A [2][i] = A [2][i] / aux; 
		}
		}
		
		aux      = A[0][2] * (-1) ;
		for (int i=0;i<n+1;i++){                                                      // Vuelvo 0 la posicion 02
						
			A [0][i] = A [0][i] + ( A[2][i] * aux);
		}
		
		aux      = A[1][2] * (-1) ;
		for (int i=0;i<n+1;i++){                                                      // Vuelvo 0 la posicion 12
			
			A [1][i] = A [1][i] + ( A[2][i] * aux);
		}
		
				
		// Imprimo resultado de la primera operacion 0 0 1
		printf ("\n\n--------------------------------------------------\n\n");
		for (int i=0;i<n;i++){                                                       // Imprimo en forma de matriz
			printf ("%.f   %.f   %.f   | %.2f\n",A[i][0],A[i][1],A[i][2],A[i][3]); // Matriz A
		}
		printf ("\n\n--------------------------------------------------\n\n");
        puts("La solucion es:\n");
		printf ("| %.2f | \n| %.2f | \n| %.2f | \n",A[0][3],A[1][3],A[2][3]);
		
		
		return 0;
		system ("PAUSE");
	}
	

		```
