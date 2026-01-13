# Práctica 3.5 - Gestión de archivos

Realiza una captura de pantalla para cada uno de los ejercicios que lo requiera.

## Montaje de dispositivos

 1.	Indica a qué dispositivos de almacenamiento corresponden los siguientes archivos de dispositivo:

    -	/dev/sda3
    -	/dev/hda1
    -	/dev/scd2 
    -	/dev/sdb2

 2.	Supongamos que un ordenador tiene dos discos duros SATA y conectado un pendrive USB. Si conectáramos un segundo pendrive cuya etiqueta es DATOS:
    
    - ¿Qué dispositivo le corresponde? 
    - ¿En qué carpeta se montaría automáticamente? 

### Comando mount

 1.	Escribir el comando para montar la cuarta partición del segundo disco duro sata en el directorio /mnt/part4 en sistema de archivos NTFS, sólo lectura y sin posibilidad de ejecutar archivos binarios.
 2.	Teniendo en cuenta que tenemos un disco duro local tipo Sata, montar la primera partición del pendrive, teniendo en cuenta que el disco duro local es IDE, en el directorio /mnt/pen con sistema de archivos NTFS y las opciones por defecto. Desmontarlo posteriormente.

## Gestión de archivos y carpetas con CLI

Utiliza la siguiente estructura de carpetas para los ejercicios posteriores:

![Estructura de carpetas](assets/images/ud3/img01.png){ width="600"}

 1. Mirando la estructura anterior, supongamos que el archivo *fichero1.docx* se encuentra en cada una de las siguientes carpetas. Escribir la ruta absoluta del archivo y la ruta relativa de cada situación:

    - abiword:
        - Absoluta: 
        - Relativa: 
 
    - editores
        - Absoluta: 
        - Relativa: 
 
    - actividades
        - Absoluta:
        - Relativa: 
 
    - documentos
        - Absoluta: 
        - Relativa: 

### Comando find

1. Buscar desde /home/usuario sólo los ficheros que tengan como tamaño mínimo 5 Mb y su nombre comienza por una letra de a-z indistintamente si es mayúscula o minúscula.

2. Buscar desde el directorio /usr/share todos los directorios cuyo nombre contiene la cadena “ma” y copiarlos junto a sus subcarpetas en el directorio ~/actividades/editores.

3. Buscar desde el directorio ~/actividades los ficheros cuyo nombre acaba en txt y presentarlos por pantalla. Directorio activo ~/documentos.

4. Buscar desde el directorio /apuntes los ficheros cuyo tamaño es inferior a 1 Kb y su nombre comienza por un número para borrarlos pidiendo permiso uno a uno. Directorio activo ~.

### Comando gzip

1. Comprimir los archivos del directorio ~/apuntes y todo lo que contiene recursivamente. Directorio activo ~/documentos.

2. Comprimir los archivos del directorio ~/documentos/sistema_operativo cuyo nombre comienza por sec y contiene i18. Directorio activo ~/actividades/editores.

3. Comprimir, usando la máxima tasa de compresión, los archivos del directorio ~/documentos/procesador_de_texto cuyo nombre comienza por p y contiene un número. Directorio activo ~/documentos/sistema_operativo.

### Comando tar

1. Empaquetar y comprimir en el archivo ~/apuntes.tar.gz los archivos del directorio ~/apuntes.

2. Empaquetar SIN COMPRIMIR en el archivo ~/apuntes.tar los archivos del directorio ~/apuntes.

3. Empaquetar y comprimir en el archivo ~/documentos.tar.gz los archivos del directorio ~/documentos cuyo nombre empieza por número y contiene la cadena “doc”.Directorio activo ~.

4. Desempaquetar los archivos del paquete comprimido ~/apuntes/apuntes3.tar.gz. Directorio activo ~/documentos.

5. Desempaquetar los archivos del paquete NO comprimido ~/apuntes/apuntes3.tar. Directorio activo ~/documentos.

6. Muestra los archivos del paquete comprimido ~/apuntes/apuntes3.tar.gz. Directorio activo ~/documentos.

### Comando ln

1. Crear un enlace del archivo ~/actividades/UD1/ejer1.txt en el enlace ~/enlace_ejer1. El Directorio activo es ~/apuntes.

## Entrega

Crea un documento PDF, a partir de un Word o Google Docs, con las siguientes consideraciones:

- El nombre del archivo a entregar en la plataforma Moodle Centros debe tener el siguiente formato: `Apellido1Apellido2_Nombre_SOM_UD3_P5.pdf`.
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