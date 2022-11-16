# Avance-1
Tienda de videjuegos

#include <iostream>
#include <string>
#include <math.h>
#include <stdlib.h>
#include <locale.h>
#include <conio.h>
#include <stdio.h>
#include <cstring>
#include <cstdlib>

using namespace std;

int main()
{
    int  numart, opc;
    double precio, IVA = 1.16, ptotal;
    string nom_juego, clasi, caracteristicas, a_lanzamiento;
    string descripcion, genero, articulo;
    std::cout << "\t ***BIENVENIDO A VIDEO&GAME STORE***\n";
    cout << "1.- Agregar Articulo \n 2.-Modificar Articulo\n 3.-Eliminar articulo\n 4.-lista articulo\n 5. - Limpiar pantalla\n 6. - Salir" << endl;
    cin >> opc;

    switch (opc)
    {
    case 1: //Agregar articulo
        cout << "Ingrese el numero de articulo" << endl;
        cin >> numart;
        cout << "Ingrese el año de lanzamiento" << endl;
        cin >> a_lanzamiento;
        cin.ignore();
        getline(cin, a_lanzamiento);
        cout << "ingrese el nombre del juego" << endl;
        //me ignora el primer espacio
        getline(cin, nom_juego);// ejecuta los espacios en la variable
        cout << "Ingrese la clasificación del juego" << endl;
        getline(cin, clasi);
        cout << "Ingrese las caracteristicas del juego" << endl;
        getline(cin, caracteristicas);
        cout << "Ingrese la descripcion del juego" << endl;
        getline(cin, descripcion);
        cout << "Ingrese el genero del juego" << endl;
        getline(cin,genero);
        cout << "Ingrese el precio del juego" << endl;
        cin >> precio;
        ptotal = precio * IVA;
        cout << "El precio total del juego es de;\n " << ptotal;
        system("pause");
        system("cls");
        return main();
        break;

        return main();
        break;


        return 0;
    }
}

    
    //13/11/2022// PIA 
	
