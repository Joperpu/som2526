# Práctica 3.3 - Comandos de gestión de archivos I

## Ejercicios

Haz una captura de pantalla para cada uno de los ejercicios.

### Ejercicios usando el comando *ls*

1.	Listar todos los archivos cuya extensión es “.gz” de la carpeta /usr/share/doc/alsa-base/driver

2.	Listar todos los archivos que comienzan por “S” y contienen el número “2” del directorio /etc/rc2.d

3.	Listar todos los archivos que comienzan por “l” y contienen “menu” del directorio /usr/share/doc

4.	Listar los archivos del directorio /usr/share/doc/ cuyo nombre comienza por la letra “a” o la letra “c” y contengan la palabra “icon”. Que aparezcan en formato extendido y sin subdirectorios.

5.	Listar los archivos del directorio /usr/share/doc/alsa-base/driver cuyo nombre contiene un número y tienen extensión .txt

6.	Listar los archivos del directorio /usr/share/doc/apt/examples cuyo nombre comienza por letra consonante

7.	Listar los archivos del directorio /var/log cuyo nombre NO contiene un número y tienen extensión “.log”

8.	Listar en formato largo “-l” los archivos del directorio /var/log

9.	Listar todo el contenido de la carpeta y sus subcarpetas del directorio /usr/share/doc/alsa-base en formato ancho incluyendo los archivos ocultos.

10.	Listar todo el contenido del directorio /etc

11.	Listar los archivos y carpetas (recursivamente) del directorio /etc cuyo nombre comienza por “a”

12.	Listar los archivos en formato largo del directorio /etc cuyo nombre comienza por “rc” seguido de un número y acabado en “d”

13.	Listar en formato largo (-l) los archivos del directorio “/usr/share/doc/apt/examples” cuyo nombre comienza por vocal y acaba en consonante.

14.	Listar en formato largo los archivos del directorio “/etc/rc6.d” cuyo nombre comienza por “K” seguida de dos números

### Ejercicios usando el comando *cp*

1.	Copiar los archivos del directorio /usr/share/doc/alsa-base/driver cuyo nombre contiene un número en el directorio “~/Documentos”

2.	Copiar el archivo “/etc/network/interfaces” en la carpeta “~/actividades/hoja_calculo” con el nombre “red.conf”

3.	Copiar el directorio y subdirectorios (recursivamente) /usr/share/doc/alsa-base/driver en ~/apuntes

4.	Copiar todos los archivos y subdirectorios de la carpeta “/etc/network” en “~/apuntes/t3”

### Ejercicios usando el comando *mv*

1.	Mover el archivo ~/apuntes/t3/network/interfaces ~/actividades/editores/abiword

2.	Mover el archivo ~/actividades/editores/abiword/interfaces a la carpeta ~/Documentos/sistema_operativo y ponerle de nombre “tarjetas_red”

3.	Cambiar el nombre del archivo ~/Documentos/sistema_operativo/tarjetas_red por interfaces_de_red

4.	Mover todos los archivos cuyo nombre comienza por “r” y acaba en “f” del directorio “~/actividades/hoja_calculo” al directorio  “~/Documentos/sistema_operativo”. Directorio activo de trabajo "~/apuntes/t3"

5.	Mover y cambiar el nombre del archivo “~/Documentos/sistema_operativo/glibc2.m4” a “~/apuntes/t5/libreria.m4”. Directorio activo de trabajo "~/actividades/editores".

6.	Mover la carpeta “~/apuntes/t3” a la carpeta “~/apuntes/t6”. Desde el directorio activo "~".

7.	Mover el archivo “~/Documentos/sistema_operativo/red.conf” a la carpeta “~/apuntes/t6” y cambiarle el nombre por “nat_movido”. Directorio activo de trabajo "/etc"


### Ejercicios usando el comando *rm*

*En algunos casos deberás usar el comando find junto a rm*

1.	Borrar el archivo “interfaces_de_red” de la carpeta “~/Documentos/sistema_operativo”

2.	Borrar los archivos de la carpeta y subcarpetas “apuntes” que comienzan por “vocal” o la letra “d”. 

3.	Borrar los archivos y subcarpetas de la carpeta “~/Documentos” con extensión “.txt”

4.	Borrar todos los archivos y subcarpetas de “~/apuntes” que comienzan por “t” y acaban en un número. 
Debes moverte antes al directorio activo “~/actividades/hoja_calculo”.

5.	Borrar los archivos de la carpeta “~/Documentos/sistema_operativo” cuyo nombre contiene la cadena “text”. Directorio activo “~/apuntes”.

6.	Borrar todos los archivos y subcarpetas de la carpeta “~/apuntes” que comienzan por “t” y acaban en un número seguido de otro carácter. Directorio activo “~/actividades/hoja_calculo”.


### Ejercicios usando el comando *cat*

1.	Mostrar el contenido del archivo “/etc/passwd”

2.	Mostrar todos los archivos con extensión “.txt” de la carpeta “~/apuntes”


### Ejercicios usando el comando *find*

1.	Buscar desde el directorio personal los archivos que comienzan por vocal y tienen extensión “.gz”, y mostrarlos por pantalla

2.	Buscar desde el directorio “/usr/share/doc/apt” todos los archivos cuyo nombre contiene la cadena “READ” y mostrarlos por pantalla

3.	Buscar todos los archivos comprimidos con “.gz” que hay a partir de “/usr/share/doc”

4.	Buscar todos los archivos de texto de “/usr” con un tamaño mínimo de 10 KB.

5.	Buscar todos los archivos de la carpeta /usr cuyo nombre comienza por letra mayúscula y están comprimidos con “gz”. 

6.	Buscar desde el directorio “/usr/share” todos los archivos y directorios cuyo nombre contiene la cadena “ma” y copiarlos en el directorio “~/actividades/editores”

7.	Buscar todos los archivos comprimidos (.gz) que hay a partir de la carpeta “/usr/share/doc”

8.	Buscar desde el directorio personal todas las carpetas cuyo nombre comienza por una letra y contiene un número entre 1 y 5. 

9.	Buscar todos los archivos, y solo los archivos, del directorio “/etc” que comienzan por “if”. Directorio activo “/usr/share”.

## Entrega

Crea un documento PDF, a partir de un Word o Google Docs, con las siguientes consideraciones:

- El nombre del archivo a entregar en la plataforma Moodle Centros debe tener el siguiente formato: `Apellido1Apellido2_Nombre_SOM_UD3_P3.pdf`.
- Portada con imagen, nombre del alumno, título y curso.
- Encabezado con nombre de la práctica y materia.
- Pie de página con nombre, número de página insertado, curso, año escolar, instituto.
- Índice o tabla de contenidos generada automáticamente.
- Tipo de letra: Times New Roman 12 o similar, interlineado sencillo, espaciado anterior 6p.
- Uso correcto de la ortografía.
- Texto justificado con uso de salto de páginas correcto.
- Enlaces web de referencia cuando se coge información de un sitio web.
- Las fotos que se puedan ver correctamente al ampliarlas y que no ocupen mucho espacio.
- Insertar Título de foto que haga referencia al apartado y ejercicio correspondiente.
- Para las capturas de pantalla de las máquinas virtuales:
    - Se captura todo el escritorio de la máquina virtual donde se pueda leer el nombre de la máquina, con el fondo de su plataforma Moodle, donde se pueda ver imagen de perfil. Toda aquella práctica que no cumpla este requisito no será evaluada.
    - Al igual que en los Títulos de las fotos, en el Título de la captura de pantalla irá referenciado el apartado y ejercicio al que corresponde.