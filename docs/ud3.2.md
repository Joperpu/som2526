# Unidad 3 - Gestión de archivos en Lubuntu

## Introducción al almacenamiento en GNU/Linux (Lubuntu)

En Lubuntu el sistema de archivos por defecto es ext4, que organiza y guarda la información del sistema. Además, el sistema reconoce y puede usar otros formatos como FAT32, exFAT y NTFS, tanto en particiones internas como en dispositivos extraíbles.

Linux presenta todo el almacenamiento como un único árbol que cuelga de la raíz ``/``. No se asignan letras de unidad como en Windows; en su lugar, cada dispositivo o partición se monta en algún directorio del árbol, de modo que toda la información es accesible desde la misma jerarquía.

ext4 es un sistema de archivos con journaling (transaccional). Esto significa que mantiene consistente la estructura del sistema de archivos (directorios, inodos, metadatos) ante apagados inesperados o fallos, reduciendo comprobaciones largas al reiniciar. El contenido de los archivos puede necesitar recuperación adicional según el caso, pero la estructura queda protegida.

Los elementos básicos son directorios (carpetas) y archivos; con ellos se almacena, organiza y recupera la información.

### Estructura

En GNU/Linux los archivos se organizan en directorios formando una jerarquía que comienza en / (raíz). Los datos pueden residir en distintos dispositivos, pero antes de acceder a ellos es necesario montarlos (asociarlos a un directorio). Conceptos clave:

- Los nombres distinguen mayúsculas y minúsculas.
- La raíz se referencia como /.
- En los nombres no puede usarse la barra /.
- Un archivo/directorio se identifica por su ruta absoluta (desde /), con / como separador: por ejemplo, /usr/share/keymaps/us.map.gz.
- La longitud máxima de un nombre (sin contar la ruta) suele ser 255 caracteres.
- En cada directorio existen dos entradas especiales: . (el propio directorio) y .. (el padre). En /, .. referencia a la propia raíz.
- No hay un árbol por cada dispositivo: todo cuelga de /. Cada dispositivo se monta en un punto de montaje accesible desde la jerarquía.

Durante la instalación se crea la estructura básica. Algunos directorios habituales:

- ``/`` Raíz del sistema.
- ``/bin`` Comandos esenciales para todos los usuarios.
- ``/boot`` Archivos del cargador de arranque.
- ``/dev`` Archivos de dispositivo.
- ``/etc`` Configuración específica del sistema.
- ``/lib`` Bibliotecas compartidas esenciales (y en sistemas de 64-bit, también /lib64).
- ``/mnt`` Puntos de montaje temporales.
- ``/media`` Montaje automático de medios extraíbles (p. ej., /media/usuario/USB).
- ``/proc`` Interfaz al kernel en tiempo real (pseudo-FS).
- ``/sbin`` Comandos de administración del sistema.
- ``/tmp`` Archivos temporales (se limpian al arrancar en sistemas bien configurados).
- ``/usr`` Programas y datos de solo lectura a nivel de sistema.
- ``/var`` Datos variables (logs, colas, cachés, correo…).
- ``/home`` Directorios personales de los usuarios.
- ``/root`` Directorio personal del superusuario.
- ``/run`` Datos de estado en tiempo de ejecución (tmpfs).

Algunos detalles prácticos:

- /tmp y /var pueden ir en particiones separadas por seguridad y para evitar que un crecimiento inesperado afecte al resto del sistema.
- /home en una partición propia facilita copias de seguridad y permite reinstalar o cambiar de distribución manteniendo datos y configuraciones de usuario.

Sobre las rutas:

- Ruta absoluta: desde la raíz hasta el objetivo. Ej.: /home/usuario/documentos/informe.odt.
- Ruta relativa: desde el directorio actual. Si estás en /home/usuario, puedes referirte a lo anterior como documentos/informe.odt.

En Linux/Unix “todo es un archivo”: además de los archivos de datos, también lo son muchos dispositivos e interfaces del sistema, lo que unifica el acceso y la administración dentro de la misma jerarquía.

### Extensiones en los nombres de archivo

En GNU/Linux (Lubuntu) las extensiones no son obligatorias ni determinan el tipo real del archivo. El sistema y el escritorio (PCManFM-Qt) usan principalmente la detección por contenido (tipo MIME) y permisos, no la extensión. Aun así, usar extensiones es una buena práctica porque facilita la asociación con aplicaciones y la identificación visual.

