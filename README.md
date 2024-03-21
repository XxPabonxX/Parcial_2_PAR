# Parcial_2_PAR
#include <iostream>
#include <stdlib.h>
#include <iomanip>

using namespace std;
double normalizacion(double matriz_imagen[10][10]);
void normal_prom(double matriz_normal[10][10], double promedio, int uno[10]);

int main() {

	int ceroXcolumna[10]{ };
	double prom = 0, matriz_imagen[10][10] =
	{
	  {234, 220, 29 , 228, 90 , 236, 89 , 241, 178,	155},
	  {136, 21 , 58 , 1  , 159, 108, 146, 225, 7  ,	154},
	  {122, 77 , 218, 1  , 254, 8  , 2  , 143, 161,	115},
	  {95 , 171, 87 , 49 , 50 , 48 , 87 , 118, 221,	192},
	  {1  , 127, 244, 60 , 141, 175, 2  , 146, 181,	53 },
	  {174, 112, 9  , 186, 157, 128, 2  , 51 , 143,	87 },
	  {189, 78 , 3  , 236, 2  , 91 , 169, 241, 117,	151},
	  {94 , 151, 77 , 109, 148, 173, 211, 52 , 83 ,	2  },
	  {20 , 135, 3  , 146, 2  , 112, 202, 83 , 2  ,	19 },
	  {179, 1  , 178, 252, 2  , 59 , 80 , 1  , 52 ,	215}
	};

	prom = normalizacion(matriz_imagen);
	cout << endl << "El promedio de la matriz normalizada es: " << prom << endl;

	normal_prom(matriz_imagen, prom, ceroXcolumna);
	cout << endl << "La matriz 1 y 0 es: " << endl << endl;

	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 10; j++)
		{
			cout << setw(11) << matriz_imagen[i][j] << " ";
		}
		cout << endl;
	}

	cout << endl << "El vector de cantidad de unos es: [" ;

	for (int i = 0; i < 10; i++)
	{
		cout << ceroXcolumna[i] << " ";
	}
	cout << "]" << endl;

	system("Pause");
	return 0;
}

// funcion 1.
double normalizacion(double matriz_imagen[10][10]) {

	float prom = 0;

	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 10; j++)
		{
			matriz_imagen[i][j] = matriz_imagen[i][j] / 255;
			prom += matriz_imagen[i][j];
		}
	}

	system("cls");
	cout << "La matriz de la imagen normalizada es: " << endl << endl;

	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 10; j++)
		{
			cout << setw(11) << matriz_imagen[i][j] << " ";
		}
		cout << endl;
	}

	prom = prom / 100;

	return prom;
}

// funcion 2.
void normal_prom(double matriz_normal[10][10], double promedio, int uno[10]) {

	int cont_uno = 0;

	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 10; j++)
		{
			matriz_normal[i][j] = matriz_normal[i][j] - promedio;

			if (matriz_normal[i][j]>0.3)
			{
				matriz_normal[i][j] = 1;
			}
			else
			{
				matriz_normal[i][j] = 0;
			}
		}
	}

	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 10; j++)
		{
			if (matriz_normal[j][i]>0.3)
			{
				cont_uno++;
			}
		}

		uno[i] = cont_uno;
		cont_uno = 0;

	}

}
