# Práctica 1.1 - El sistema operativo y cómo representa la información

## Parte 1 - Cuestionario

1. Define con tus palabras qué es un sistema operativo (1–2 líneas).
2. Pon un ejemplo de hardware, uno de software y uno de periférico.
3. (V/F) Sin sistema operativo, las aplicaciones podrían usar el hardware con la misma facilidad.
4. Dibuja un esquema por capas con: Usuarios → Aplicaciones → SO → Drivers → Hardware (etiqueta cada capa con 1 ejemplo real).
5. En una frase, diferencia archivo y carpeta.
6. Señala la ruta absoluta y la relativa (marca con A o B):
    <br>
     a) C:\Usuarios\Ana\Fotos\gato.jpg <br>
     b) Documentos\apuntes.txt <br>
7. ¿Para qué sirve la extensión de un archivo? Pon 2 ejemplos.
8. (V/F) En GNU/Linux, los archivos que empiezan por punto (.oculto) no se muestran por defecto.
9. foto.PNG y foto.png ¿son el mismo archivo en todos los sistemas? Explica en 1 línea.
10. Relaciona (traza flechas): Archivo → Contenido, Directorio → Contiene entradas de archivos, Metadatos → Tamaño/fechas/propietario.
11. ¿Qué es metadato? Escribe un ejemplo.
12.	Dibuja un mini-árbol con una carpeta Curso y dentro Apuntes, Practicas y el archivo indice.txt.
13.	Completa: 1 byte = __ bits.
14.	Convierte 1101₂ a decimal (muestra el cálculo con potencias de 2).
15. Pasa 0xA (hex) a binario.
16.	¿Por qué UTF-8 es mejor opción que ASCII para textos con tildes y “ñ”?
17.	Tu conexión dice 100 Mb/s. ¿A cuántos MB/s equivale aproximadamente? (pista: 8 bits = 1 byte)
18.	Señala la unidad correcta para capacidad y para velocidad (elige):<br>
    a) Capacidad: [ Mb | MB | GB ]   <br>
    b) Velocidad de red: [ Mb/s | MB | GiB ]<br>
19.	Nombra tres funciones del sistema operativo (por ejemplo “gestiona ___”).
20.	¿Qué es un proceso? (1 línea)
21.	El planificador reparte ___ entre procesos (elige: RAM / CPU / pantalla).
22.	(V/F) Si un proceso se “cuelga”, el sistema se apaga forzosamente.
23.	Marca si la tarea es CPU-bound o I/O-bound:<br>
    a) Comprimir un vídeo grande → __ ; <br>
    b) Copiar mil fotos a un pendrive → __ <br>
24.	¿Por qué existe la memoria virtual? (elige la mejor)<br>
    a) Para que los vídeos se vean en 4K.<br>
    b) Para simular más memoria usando disco cuando la RAM no alcanza.<br>
    c) Para que los iconos se vean más bonitos.<br>
25.	Completa: los permisos indican quién puede hacer qué con un archivo o carpeta.
26.	En Linux, ¿qué significa r en un archivo? ¿y x en un directorio? (1 palabra cada uno).
27.	(V/F) En Windows, “solo lectura” es un atributo; los permisos detallados se configuran en Seguridad (ACL).
28.	¿Para qué sirve tener usuarios y grupos distintos en un equipo? (indica dos):
    - Organización
    - Seguridad 
    - Decoración de iconos 
    - Control de acceso
29.	¿Por qué no es buena idea poner “permiso total para todos” en una carpeta compartida?
30.	Define en 1 línea qué es una transacción.
31.	Explica en 1–2 líneas qué hace el journaling de un sistema de archivos.
32.	(V/F) Con journaling, tras un corte de luz el sistema tarda menos en recuperar el estado.
33.	¿Qué recomendación debes seguir siempre con un USB antes de retirarlo?
34.	Elige el sistema de archivos más adecuado para cada caso (marca 1):<br>
    a) USB que usarás en Windows, macOS y Linux: [ FAT32 | exFAT | NTFS ]<br>
    b) Disco del sistema en Windows: [ FAT32 | exFAT | NTFS ]<br>
    c) Datos en GNU/Linux: [ ext4 | exFAT | FAT32 ]<br>


## Parte 2 - Mi sistema operativo en una página

Elabora una ficha clara y visual sobre un sistema operativo actual (a elegir: Windows 11 o Ubuntu), usando lenguaje sencillo y apoyos visuales. No hace falta entrar en comandos ni configuraciones avanzadas.

1. ¿Qué es y para qué sirve? (2–3 frases)
2. Funciones principales (3 viñetas): procesos, memoria, archivos, red…
3. Cómo organiza los datos: qué es un archivo, una carpeta, y ejemplos de extensiones típicas.
4. Sistema de archivos por defecto (nómbralo; p. ej., NTFS, ext4, APFS) y una ventaja práctica (p. ej., journaling).
5. Buenas prácticas de uso (3 viñetas): expulsar USB, actualizar, cuenta no admin…
6. Mini-glosario (4 términos): proceso, permiso, extensión, journaling.
7. Un esquema simple (dibujado o incrustado): “Usuario → Aplicaciones → SO → Hardware”.

## Criterios de evaluación

Esta tarea evalúa todos los criterios de evaluación del **RA1**.

## Método de entrada

Crea un único archivo PDF y súbelo a la tarea correspondiente en la plataforma Moodle Centros con la siguiente nomenclatura:

Apellido1Apellido2_Nombre_SOM_PR1-1.pdf