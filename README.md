# **Proyecto Final Computo Concurrente**

## **Descripcion**

El objetivo del proyecto fue la paralelizacion de un algoritmo que resuelve el problema del agente viajero empleando una heuristica de recocido simulado. 

## **Contenido** ##
Este repositorio contiene los codigos en lenguaje C utilizando tres tecnicas de paralelizacion para el programa a paralelizar **simulated_annealing.c**: **PTHREAD**, **CUDA** y **MPI**

En la carpeta **Instancias** se ubican archivos de prueba con extension .tsp los cuales constan de diferentes datos de tamaño a resolver para el problema del agente viajero es decir distinto numero de ciudades con su distancia euclidiana.


## **Instrucciones de compilacion y ejecucion**
Para poder ejecutar y compilar los codigos es necesario que la instancia y el programa esten en el mismo directorio.

**PTHREAD**

Para poder compilar y ejecutar el codigo ***recocido_pthread.c***, es necesario instalar el compilador de C/C++, se sugiere utilizar GNU debido a que tiene mejor soporte para el manejo de hilos.

**Compilacion**

Teniendo acceso al compilador de C/C++ se compila utilizando la siguiente sintaxis:

    gcc nombre_programa.c -o nombre_salida

En donde gcc indica que se utilice el compilador para compilar un archivo de C, nombre_programa.c como se intuye, indica el nombre del programa a ejecutar y nombre_salida indica un alias para el archivo que se genera y se utilice para poder ejecutar. 

Ejemplo de uso:

    gcc recocido_pthreads.c -o pthread -lm

Con esta instruccion se indica al compilador de C/C++ que compile el programa recocido_pthreads.c y el archivo para ejecutar se llame pthread. La bandera *-lm* indica que al momento de compilar se enlace la biblioteca de C *math.h* mientras que la bandera *-o* sirve para indicar el nombre de archivo de salida.

**Ejecucion**

Para ejecutar el programa se utiliza la siguiente instruccion:

    ./pthread archivo.tsp iteraciones numero_hilos

En donde pthread es el nombre indicado al momento de la compilacion, iteraciones como se intuye es el numero de iteraciones que se desea y numero_ hilos indica el numero de hilos que se desea utilizar

Ejemplo de uso:

    ./pthread berlin52.tsp 1000 20

con esta instruccion se indica que se ejecute el programa pthread, utilice el archivo berlin52.tsp, se realicen 1000 iteraciones y se creen 20 hilos.



**MPI**

Para poder compilar y ejecutar el codigo **recocido_mpi.c**, es necesario instalar el compilador mpicc (Message Passing Interface) o en su defecto utilizar un cluster. 

**Compilacion**

Teniendo acceso al compilador de mpi se compila utilizando la siguiente sintaxis:

    mpicc nombre_programa.c -o nombre_salida -lm

En donde mpicc indica que se utilice el compilador mpicc, nombre_programa.c como se intuye, indica el nombre del programa a ejecutar y nombre_salida indica un alias para el archivo que se genera y se utilice para poder ejecutar. La bandera *-lm* indica que al momento de compilar se enlace la biblioteca de C *math.h* mientras que la bandera *-o* sirve para indicar el nombre de archivo de salida.

Ejemplo de uso:


    mpicc recocido_mpi.c -o mpi

Con esta instruccion se indica al compilador de mpi que compile el programa recocido_mpi.c y el archivo para ejecutar se llame mpi.

**Ejecucion**

Para ejecutar el programa se utiliza la siguiente instruccion:

    mpiexec -n N ./mpi

En donde -n es una bandera para indicar el numero de procesos que se desea utilizar, N es el numero de procesos y mpi es el nombre indicado al momento de la compilacion.

Ejemplo de uso:

    mpiexec -n 4 ./mpi

con esta instruccion se indica que se utilicen 4 procesos y se ejecute el programa mpi.


**CUDA**

Para poder compilar y ejecutar el codigo **recocido_cuda.c** es necesario contar con una tarjeta grafica dedicada e instalar el compilador nvcc o en su defecto utilizar un servidor que cuente con tarjeta grafica dedicada. 

**Compilacion**

Teniendo acceso al compilador de cuda se compila utilizando la siguiente sintaxis:

    nvcc nombre_programa.c -o nombre_salida

En donde nvcc indica que se utilice el compilador de la tarjeta grafica dedicada, nombre_programa.c como se intuye, indica el nombre del programa a ejecutar y nombre_salida indica un alias para el archivo que se genera y se utilice para poder ejecutar. La bandera *-o* sirve para indicar el nombre de archivo de salida.

Ejemplo de uso:

    nvcc recocido_cuda.cu -o cuda

Con esta instruccion se indica al compilador de la tarjeta grafica que compile el programa recocido_cuda.cu y el archivo para ejecutar se llame cuda.

**Ejecucion**

Para ejecutar el programa se utiliza la siguiente instruccion:

    ./nombre_salida

En donde se indica el programa a ejecutar

Ejemplo de uso:

    ./cuda

con esta instruccion se indica que se ejecute el programa cuda.


## Notas sobre ejecucion y compilacion

Debido al equipo de computo requerido, al momento del desarollo de estos codigos se utilizo el servidor de la universidad para poder hacer uso del compilador mpicc y nvcc.
Esto influyo sobre todo en la compilacion y ejecucion del programa de MPI. Por ejemplo se utilizo la instruccion

    mpiexec -n N --hostfile lista_nodos.txt ./mpi

Para indicar adicionalmente un archivo que contenia la lista de nodos del servidor.