README

Rodrigo Reyes A01284917

Carrera ITC

#include <stdio.h>
#include <string>
#include <iostream>

#include "Serie.hpp"
#include "Episodio.hpp"

using namespace std;

// Funciones
void leeDatosEpisodio(string &_titulo, int &_temporada, double &_calificacion){
    cout << "\nIngrese el titulo: ";
    cin.ignore();
    getline(cin, _titulo);
    cout << "Ingrese la temporada: ";
    cin >> _temporada;
    cout << "Ingrese la calificacion: " ;
    cin >> _calificacion;
}

void leeDatosSerie(string &_id, string &_titulo, int &_duracion, string &_genero, double &_calificacionPromedio, int &_cantEpisodios){
    cout << "\nIngrese un id: ";
    cin.ignore();
    getline(cin, _id);
    cout << "Ingrese un titulo: ";
    getline(cin, _titulo);
    cout << "Ingrese una duración: ";
    cin >> _duracion;
    cout << "Ingrese un genero: ";
    cin.ignore();
    getline(cin, _genero);
    cout << "Ingrese una calificacion: ";
    cin >> _calificacionPromedio;
    cout << "Ingrese la cantidad de episodios: ";
    cin >> _cantEpisodios;

}

int menu(){
    int opcionSeleccionada;

    cout << "\nMenu de opciones"
            "\n0. Salir"
            "\n1. leer datos de la Serie y crear un objeto de la Clase Serie con el método constructor con parámetros."
            "\n2. setId(string):void"
            "\n3. setTitulo(string):void"
            "\n4. setDuracion(int):void"
            "\n5. setGenero(string):void"
            "\n6. setCalificacion(double):void"
            "\n7. setCantidadEpisodios(int):void"
            "\n8. Desplegar serie con el método str( )"
            "\n9. Leer datos del objeto Episodio y crear un objeto con el constructor con parámetros"
            "\n10.desplegar episodio con el método str( )"
            "\n11.Añadir episodios"
            "\nIngrese el número de la opción que desee usar: ";
    
    cin >> opcionSeleccionada;
    return opcionSeleccionada;
}

// MAIN
int main() {
    // Link video
    // https://youtu.be/wqDnjx-gcgc

    // Declaración de objetos de la clase Serie y Episodio
    Serie serie;
    Episodio episodio;

    // Declaración de variables de Serie y Episodio
    string id, titulo, genero;
    int duracion, cantEpisodios, temporada;
    double calificacionPromedio, calificacion;

    // Inicializacion de vccc
    int opcionMenu;

    // Mostrar menu, que retorna la opcion seleccionada por el usaurio
    opcionMenu = menu();

    // Declaración de condiccion vccc
    while (opcionMenu != 0){

        if (opcionMenu == 1){
            // Llamar a funcion leeDatosSerie con parametros por referencia - obtener valor de parametros para crear objeto
            leeDatosSerie(id, titulo, duracion, genero, calificacionPromedio, cantEpisodios);

            // Crear objeto temporal de clase Serie con constructor con parametros
            Serie serieTemp{id, titulo, duracion, genero, calificacionPromedio, cantEpisodios};
            cout << "Serie creada con los siguientes datos: " << serieTemp.str() << endl;

            // Asignar valor de objeto temporal al objeto que se usa en main
            serie = serieTemp;
        }        
        else if (opcionMenu == 2){
            cout << "\nIngrese un id: ";
            cin.ignore();
            getline(cin, id);
            serie.setId(id);
        }
        else if (opcionMenu == 3){
            cout << "\nIngrese un titulo: ";
            cin.ignore();
            getline(cin, titulo);
            serie.setTitulo(titulo);
        }
        else if (opcionMenu == 4){
            cout << "\nIngrese una duración: ";
            cin >> duracion;
            serie.setDuracion(duracion);
        }
        else if (opcionMenu == 5){
            cout << "\nIngrese un genero: ";
            cin.ignore();
            getline(cin, genero);
            serie.setGenero(genero);
        }
        else if (opcionMenu == 6){
            cout << "\nIngrese una calificacion: ";
            cin >> calificacionPromedio;
            serie.setCalificacion(calificacionPromedio);
        }
        else if (opcionMenu == 7){
            cout << "\nIngrese la cantidad de episodios: ";
            cin >> cantEpisodios;
            serie.setCantidadEpisodios(cantEpisodios);
        }
        else if (opcionMenu == 8){
            cout << "\nSerie con datos " << serie.str() << endl;
        }
        else if (opcionMenu == 9){
            // Llamar a funcion leeDatosEpisodio con parametros por referencia - obtener valor de parametros para crear objeto
            leeDatosEpisodio(titulo, temporada, calificacion);
            
            // Crear objeto temporal de clase Episodio  con constructor con parametros
            Episodio episodioTemp{titulo, temporada, calificacion};
            cout << "Episodio creado con los siguientes datos: " << episodioTemp.str() << endl;
            
            // Asignar valor de objeto temporal al objeto que se usa en main
            episodio = episodioTemp;
        }
        else if (opcionMenu == 10){
            cout << "\nEpisodio con datos " << episodio.str() << endl;
        }
        else if (opcionMenu == 11){
            serie.addEpisodio(Episodio("Clases",1 ,90));
            serie.addEpisodio(Episodio("Constructores",1 ,90));
            serie.addEpisodio(Episodio("Composicion",1 ,99.5));
            serie.addEpisodio(Episodio("Arreglos",1 ,99.5));
            serie.addEpisodio(Episodio("Clase Arreglos",1 ,100));
            serie.addEpisodio(Episodio("Calificacion Final",1 ,100));
            serie.calculaCalificacionPromedio();
            cout << serie.str() << endl;
            serie.delEpisodio();
            serie.addEpisodio(Episodio("Calificacion Final",1 ,100));
            cout << serie.str() << endl;
        }
        else {
            cout << "\nOpcion no existente, intente de nuevo" << endl;
        }
        
        // Actualizar vccc
         opcionMenu = menu();
    }

  return 0;
} 
