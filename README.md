# Informe Taller de Programación I (75.42)

#	Trabajo Práctico N° 0: Contador de Palabras



## Nombre y Apellido: Federico Elías


## Padrón: 96105


## Fecha de Entrega: 05/10/2020

# Paso 0

**a. Capturas de pantalla de la ejecución, con y sin Valgrind.**

Se ejecutó el programa:

-Con Valgrind:

![conValgrind](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso0_conValgrind.png)

-Sin Valgrind:

![sinValgrind](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso0_sinValgrind.png)

**b. ¿Para qué sirve ​ Valgrind​ ? ¿Cuáles son sus opciones más comunes?**

Valgrind sirve para debuggear programas en linux, 
para encontrar tanto errores como pérdidas de memoria.
Estos problemas pueden ser: acceso indebido a una dirección de memoria,
usar valores sin inicializar previamente, liberar memoria dos veces,
escribir/leer en una dirección de memoria ya liberada, memory leaks

La herramienta por defecto de Valgrind es Memcheck, 
que permite detectar los errores mencionados anteriormente.
Las opciones más comunes de ésta herramienta son:

- leak-check=<no|summary|yes|full> [default: summary]: 
Opción que indica la cantidad de memory leaks. 
Si se elige el valor summary devuelve la cantidad de leaks,
y si elige 'yes' o 'full' devuelve un detalle sobre los mismos.

- log-file=<filename>: Opción que indica que el detalle de la ejecución 
de Valgrind va a escribirse en un archivo, siendo 'filename' 
el nombre del archivo. 
Si se deja vacío el valor filename la ejecución terminará en error.

- undef-value-errors=<yes|no> [default: yes]: Opción con la que se indica
verificar las variables no inicializadas si se el elige el valor default, 
ó no verifica ninguna variable si se elige 'no'.

**c. ¿Qué representa sizeof()​? ¿Cuál sería el valor de salida de sizeof(char)​ y sizeof(int)​?**

sizeof(): Devuelve el tamaño en bytes del parámetro de entrada.
El parámetro puede ser una variable definida o un tipo de dato.

 -sizeof(char): devuelve 1byte siempre

 -sizeof(int): Puede devolver 2bytes en máquinas de 16 bits,
	4bytes en máquinas de 32 bits o 8bytes en máquinas de 64 bits,
	depende del compilador y la arquitectura.

**d. ¿El sizeof()​ de una struct de C es igual a la suma del sizeof() de cada uno sus elementos? Justifique mediante un ejemplo.**

   No, el sizeof() de un struct en C devuelve como tamaño del struct el tamaño de la variable más grande multiplicada por la cantidad de elementos del struct. Esto es debido al padding que le agrega C a las demás variables, así evita problemas de alineamiento.

*Ejemplo:*

El código:

```c
struct estructura{
	char a; //Tamaño 1
	char b; //Tamaño 1
};

int main(){
	struct estructura est;
	printf("%ld\n", sizeof(struct estructura));
}
```
Devuelve 2

Mientras que el código:
```c	
struct estructura{
	int a; //Tamaño 4 en la máquina en que se lo ejecutó
	char b; //Tamaño 1
};

int main(){
	struct estructura est;
	printf("%ld\n", sizeof(struct estructura));
}
```
Devuelve 8

**e. Investigar la existencia de los archivos estándar: STDIN, STDOUT, STDERR. Explicar brevemente su uso y cómo redirigirlos en caso de ser necesario (caracteres >​ y < ) y como conectar la salida estándar de un proceso a la entrada estándar de otro con un pipe​ (carácter |).**

   STDIN STDOUT y STDERR son flujos de datos que conectan la entrada 
y la salida de un programa con la consola de comando cuanto éste se ejecuta.
   
  -STDIN: es un valor de entrada dado por el usuario,
si es que el programa lo solicita. Puede redirigirse con
el comando '<' seguido del nombre de un archivo, entonces
el contenido del input será el contenido del archivo indicado.

  -STDOUT es un valor de salida que la consola de comando provee al usuario.
Puede redirigirse con el comando '>' seguido del nombre de un archivo, 
para escribir su valor a dicho archivo, si el archivo no existe, se crea.

  -STDERR se usa para enviar mensajes de error al usuario cuando 
hay alguna falla en el programa que se ejecuta. También puede redirigirse
a un fichero de texto, con el comando '2>', para que la consola
lo diferencie del comando para redirigir el resultado de STDOUT.

# Paso 1

**a. Captura de pantalla mostrando los problemas de estilo detectados. Explicar cada uno.**

1. Siempre debe haber espacio entre un if/else/while 
y el paréntesis que realiza la comparación
![paso1_anElseShouldAppear](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_anElseShouldAppear.png)

2. Else y las llaves deben estar en la misma linea
![paso1_anElseShouldAppearMain](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_anElseShouldAppearMain.png)

3. No debe haber espacios entre el caracter ';' y el fin de línea de código
![paso1_extraSpace](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_extraSpace.png)