A diferencia del antiguo esquema “8.3” de MS-DOS (o la dependencia fuerte de extensiones en Windows), en Linux:

- Un nombre puede contener varios puntos (.tar.gz, .config.backup) y cualquier longitud razonable.
- Los nombres distinguen mayúsculas/minúsculas (foto.PNG y foto.png pueden ser distintos).
- Los archivos ocultos empiezan por . (p. ej., .bashrc).
- La ejecución no depende de una extensión .exe: importa el permiso de ejecución y, en scripts, la línea shebang (#!/bin/bash, #!/usr/bin/env python3).

Extensiones habituales (orientativas, no limitativas):

- txt (texto plano), pdf (documento), odt/ods/odp (LibreOffice), docx (Word)
- jpg/png/gif/webp (imagen), mp3/flac/mp4/mkv (audio/vídeo)
- zip/7z/tar.gz/tar.xz (comprimidos/archivos)
- deb (paquete Debian/Ubuntu), AppImage (aplicación portable), iso (imagen de disco)

## Montaje de dispositivos de almacenamiento

En Lubuntu los datos residen en dispositivos de bloque (discos, particiones, USB, CD/DVD…) representados por ficheros en /dev. Para poder acceder a su contenido deben montarse: esto asocia el dispositivo con un directorio del árbol (punto de montaje).
Al conectar un pendrive o introducir un CD/DVD, el sistema (udisks2 + PCManFM-Qt) suele montarlos automáticamente bajo /media/<usuario>/… usando la etiqueta o el UUID. Desde ese momento el contenido es accesible como si fuera una carpeta más.
Al terminar, hay que desmontar el dispositivo: en la interfaz gráfica, usa “Expulsar/Quitar de forma segura”; en terminal, umount o udisksctl unmount. Tras desmontar, el punto de montaje bajo /media/<usuario> puede eliminarse automáticamente.

Identificación de dispositivos

Hoy en día la mayoría de discos SATA/SCSI/USB aparecen como /dev/sdX (X = a, b, c…). Las particiones se numeran: /dev/sda1, /dev/sda2, etc. Los discos NVMe se nombran como /dev/nvme0n1 y sus particiones /dev/nvme0n1p1, p2…. Las memorias eMMC/SD pueden verse como /dev/mmcblk0p1. Las unidades ópticas suelen ser /dev/sr0.
Los antiguos nombres IDE tipo /dev/hd[a-d] son legado y no se usan en sistemas actuales.

Herramientas útiles para saber “qué es qué”:

Listar discos y puntos de montaje:

```bash
lsblk
```
Ver UUID/etiquetas y tipo de FS:

```bash
blkid
```

Tabla de particiones (modo lectura):

```bash
sudo fdisk -l /dev/sda
```

Enlaces por nombre, UUID o etiqueta:

```bash
ls -l /dev/disk/by-uuid/
ls -l /dev/disk/by-label/
```

Montaje y desmontaje manual:

```bash
sudo mkdir -p /mnt/usb
sudo mount /dev/sdb1 /mnt/usb            # montar
sudo umount /mnt/usb                     # desmontar por ruta (o: sudo umount /dev/sdb1)
```

Con udisks2 (integra mejor con el escritorio):

```bash
udisksctl mount -b /dev/sdb1
udisksctl unmount -b /dev/sdb1
udisksctl power-off -b /dev/sdb           # apaga el dispositivo (seguro para retirar)
```

### Montaje y desmontaje con la GUI

En Lubuntu, el montaje de dispositivos externos es sencillo y está orientado al usuario. Al conectar un USB o introducir un CD/DVD, el sistema (udisks2) los detecta y monta automáticamente; el contenido aparece en el panel lateral del gestor de archivos PCManFM-Qt bajo /media/<usuario>/<Etiqueta>.

#### Unidades ópticas

Al introducir un CD o DVD, se muestra un nuevo elemento en el panel lateral con el título del disco. Al hacer clic, se abre su contenido en PCManFM-Qt.
Las unidades ópticas son normalmente solo lectura: podrás copiar archivos desde el disco, pero no borrarlos ni moverlos en el propio medio.

Para expulsar el disco, haz clic derecho sobre su entrada en el panel lateral y elige Expulsar.

### Memorias flash

Al conectar un pendrive o disco USB, Lubuntu lo monta y abre su contenido directamente en PCManFM-Qt. Desde ese momento puedes gestionar archivos como en cualquier otra carpeta del sistema.

Para retirar el dispositivo con seguridad:
1. Clic derecho sobre su entrada en el panel lateral.
2. Selecciona Quitar de forma segura (o Desmontar/Expulsar, según el caso).
3. Si hay archivos en la papelera del dispositivo, el sistema puede preguntar si deseas vaciarla.

Consejo: espera a que finalicen las copias antes de retirar el USB. Usar “Quitar de forma segura” evita corrupción de datos.

## Montaje y desmontaje en CLI. Comandos mount y umount

En tareas administrativas sin GUI, a menudo hay que montar manualmente. Para ello se usa mount; para liberar el punto de montaje, umount.

Sintaxis básica

```bash
sudo mount [opciones] dispositivo directorio
sudo umount dispositivo|directorio
```

Argumentos

- dispositivo: archivo de dispositivo (p. ej., /dev/sdb1, /dev/nvme0n1p3).
- directorio: punto de montaje (p. ej., /mnt/usb).

Opciones comunes

- -t <sistema_de_archivos>: especifica el tipo. Ejemplos habituales:
- ext4 (Linux), xfs, btrfs
- vfat (FAT32), exfat (exFAT)
- ntfs (soporte lectura/escritura con el driver ntfs3 en kernels actuales)
- -o <opciones>: lista separada por comas (sin espacios) con opciones de montaje.
- --bind olddir newdir: vuelve a montar un directorio en otro punto del árbol.
- --move olddir newdir: mueve un montaje de un directorio a otro.

Nota: hoy el kernel usa por defecto relatime (actualiza tiempos de acceso de forma diferida). Las opciones atime/noatime ajustan ese comportamiento.

Opciones de montaje (selección)

Se indican con -o y se separan por comas; algunas son excluyentes:

- atime / noatime
Actualiza / no actualiza el tiempo de acceso. noatime reduce escrituras y puede mejorar rendimiento.
- exec / noexec
Permite / prohíbe ejecutar binarios desde el montaje.
- ro / rw
Montaje en solo lectura o lectura/escritura.
- remount
Reaplica opciones sobre un montaje ya existente.
- uid=<n> / gid=<n>
Fija propietario/grupo del punto de montaje (útil en vfat/exfat/ntfs, que no guardan permisos POSIX).

Ejemplos:

```bash
# Montar un pendrive FAT32 en /mnt/usb
sudo mkdir -p /mnt/usb
sudo mount -t vfat -o uid=$(id -u),gid=$(id -g),umask=022 /dev/sdb1 /mnt/usb

# Montar NTFS con lectura/escritura (driver ntfs3)
sudo mount -t ntfs -o rw /dev/sdb2 /mnt/ntfs

# Cambiar opciones sin desmontar (remount en solo lectura)
sudo mount -o remount,ro /mnt/usb

# Desmontar por ruta o dispositivo
sudo umount /mnt/usb
# o
sudo umount /dev/sdb1
```

## Gestión de archivos y directorios en CLI

En Lubuntu trabajarás a menudo en terminal con rutas y nombres de archivos. Dos ideas clave:
- El directorio activo (o de trabajo) es donde te encuentras al ejecutar un comando (pwd lo muestra).
- Cada usuario tiene su carpeta personal (HOME), normalmente /home/<usuario>. En terminal, al iniciar sesión, el directorio activo suele ser el HOME. El símbolo ~ es un atajo de esa carpeta.

Los comandos aceptan rutas absolutas o relativas:

- Absoluta: empieza en la raíz / y recorre toda la jerarquía, ej.: /home/usuario/trabajos/oficina/memoria.odt
- Relativa: parte del directorio activo.
- . representa el directorio actual (a menudo se omite).
- .. representa el directorio padre.

Ejemplos (suponiendo que estás en /home/usuario):

- Ruta relativa hacia un archivo más profundo:
./trabajos/oficina/memoria.odt  → normalmente se escribe trabajos/oficina/memoria.odt
- Si el activo es /home/usuario/trabajos, el mismo archivo sería:
oficina/memoria.odt
- Si el activo es el propio directorio de la oficina, puedes referirte a él como:
./memoria.odt o simplemente memoria.odt
- Para subir en la jerarquía: desde /home/usuario/trabajos/oficina/apuntes, el archivo del padre se indica como:
../trabajo.odt
- Para un salto mayor (subir varios niveles y cambiar de rama):
../../../informe.odt llega a /home/usuario/informe.odt
y, si necesitas ir a la carpeta de otro usuario desde /home/usuario/trabajos:
../../ajimenez/documentos/manual.txt

En general, da igual usar ruta absoluta o relativa: elige la que sea más clara y corta desde tu ubicación actual.

### Metacaracteres en los nombres de archivo

Para operar sobre conjuntos de archivos sin listarlos uno a uno, la shell expande patrones (globbing) antes de ejecutar el comando. Los comodines más comunes son:

- \*  → coincide con cero o más caracteres.
    - *.log coincide con app.log, errores.log, etc.
- ?  → coincide con un solo carácter.
    - img_?.png coincide con img_1.png, no con img_10.png.
- [ ... ]  → clase de caracteres; uno de los listados.
    - foto_[abc].jpg coincide con foto_a.jpg, foto_b.jpg, foto_c.jpg.
    - [a-z]  → rango de caracteres.
    - capitulo_[0-9].txt para un dígito.
    - [! ... ]  → negación: cualquier carácter no listado.
    - archivo_[!a]* excluye los que empiezan por a tras el guion bajo.

Recuerda que en GNU/Linux los nombres distinguen mayúsculas y minúsculas: foto.PNG y foto.png pueden ser distintos. Si el nombre contiene espacios o caracteres especiales, cítalo ("Mi archivo.txt") para que la shell no lo fragmente.

### Crear directorios: mkdir

El comando mkdir crea directorios y, opcionalmente, su estructura de padres.

Sintaxis

```bash
mkdir [opciones] directorio ...
```

Parámetros

- directorio ...  Lista de directorios (separados por espacios) a crear.

Opciones

- -p, --parents  Crea también los directorios padre que falten e ignora los que ya existan.

Ejemplos

```bash
mkdir proyectos               # Crea un directorio
mkdir doc notas               # Crea varios a la vez
mkdir -p curso/ud1/apuntes    # Crea la ruta completa si no existe
```

### Cambiar el directorio activo: cd

El comando cd cambia el directorio de trabajo actual.

Sintaxis

```bash
cd [directorio]
```

Parámetros

- directorio  Destino al que moverse. Si se omite, se cambia al HOME del usuario.

Ejemplos

```bash
cd                 # Va a tu HOME (~/)
cd /etc            # Ruta absoluta
cd trabajos/ud1    # Ruta relativa
cd ..              # Sube al directorio padre
cd -               # Vuelve al directorio anterior
```

### Eliminar directorios: rmdir

El comando rmdir elimina directorios vacíos. Si el directorio contiene archivos o subdirectorios, mostrará un error.

Sintaxis

```bash
rmdir [opciones] directorio ...
```

Parámetros

- directorio ...  Lista de directorios (separados por espacios) a eliminar.

Opciones

- -p, --parents  Elimina el subárbol de directorios vacíos: borra el indicado y, si quedan vacíos, sus antecesores.

Ejemplos

```bash
rmdir tmp                 # Solo si 'tmp' está vacío
rmdir -p curso/ud1/ap     # Borra 'ap', luego 'ud1' y luego 'curso' si todos están vacíos
```

### Listar el contenido de un directorio: ls

ls muestra el contenido de archivos y directorios. Puedes listar varios destinos a la vez.

Sintaxis

```bash
ls [opciones] [archivos ...]
```

Parámetros

- archivos ...  Rutas a listar (opcionales). Si se omiten, lista el directorio actual.

Opciones habituales

- -l  Formato largo: tipo y permisos, enlaces, propietario, grupo, tamaño, fecha de modificación y nombre.
- -t  Ordena por fecha (descendente).
- -S  Ordena por tamaño (descendente).
- -X  Ordena por extensión (sufijo tras el último punto).
- -r  Invierte el orden de la opción de ordenación usada (-t, -S, -X, …).
- -R  Recursivo: lista el contenido de los subdirectorios.
- -a  Incluye archivos ocultos (nombres que empiezan por .).
- -d  Lista el directorio en sí en lugar de su contenido (útil con -l).

Ejemplos

```bash
ls -l                     # Listado detallado del directorio actual
ls -la                    # Incluye ocultos
ls -lt                    # Ordenado por fecha (reciente primero)
ls -lrth                  # (útil) largo + inverso + tiempos + tamaño "humano"*
ls -R /etc                # Recursivo
ls -d */                  # Lista solo subdirectorios del actual
ls -X                     # Ordenado por extensión
```

### Copiar archivos y directorios: cp

El comando cp crea copias de archivos (y, si se indica, de directorios).

Sintaxis

```bash
cp [opciones] archivos_origen ... destino
```

Parámetros

- archivos_origen ...  Uno o varios archivos (se admiten comodines).
- destino
- Si es un directorio existente, copia cada origen dentro de él conservando su nombre.
- Si no existe y solo hay un origen, crea un único archivo con el nombre dado.
- Si hay varios orígenes y el destino no es un directorio existente, dará error.

Opciones útiles

- -i  Pregunta antes de sobrescribir (por defecto, sobrescribe sin preguntar).
- -r, -R  Copia recursivamente directorios y su contenido.
- --parents  Preserva la ruta creando los directorios que falten en el destino.
- -p  Preserva atributos (marca de tiempo, permisos, propietario, grupo).
- -u  Solo copia si el origen es más reciente o no existe en el destino.
- -v  Modo verboroso (muestra qué va copiando).
- (nota) -a “archive” equivale a una copia recursiva preservando enlaces/atributos: muy práctico para clonar árboles (-a ≈ -dR --preserve=all).

En sistemas de archivos sin permisos POSIX (FAT/exFAT/NTFS montados sin mapeo), -p puede no conservarlos tal cual.

Ejemplos

```bash
cp informe.odt informe_copia.odt                 # Copia simple
cp *.png /home/usuario/imagenes/                 # Varios archivos a un directorio
cp -R proyecto/ /mnt/usb/                        # Copia recursiva de un directorio
cp -a sitio_web/ /backup/                        # Clonado preservando todo (recomendado)
cp --parents src/utils/script.sh /tmp/paquete/   # Crea /tmp/paquete/src/utils/script.sh
cp -u datos.db /backup/datos.db                  # Solo si el origen es más nuevo
```

### Mover archivos y directorios: mv

mv mueve archivos/directorios a otra ubicación o renombra si el destino no es un directorio.

Sintaxis

```bash
mv [opciones] archivos_origen ... destino
```

Parámetros

- archivos_origen ...  Uno o varios orígenes (se admiten comodines).
- destino
- Si es un directorio existente, mueve allí todos los orígenes.
- Si no es un directorio existente, renombra el único origen indicado.

Opciones útiles

- -f  No pregunta al sobrescribir (comportamiento forzado).
- -i  Pregunta antes de sobrescribir (seguro).
- -n  No sobrescribe nunca (no-clobber).
- -u  Solo mueve si el origen es más reciente o no existe en el destino.
- -v  Modo verboroso.

Ejemplos

```bash
mv borrador.txt final.txt                        # Renombrar
mv *.jpg /home/usuario/fotos/                    # Mover varios archivos a un directorio
mv -i reporte.pdf /mnt/usb/                      # Pregunta si hay un reporte.pdf allí
mv proyecto proyecto_old                         # Renombrar un directorio
```

### Eliminar archivos y directorios: rm

El comando rm borra archivos y (si se indica) directorios.

Sintaxis

```bash
rm [opciones] archivo ...
```

Parámetros

- archivo ...  Lista de archivos/directorios a eliminar (admite comodines).

Opciones principales

- -r, -R  Borrado recursivo (necesario para eliminar directorios con contenido).
- -f        Forzar: no pide confirmación y omite errores (cuidado).

Opciones útiles (recomendadas):

- -i  pide confirmación antes de borrar cada entrada.
- -v  modo “verboroso”, muestra lo que va borrando.

Ejemplos

```bash
rm notas.txt                         # Borra un archivo
rm -i informe.pdf                    # Pide confirmación
rm -r documentos                     # Borra un directorio y su contenido
rm -rf build/                        # Forzado y recursivo (peligroso)
rm -- -nombre-raro.txt               # Borra un archivo que empieza por '-'
```

Precaución: rm elimina de forma definitiva (no va a la papelera). Revisa la ruta y los comodines antes de ejecutar, especialmente con -f y -r.

### Mostrar el contenido de archivos de texto: cat, more (y less)

#### cat

Muestra por pantalla (STDOUT) el contenido de uno o varios archivos y también sirve para concatenar.

Sintaxis

```bash
cat archivo ...
```

Si pasas varios archivos, cat imprime uno tras otro. Útil con tuberías:

```bash
cat notas.txt | grep examen
```

#### more

Visualiza un archivo por páginas y permite moverte de forma básica.

Sintaxis

```bash
more [opciones] archivo
```

Opciones

- -n  número de líneas por pantalla.

Controles habituales

- Intro → avanza 1 línea
- Espacio o f → avanza 1 página
- b → retrocede 1 página
- /patrón → busca
- q → salir

En sistemas actuales encontrarás less, más potente que more:

```bash
less archivo # navegación con ↑/↓, PgUp/PgDn, /buscar, n/N, q para salir
```

### Búsqueda de archivos y directorios: find

find recorre un subárbol y aplica criterios de selección y acciones.

Sintaxis

```bash
find directorio_inicio [opciones] [acciones]
```
Parámetros

- directorio_inicio  Punto desde el que comenzar (p. ej. . para el actual).

Criterios útiles

- -name "patrón"  Coincidencia por nombre (usa comillas para comodines); -iname ignora mayúsculas.
- -size n[cwbkMG]  Por tamaño: c=bytes, w=palabras de 2 bytes, b=bloques 512B, k=KB, M=MB, G=GB.
Prefijos: +n (más de), -n (menos de), n (exacto).
Ej.: -size +100M (mayores de 100 MB).
- -type c  Por tipo: f archivo regular, d directorio, l enlace simbólico, b bloque, c carácter, p FIFO, s socket.
- Otros frecuentes: -mtime (días desde última modificación), -maxdepth N / -mindepth N.

Acciones

- -print  Muestra la ruta (implícita en GNU find).
- -delete  Borra coincidencias (peligroso, combínalo con -type/-maxdepth).
- -exec comando {} \;  Ejecuta comando una vez por coincidencia.
-exec comando {} + agrupa varias rutas por ejecución (más eficiente).

Ejemplos

```bash
find . -name "*.log" -size +10M -print
find /var/www -type f -mtime -7 -print            # Archivos modificados en 7 días
find /home -type f -name "*.tmp" -delete
find . -type f -iname "*.jpg" -exec cp -t /tmp {} +
```

Para nombres con espacios, usa -print0 y xargs -0:

```bash
find . -type f -name "*.pdf" -print0 | xargs -0 du -h
```

### Compresión de archivos: gzip

gzip comprime cada archivo y genera otro con sufijo .gz (el original se reemplaza por defecto).
Para descomprimir, usa gzip -d o gunzip.

Sintaxis

```bash
gzip [opciones] archivo ...
```

Opciones

- -d  descomprimir.
- -1 … -9  nivel de compresión (por defecto -6): más alto = más lento y mayor compresión.

Ejemplos

```bash
gzip informe.txt          # -> informe.txt.gz
gzip -9 *.csv             # máxima compresión
gunzip informe.txt.gz     # descomprime
```

### Empaquetado de archivos: tar

tar empaqueta muchos archivos en uno solo (tarball). La compresión es opcional y se añade con banderas.

Sintaxis general

```bash
tar [opciones] archivo ...
```

Opciones clave

- -c  crear
- -x  extraer
- -t  listar
- -f <archivo.tar>  usar este fichero (siempre al final del bloque de opciones)
- Compresión:
- -z  gzip  → .tar.gz o .tgz
- -j  bzip2 → .tar.bz2
- -J  xz    → .tar.xz
- --zstd    → .tar.zst

Patrones típicos

```bash
# Crear
tar -cvf curso.tar curso/                    # solo empaquetar
tar -czvf curso.tgz curso/                   # empaquetar + gzip
tar -cJvf curso.tar.xz curso/                # empaquetar + xz

# Listar contenido
tar -tvf curso.tgz

# Extraer
tar -xvf curso.tgz
tar -xvf curso.tgz -C /destino               # extraer en /destino
```

### Enlaces (duros y simbólicos): ln

Un enlace es otra forma de referirse a un archivo.

- Enlace duro (hard link): otro nombre para el mismo inodo. No distingue “original” y “copia de nombre”.
    - No puede apuntar a directorios (salvo casos de sistema) ni cruzar sistemas de archivos distintos.
- Enlace simbólico (soft link / symlink): archivo especial que contiene la ruta del objetivo. Puede apuntar a directorios y cruzar sistemas de archivos.

Sintaxis

```bash
ln [opciones] archivo_origen enlace
```

Parámetros

- archivo_origen  Ruta del objetivo (mejor absoluta para evitar roturas al mover el enlace).
- enlace          Nombre del enlace a crear.

Opciones
- -s  crea un enlace simbólico (sin -s, se crea uno duro).

Ejemplos

```bash
# Enlace duro
ln /var/log/app.log ~/app.log

# Enlace simbólico (recomendado para directorios o entre FS)
ln -s /opt/app/config ~/config-app
ln -s /usr/bin/python3 /usr/local/bin/python
```

Comportamiento según operación

- Visualizar (cat, more, less): verás el contenido del objetivo (en ambos tipos).
- Copiar (cp enlace destino): copias el contenido del objetivo. Para copiar el enlace simbólico como tal, usa cp -d o cp -a.
- Mover (mv enlace destino): mueves el enlace; el objetivo no se mueve.
- Borrar (rm enlace): elimina el enlace. El archivo real se borra solo cuando desaparece su último enlace duro (último nombre).

Para inspeccionar enlaces, usa ls -l (los symlinks muestran enlace -> objetivo).

### Crear archivos y actualizar marcas de tiempo: touch

El comando touch crea archivos vacíos y/o actualiza sus marcas de tiempo (acceso y modificación).

Sintaxis

```bash
touch [opciones] archivo ...
```

Parámetros

- archivo ...  Uno o varios archivos. Si no existen, se crean (salvo -c).

Opciones

- -c  No crea archivos nuevos; solo actualiza marcas si existen.
- -a  Actualiza acceso (atime).
- -m  Actualiza modificación (mtime).
- -d "FECHA"  Establece fecha/hora con texto (ej.: "2025-09-01 08:30").
- -t [[CC]YY]MMDDhhmm[.ss]  Fecha/hora en formato numérico.
- -r <ref>  Copia marcas de tiempo de <ref>.

Ejemplos

```bash
touch notas.txt                                # crea/actualiza
touch -c inexistente.txt                       # no crea (silencio)
touch -a -d "2025-01-01 12:00" informe.log     # solo atime
touch -t 202512311159.59 cierre.log            # 2025-12-31 11:59:59
```

### Buscar texto en archivos: grep

grep busca patrones (expresiones regulares) en texto.

Sintaxis

```bash
grep [opciones] patrón [archivo ...]
```

Opciones útiles:

- -i  Ignora mayúsculas.
- -n  Muestra número de línea.
- -r/-R  Recursivo.
- -w  Coincidencia de palabra completa.
- -v  Invierte (muestra lo que no coincide).
- -c  Cuenta coincidencias.
- -l/-L  Muestra archivos que sí / no contienen el patrón.
- -E  ER extendidas (|, +, ?, () sin escapes).
- -F  Cadena fija (sin regex, más rápido).
- -A N / -B N / -C N  Contexto después, antes, ambos.
- --color=auto  Resalta coincidencias.

Ejemplos

```bash
grep -R "ERROR" /var/log
grep -niw "usuario" *.txt
grep -E "^(INFO|WARN)" app.log
dmesg | grep -i usb
ps aux | grep -E "[f]irefox"                  # evita listar el propio grep
tail -F /var/log/syslog | grep --line-buffered -i "network"
```

### Ver final de archivos y seguir cambios: tail

tail muestra el final de un archivo; con -f sigue anexos (logs). -F reabre si el archivo se rota.

Sintaxis

```bash
tail [opciones] [archivo ...]
```

Opciones

- -n N  Muestra las N últimas líneas (por defecto 10).
- -f    Sigue el crecimiento en tiempo real.
- -c N  Lee los últimos N bytes.
- -q    Silencioso (no imprime cabeceras con múltiples archivos).

Ejemplos

```bash
tail -n 50 /var/log/syslog
tail -f app.log | grep -i error
```