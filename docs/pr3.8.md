# Práctica 3.8 - Gestión de discos, procesos y tareas programadas

## Descripción de la tarea

Realiza una captura de pantalla para cada uno de los ejercicios que lo requiera.

Antes de empezar ejecuta este bloque de comandos:

```bash
mkdir -p ~/labdisk/{docs,logs,datos/{img,raw}}
fallocate -l 1M ~/labdisk/docs/a.txt
fallocate -l 2M ~/labdisk/logs/app.log
fallocate -l 3M ~/labdisk/datos/img/foto.bin
fallocate -l 5M ~/labdisk/datos/raw/dump.bin
```

## Ejercicios

1. Identifica todos los discos y particiones presentes en el sistema y redacta un informe con: dispositivo, tipo/ID de partición, tamaño y punto de montaje si existiera.

2. Obtén un listado de particiones usando una herramienta distinta a la del ejercicio anterior.

3. Anota el tamaño en bloques de una partición concreta del disco principal.

4. En otra máquina virtual Lubuntu, crea una nueva partición y establece sobre ella un sistema de archivos de la familia ext con tamaño de bloque 4096.

5. En otra máquina virtual Lubuntu crea un sistema de archivos FAT de 32 bits etiquetado con el nombre PRACTICA.

6. Monta ambos sistemas de archivos creados en dos puntos de montaje dentro de /mnt. Crea un archivo de texto en cada uno con una línea identificativa y desmonta.

7. Simula un chequeo y reparación automática del sistema de archivos ext de pruebas (sin montarlo).

8. Calcula el tamaño total de labdisk, el tamaño de cada subcarpeta inmediata y el total acumulado.

9. Determina el uso de espacio libre/ocupado de los sistemas de archivos montados en formato “humano”. Después, limita la vista a un tipo concreto (por ejemplo, solo ext).

10. Localiza los tres subdirectorios más pesados dentro de ~/labdisk (en cualquier profundidad) y anótalos ordenados de mayor a menor con su tamaño aproximado.

11. Muestra el conjunto de procesos en ejecución con formato “completo”. Extrae a un archivo los campos: PID, PID del padre, usuario, estado, %CPU, %MEM, tiempo y comando.

12. Obtén un listado de todos los procesos ordenado por uso de CPU de mayor a menor y limita la salida a los 10 más activos.

13. Genera una vista en forma de árbol del conjunto de procesos incluyendo comando y PID.

14. Lanza dos procesos de larga duración (del orden de varios minutos) para pruebas.

15. Envía a uno de los procesos de prueba una señal de finalización “suave” y verifica que termina.

16. Finaliza todas las instancias restantes del segundo proceso de prueba indicando el nombre del programa en lugar de sus PIDs.

17. Abre una sesión de monitorización interactiva del sistema y:
    - Cambia el orden a “memoria”.
    - Muestra el uso por CPU individual.
    - Filtra por tu usuario.

18. Programa un reinicio dentro de 10 minutos con un mensaje informativo para usuarios conectados y, a continuación, cancélalo.

19. Especifica el comando exacto que realizaría un apagado inmediato del sistema.

20. Crea un pequeño script en ~/labdisk que añada la fecha actual a ~/labdisk/logs/at.log. Dale permisos de ejecución.

21. Programa la ejecución del script anterior dentro de 2 minutos y comprueba posteriormente que el registro se ha añadido.

22. Programa otra ejecución del mismo script para dentro de 10 minutos y elimínala antes de que ocurra.

23. Abre tu planificador periódico de usuario y establece que la shell por defecto sea /bin/bash para las tareas programadas.

24. Añade una tarea diaria a las 02:15 que escriba una línea con fecha en ~/labdisk/logs/cron.log.

25. Añade una tarea que se ejecute al arrancar el sistema y otra que se ejecute cada hora.

26. Programa una tarea periódica que se ejecute los lunes y jueves a las 03:10 y otra que se ejecute cada 15 minutos.

27. Elimina todas tus tareas periódicas de usuario y verifica que el planificador queda vacío.

## Entrega

Crea un documento PDF, a partir de un Word o Google Docs, con las siguientes consideraciones:

- El nombre del archivo a entregar en la plataforma Moodle Centros debe tener el siguiente formato: `Apellido1Apellido2_Nombre_SOM_UD3_P8.pdf`.
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