4. Else y las llaves deben estar en la misma linea
![paso1_ifAnElseHasBrace](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_ifAnElseHasBrace.png)

5. Else y las llaves deben estar en la misma linea
![paso1_ifAnElseHasBraceMain](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_ifAnElseHasBraceMain.png)

6. Siempre debe haber espacio entre un if/else/while 
y el paréntesis que realiza la comparación

![paso1_missingSpaceBefore](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_missingSpaceBefore.png)

7. Siempre debe haber espacio entre un if/else/while 
y el paréntesis que realiza la comparación
![paso1_missingSpaceInIf](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_missingSpaceInIf.png)

8. No debe haber espacios entre un paréntesis y la comparación
![paso1_missmatchingSpacesInside()](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_missmatchingSpacesInside().png)

9. No debe haber espacios entre un paréntesis y la comparación
![paso1_shouldHaveZeroInside](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_shouldHaveZeroInside.png)

10. Snprintf es más segura que strcpy porque establece un límite de copia
![paso1_snprintfThanStrcpy](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_snprintfThanStrcpy.png)

11. Toda línea de código y comentario debe ser de 80 caractereso menos
![comentarioMayorA80Caracteres](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_linesShouldBe<=80.png)

**b. Captura de pantalla indicando los errores de generación del ejecutable. Explicar cada uno e indicar si se trata de errores del compilador o del linker.**

  Errores de linkeo: errores que ocurren cuando el enlazador 
no puede resolver algún símbolo porque este no se encuentra
en ninguna de las librerías que se pretender vincular

 Errores del compilador: errores donde no se respetan las reglas del lenguaje.

Todos estos errores ocurren por no haber incluido el .h en el main.
Son todos errores del compilador.

![paso1_unknownTypeName](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_unknownTypeName.png)

![paso1_implicitDeclaration](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_implicitDeclaration.png)

![paso1_implicitDeclaration2](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_implicitDeclaration2.png)

![paso1_implicitDeclaration3](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_implicitDeclaration3.png)

![paso1_implicitDeclaration4](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso1_implicitDeclaration4.png)


**c. ¿El sistema reportó algún WARNING? ¿Por qué?**

El sistema reportó warnings pero, debido a los flags del compilador:
CFLAGS = -Wall -Werror -pedantic -pedantic-errors
estos fueron tratados como errores

# Paso 2

**a. Describa en breves palabras las correcciones realizadas respecto de la versión anterior.**

- Se corrigieron todos los errores de codificación indicados en el Paso 1.
- Se incluyó a paso2_wordscounter.h en main.c
- Se cambió strcpy por memcpy.

**b. Captura de pantalla indicando la correcta ejecución de verificación de normas de programación.**

![paso2_sinErroresCodificacion](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso2_sinErroresCodificacion.png)

**c. Captura de pantalla indicando los errores de generación del ejecutable. Explicar cada uno e indicar si se trata de errores del compilador o del linker**

Se invocó a la función malloc sin haber 
incluido ninguna librería que provee la misma:

![paso2c_malloc](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso2c_malloc.png)

No se incluye la biblioteca que permite usar datos 
de tipo size__t y FILE, sin embargo se declara una
función que devuelve un size_t y otra que tiene de
parámetro de entrada un FILE.

![paso2c_unknownTypeSize](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso2c_unknownTypeSize.png)

![paso2c_sizeNotIncluded](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso2c_sizeNotIncluded.png)

![paso2c_unknownTypeFile](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso2c_unknownTypeFile.png)

![paso2c_fileNotIncluded](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso2c_fileNotIncluded.png)

Debido a la falta de inclusión de bibliotecas,
ocurre el siguiente error:

![paso2c_conflictingTypes](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso2c_conflictingTypes.png)

Todos son errores de compilación.

# Paso 3

**a. Describa en breves palabras las correcciones realizadas respecto de la versión anterior.**

- Se incluyeron las librerías stdio.h y string.h, ambas contienen
el tipo de dato size_t y stdio.h contiene el tipo de dato FILE.

- Se incluyó la librería stdlib.h que contiene la función malloc.

**b. Captura de pantalla indicando los errores de generación del ejecutable. Explicar cada uno e indicar si se trata de errores del compilador o del linker**

La función wordscounter_destroy es declarada en el .h 
pero no fue implementada en el .c, este es un error de linker.

![paso3_destryNoImplementado](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso3_destryNoImplementado.png)

# Paso 4

**a. Describa en breves palabras las correcciones realizadas respecto de la versión anterior.**

- Se implementó la función wordscounter_destroy declarada en el .h

**b. Captura de pantalla del resultado de ejecución con Valgrind de la prueba ‘TDA’. Describir los errores reportados por Valgrind.**

