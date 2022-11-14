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
	
#include <iostream>
#include <string>
#include <fstream>
#include <stdlib.h>
#include <cstring>
struct juego {
	int ID;
	int A_lanz;
	char Nombre[40];
	char Clasi[10];
	char Carac[40];
	char Desc[40];
	char Genero[10];
	double Precio;
};
using namespace std;
int main() {
	ifstream Inv;
	Inv.open("Inventario.txt");
	int opc = 0, i = 0, Cant = 0, numart = 0;;
	struct juego* juegos = NULL;
	int exito = 0;
	if (Inv) {
		while (Inv >> numart) {
			struct juego* masjuegos = NULL;
			int a_lanz;
			double ptotal;
			char nom_juego[40] = { 0 }, clasi[10] = { 0 }, carac[40] = { 0 }, desc[40] = { 0 }, genero[10] = { 0 };
			Inv >> nom_juego;
			Inv >> a_lanz;
			Inv >> clasi;
			Inv >> genero;
			Inv >> carac;
			Inv >> desc;
			Inv >> ptotal;
			Cant++;
			masjuegos = (struct juego*)realloc(juegos, Cant * sizeof(struct juego));
			if (masjuegos != NULL) {
				juegos = masjuegos;
				juegos[Cant - 1].ID = numart;
				juegos[Cant - 1].A_lanz = a_lanz;
				strcpy(juegos[Cant - 1].Nombre, nom_juego);
				strcpy(juegos[Cant - 1].Clasi, clasi);
				strcpy(juegos[Cant - 1].Carac, carac);
				strcpy(juegos[Cant - 1].Desc, desc);
				strcpy(juegos[Cant - 1].Genero, genero);
				juegos[Cant - 1].Precio = ptotal;
			}
			else {
				free(juegos);
				puts("Error (re)allocando memoria");
				exit(1);
			}
		}
	}
	Inv.close();
	do {
		int  clasiN, generoN, numart, a_lanz, n, SID, XID, ord;
		double precio, IVA = 1.16, ptotal;
		char nom_juego[40] = { 0 }, clasi[10] = { 0 }, carac[40] = { 0 }, desc[40] = { 0 }, genero[10] = { 0 };
		struct juego* masjuegos = NULL;
		cout << Cant << endl;
		cout << "\t ***BIENVENIDO A VIDEO&GAME STORE***\n";
		cout << "1.- Agregar Articulo \n2.-Modificar Articulo\n3.-Eliminar articulo\n4.-lista articulo\n5. - Limpiar pantalla\n6. - Salir" << endl;
		cin >> opc;
		switch (opc) {
		case 1: { //Agregar articulo
			do {
				exito = 1;
				cout << "Ingrese el numero de articulo" << endl;
				cin >> numart;
				for (i = 0; i < Cant; i++) {
					if (juegos[i].ID == numart) {
						exito = 0;
					}
				}
			} while (exito == 0);
			cout << "Ingrese el año de lanzamiento" << endl;
			cin >> a_lanz;
			cin.ignore(1, '\n');
			cout << "ingrese el nombre del juego" << endl;
			cin.getline(nom_juego, 40);
			cout << "Seleccione la clasificación del juego\n1.Menores\n2.Jovenes\n3.Adultos" << endl;
			cin >> clasiN;
			switch (clasiN) {
			case 1: {
				strcpy(clasi, "Menores");
				break;
			}
			case 2: {
				strcpy(clasi, "Jovenes");
				break;
			}
			case 3: {
				strcpy(clasi, "Adultos");
				break;
			}
			}
			cin.ignore(1, '\n');
			cout << "Ingrese las caracteristicas del juego" << endl;
			cin.getline(carac, 40);
			cout << "Ingrese la descripcion del juego" << endl;
			cin.getline(desc, 40);
			cout << "Seleccione el genero del juego \n1.Shooter\n2.Carreras\n3.Aventura" << endl;
			cin >> generoN;
			switch (generoN) {
			case 1: {
				strcpy(genero, "Shooter");
				break;
			}
			case 2: {
				strcpy(genero, "Carreras");
				break;
			}
			case 3: {
				strcpy(genero, "Aventura");
				break;
			}
			}
			cin.ignore(1, '\n');
			cout << "Ingrese el precio del juego" << endl;
			cin >> precio;
			ptotal = precio * IVA;
			cout << "El precio total del juego es de;\n " << ptotal << endl;
			system("pause");
			Cant++;
			masjuegos = (struct juego*)realloc(juegos, Cant * sizeof(struct juego));
			if (masjuegos != NULL) {
				juegos = masjuegos;
				juegos[Cant - 1].ID = numart;
				juegos[Cant - 1].A_lanz = a_lanz;
				strcpy(juegos[Cant - 1].Nombre, nom_juego);
				strcpy(juegos[Cant - 1].Clasi, clasi);
				strcpy(juegos[Cant - 1].Carac, carac);
				strcpy(juegos[Cant - 1].Desc, desc);
				strcpy(juegos[Cant - 1].Genero, genero);
				juegos[Cant - 1].Precio = ptotal;
			}
			else {
				free(juegos);
				puts("Error (re)allocando memoria");
				exit(1);
			}
			break;
		}
		case 2: {
			cout << "Introduzca la ID del articulo a modificar" << endl;
			cin >> SID;
			for (i = 0; i < Cant; i++) {
				if (juegos[i].ID == SID) {
					cout << "Ingrese el año de lanzamiento" << endl;
					cin >> a_lanz;
					cin.ignore(1, '\n');
					cout << "ingrese el nombre del juego" << endl;
					cin.getline(nom_juego, 40);
					cout << "Seleccione la clasificación del juego\n1.Menores\n2.Jovenes\n3.Adultos" << endl;
					cin >> clasiN;
					switch (clasiN) {
					case 1: {
						strcpy(clasi, "Menores");
						break;
					}
					case 2: {
						strcpy(clasi, "Jovenes");
						break;
					}
					case 3: {
						strcpy(clasi, "Adultos");
						break;
					}
					}
					cin.ignore(1, '\n');
					cout << "Ingrese las caracteristicas del juego" << endl;
					cin.getline(carac, 40);
					cout << "Ingrese la descripcion del juego" << endl;
					cin.getline(desc, 40);
					cout << "Seleccione el genero del juego \n1.Shooter\n2.Carreras\n3.Aventura" << endl;
					cin >> generoN;
					switch (generoN) {
					case 1: {
						strcpy(genero, "Shooter");
						break;
					}
					case 2: {
						strcpy(genero, "Carreras");
						break;
					}
					case 3: {
						strcpy(genero, "Aventura");
						break;
					}
					}
					cin.ignore(1, '\n');
					cout << "Ingrese el precio del juego" << endl;
					cin >> precio;
					ptotal = precio * IVA;
					cout << "El precio total del juego es de;\n " << ptotal;
					juegos[i].A_lanz = a_lanz;
					strcpy(juegos[i].Nombre, nom_juego);
					strcpy(juegos[i].Clasi, clasi);
					strcpy(juegos[i].Carac, carac);
					strcpy(juegos[i].Desc, desc);
					strcpy(juegos[i].Genero, genero);
					juegos[i].Precio = ptotal;
					system("pause");
				}
			}
			break;
		}
		case 3: {
			int x = 0;
			cout << "Introduzca la ID del articulo a eliminar" << endl;
			cin >> SID;
			struct juego* aux = NULL;
			for (i = 0; i < Cant; i++) {
				if (juegos[i].ID == SID) {
					XID = i;
				}
			}
			for (i = 0; i < Cant - 1; i++) {
				if (i == XID) {
					x++;
				}
				masjuegos = (struct juego*)realloc(aux, Cant * sizeof(struct juego));
				aux = masjuegos;
				aux[i].ID = juegos[i + x].ID;
				aux[i].A_lanz = juegos[i + x].A_lanz;
				strcpy(aux[i].Nombre, juegos[i + x].Nombre);
				strcpy(aux[i].Clasi, juegos[i + x].Clasi);
				strcpy(aux[i].Carac, juegos[i + x].Carac);
				strcpy(aux[i].Desc, juegos[i + x].Desc);
				strcpy(aux[i].Genero, juegos[i + x].Genero);
				aux[i].Precio = juegos[i + x].Precio;
			}
			free(juegos);
			juegos = aux;
			Cant--;
			cout << "Borrado con exito" << endl;
			break;
		}
		case 4: {
			if (Cant == 0) {
				cout << "No hay articulos que mostrar" << endl;
				system("pause");
			}
			else {
				cout << "Introduzca el orden en el que desea que se muestren los juegos\n1.Por clasificacion\n2.Por genero" << endl;
				cin >> ord;
				switch (ord) {
				case 1: {
					for (i = 0; i < Cant; i++) {
						if (strstr(juegos[i].Clasi, "Menores") != NULL) {
							cout << "ID Articulo: " << juegos[i].ID << endl;
							cout << "Nombre: " << juegos[i].Nombre << endl;
							cout << "Año de lanzamiento: " << juegos[i].A_lanz << endl;
							cout << "Clasificacion: " << juegos[i].Clasi << endl;
							cout << "Genero: " << juegos[i].Genero << endl;
							cout << "Caracteristicas: " << juegos[i].Carac << endl;
							cout << "Descripcion: " << juegos[i].Desc << endl;
							cout << "Precio: " << juegos[i].Precio << endl << endl;
						}
					}
					for (i = 0; i < Cant; i++) {
						if (strstr(juegos[i].Clasi, "Jovenes") != NULL) {
							cout << "ID Articulo: " << juegos[i].ID << endl;
							cout << "Nombre: " << juegos[i].Nombre << endl;
							cout << "Año de lanzamiento: " << juegos[i].A_lanz << endl;
							cout << "Clasificacion: " << juegos[i].Clasi << endl;
							cout << "Genero: " << juegos[i].Genero << endl;
							cout << "Caracteristicas: " << juegos[i].Carac << endl;
							cout << "Descripcion: " << juegos[i].Desc << endl;
							cout << "Precio: " << juegos[i].Precio << endl << endl;
						}
					}
					for (i = 0; i < Cant; i++) {
						if (strstr(juegos[i].Clasi, "Adultos") != NULL) {
							cout << "ID Articulo: " << juegos[i].ID << endl;
							cout << "Nombre: " << juegos[i].Nombre << endl;
							cout << "Año de lanzamiento: " << juegos[i].A_lanz << endl;
							cout << "Clasificacion: " << juegos[i].Clasi << endl;
							cout << "Genero: " << juegos[i].Genero << endl;
							cout << "Caracteristicas: " << juegos[i].Carac << endl;
							cout << "Descripcion: " << juegos[i].Desc << endl;
							cout << "Precio: " << juegos[i].Precio << endl << endl;
						}
					}
					system("pause");
					break;
				}
				case 2: {
					for (i = 0; i < Cant; i++) {
						if (strstr(juegos[i].Genero, "Shooter") != NULL) {
							cout << "ID Articulo: " << juegos[i].ID << endl;
							cout << "Nombre: " << juegos[i].Nombre << endl;
							cout << "Año de lanzamiento: " << juegos[i].A_lanz << endl;
							cout << "Clasificacion: " << juegos[i].Clasi << endl;
							cout << "Genero: " << juegos[i].Genero << endl;
							cout << "Caracteristicas: " << juegos[i].Carac << endl;
							cout << "Descripcion: " << juegos[i].Desc << endl;
							cout << "Precio: " << juegos[i].Precio << endl << endl;
						}
					}
					for (i = 0; i < Cant; i++) {
						if (strstr(juegos[i].Genero, "Carreras") != NULL) {
							cout << "ID Articulo: " << juegos[i].ID << endl;
							cout << "Nombre: " << juegos[i].Nombre << endl;
							cout << "Año de lanzamiento: " << juegos[i].A_lanz << endl;
							cout << "Clasificacion: " << juegos[i].Clasi << endl;
							cout << "Genero: " << juegos[i].Genero << endl;
							cout << "Caracteristicas: " << juegos[i].Carac << endl;
							cout << "Descripcion: " << juegos[i].Desc << endl;
							cout << "Precio: " << juegos[i].Precio << endl << endl;
						}
					}
					for (i = 0; i < Cant; i++) {
						if (strstr(juegos[i].Genero, "Aventura") != NULL) {
							cout << "ID Articulo: " << juegos[i].ID << endl;
							cout << "Nombre: " << juegos[i].Nombre << endl;
							cout << "Año de lanzamiento: " << juegos[i].A_lanz << endl;
							cout << "Clasificacion: " << juegos[i].Clasi << endl;
							cout << "Genero: " << juegos[i].Genero << endl;
							cout << "Caracteristicas: " << juegos[i].Carac << endl;
							cout << "Descripcion: " << juegos[i].Desc << endl;
							cout << "Precio: " << juegos[i].Precio << endl << endl;
						}
					}
					system("pause");
					break;
				}
				}
			}
			break;
		}
		case 5: {
			system("cls");
			cout << "Pantalla limpiada\n" << endl;
			break;
		}
		case 6: {
			cout << endl << "Gracias, vuelva pronto" << endl;
			break;
		}
		}
	} while (opc != 6);
	ofstream InvO;
	InvO.open("Inventario.txt");
	for (i = 0; i < Cant; i++) {
		InvO << juegos[i].ID << endl;
		InvO << juegos[i].Nombre << endl;
		InvO << juegos[i].A_lanz << endl;
		InvO << juegos[i].Clasi << endl;
		InvO << juegos[i].Genero << endl;
		InvO << juegos[i].Carac << endl;
		InvO << juegos[i].Desc << endl;
		InvO << juegos[i].Precio << endl;
	}
	InvO.close();
	free(juegos);
	return 0;
}