El Valgrind reportó errores de pérdida memoria dinámica.
Acorde a la salida del Valgrind,
se alocaron 218 bloques de memoria,
sólo se llegaron a liberar 2 bloques, reservados por malloc,
uno de los bloques no liberados puede recuperarse, 
y los otros 215 están completamente perdidos.

![paso4_TDA](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso4_TDA.png)

**c. Captura de pantalla del resultado de ejecución con Valgrind de la prueba ‘Long Filename’. Describir los errores reportados por Valgrind.**

En este caso Valgrind detectó un error de buffer overflow,
error que causa que el programa deba terminar inmediatamente.

![paso4_nombreLargo](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso4_nombreLargo.png)

**d. ¿Podría solucionarse este error utilizando la función strncpy? ¿Qué hubiera ocurrido con la ejecución de la prueba?**

Strncpy no tiene en cuenta la longitud del destino donde copia el dato, por lo
tanto la ejecución de la prueba también terminaría en error de buffer overflow.

**e. Explicar de qué se trata un segmentation fault y un buffer overflow.**

- Buffer overflow es un error que ocurre cuando se quiere
copiar más datos en un buffer de los que éste dispone. Por ejemplo,
en la prueba de long filename, se quisieron copiar en la variable filepath,
que era un arreglo de tamaño treinta, más de treinta caracteres.

- Segmentation fault es el error que se obtiene al intentar ingresar
a una dirección de memoria de la que no se tiene autorización.

# Paso 5

**a. Describa en breves palabras las correcciones realizadas respecto de la versión anterior.**

- En paso5__wordscounter.c, en wordscounter_next_state se usó un const char*
en vez de un char* como tipo de dato para los caracteres limitadores,
de esta forma se evita usar la función malloc.

- En paso5__main.c se cambió la función memcpy por el 
nombre del archivo de entrada como STDIN, de esa forma
no es necesario tener en cuenta el límite de caracteres del nombre del archivo.

**b. Describa el motivo por el que fallan las prueba ‘Invalid File’ y ‘Single Word’. ¿Qué información entrega SERCOM para identificar el error? Realice una captura de pantalla.**

- 'Invalid File' falla debido a que se espera un 
código de error 1 y el que se obtiene es 255.
Esto se sabe observando el mensaje de error en el Sercom:

![paso5_archivoInvalido](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso5_archivoInvalido.png)

- 'Single Word' espera la cantidad de palabras dentro del archivo
input_single_word.txt, que es una sola, pero recibe 0.
Esto ocurre porque el archivo de entrada no tiene caracteres limitadores
de palabras y además paso5_wordscounter.c no tiene lógica para sumar la
cantidad de palabras cuando se llega al End Of File.
Entonces cuando la variable next__state tenga valor STATE_IN_WORD,
el booleano **if (strchr(delim_words, c) != NULL)** nunca devuelve true,
 y así la cantidad de palabras quedará en 0.

![paso5c_unaPalabra](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso5c_unaPalabra.png)

**c. Captura de pantalla de la ejecución del comando hexdump. ¿Cuál es el último carácter del archivo input_single_word.txt?**

![paso5c_singleWordHex](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso5c_singleWordHex.png)

El último caracter es 'd', no se observan caracteres limitadores

**d. Captura de pantalla con el resultado de la ejecución con gdb. Explique brevemente los comandos utilizados en gdb. ¿Por qué motivo el debugger no se detuvo en el breakpoint de la línea 45: self->words++; ?**


![paso5d_gdbParte1](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso5d_gdbParte1.png)
![paso5d_gdbParte2](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso5d_gdbParte2.png)

- Comandos de GDB usados:
	- info functions: Da un listado de las funciones
	implementadas en cada .c del ejecutable.
	- list wordscounter_next_state: Muestra las líneas de 
	código desde una línea antes del llamado a la función wordscounter_next_state
	- list: Muestra las líneas subsecuentes a las 
	líneas mostradas con el anterior llamado.
	- break 45: Hace que la ejecución del programa corte en la línea 45
	- run input_single_word.txt: Corre el programa usando 
	el archivo de entrada input_single_word.txt
	- quit: Termina el proceso

- El programa no se detuvo porque, debido a lo 
visto en el punto c. el programa no pasó por esa línea

# Paso 6

**a. Describa en breves palabras las correcciones realizadas respecto de la versión anterior.**

 Se corrigió la lógica de la función wordscounter_next_state para evitar
el error del Paso 5, ahora la nueva lógica suma 1 palabra si se llega a EOF.

**b. Captura de pantalla mostrando todas las entregas realizadas​, tanto exitosas como fallidas.**

![paso6_submissionHistory1](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso6_submissionHistory1.png)
![paso6_submissionHistory1](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso6_submissionHistory2.png)

**c. Captura de pantalla mostrando la ejecución de la prueba ‘Single Word’ de forma local​ con las distintas variantes indicadas.**

![paso6_pruebaLocal](https://github.com/nazar9318/nazar9318-taller1-2c2020-TP0/blob/master/assets/paso6_pruebaLocal.png)
