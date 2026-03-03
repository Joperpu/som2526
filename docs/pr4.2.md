# Práctica 4.2 - Gestión de discos, volúmenes y cuotas en Windows 11

## Descripción de la práctica

Un equipo con Windows 11 Pro se va a utilizar en un aula de informática. Se ha instalado un segundo disco duro para almacenamiento de datos y se quiere:

- Prepararlo correctamente.
- Crear particiones diferenciadas.
- Controlar el uso del espacio por parte de los alumnos.
- Optimizar el rendimiento del sistema.

## Parte 1 – Administración de discos

**Ejercicio 1. Acceso y análisis inicial**

1.	Abre Administración de equipos → Administración de discos.
2.	Indica:
    - Cuántos discos aparecen (Disco 0, Disco 1…).
    - Qué tipo de particiones tiene el disco principal.
    - Qué sistema de archivos utiliza cada volumen.
3.	Explica la diferencia entre la vista superior (lista) y la vista inferior (gráfica).

**Ejercicio 2. Inicialización de un disco nuevo**

Añade un disco nuevo a la máquina virtual y comprueba que aparece como “No inicializado”.

1.	Inicializa el disco.
2.	Elige entre:
    - MBR
    - GPT
3.	Justifica técnicamente tu elección.
4.	Explica brevemente la diferencia entre MBR y GPT.

## Parte 2 – Creación y formateo de volúmenes

**Ejercicio 3. Crear un nuevo volumen simple**

En el espacio sin asignar:

1.	Crea un nuevo volumen simple utilizando todo el espacio disponible.
2.	Asigna la letra:
    - F:
3.	Etiqueta del volumen:
    - DATOS_AULA
4.	Sistema de archivos:
    - NTFS
5.	Activa formato rápido.

**Ejercicio 4. Formateo de partición**

1.	Formatea el volumen recién creado.
2.	Indica:
    - Sistema de archivos elegido.
    - Tamaño de unidad de asignación.
    - Si activaste formato rápido.
3.	Explica qué ocurre con la información al formatear.
4.	Indica en qué casos se usaría FAT32 en lugar de NTFS.

## Parte 3 – Extender y reducir volúmenes

**Ejercicio 5. Reducir una partición**

1.	Reduce el volumen F: en 1024 MB.
2.	Comprueba que se ha generado espacio sin asignar.
3.	Explica:
    - Qué ocurre internamente al reducir.
    - Por qué solo puede hacerse en NTFS.

**Ejercicio 6. Extender una partición**

1.	Extiende nuevamente el volumen F: usando el espacio sin asignar generado.
2.	Explica:
    - Por qué debe ser espacio contiguo.
    - En qué casos Windows puede solicitar convertir el disco en dinámico.

## Parte 4 – Liberación y optimización del disco

**Ejercicio 7. Liberador de espacio en disco**

En la unidad C:

1.	Accede a Propiedades → Liberador de espacio en disco.
2.	Indica qué tipos de archivos se pueden eliminar.
3.	Ejecuta la opción Limpiar archivos del sistema.
4.	Explica:
    - Diferencia entre limpiar archivos de usuario y archivos del sistema.
    - Por qué un disco lleno afecta al rendimiento.

**Ejercicio 8. Optimización y desfragmentación**

1.	Accede a Propiedades → Herramientas → Optimizar.
2.	Analiza la unidad.
3.	Indica:
    - Tipo de unidad (HDD o SSD).
    - Estado actual.
4.	Explica la diferencia entre:
    - Desfragmentación (HDD).
    - Optimización/TRIM (SSD).

## Parte 5 – Cuotas de disco en NTFS

**Ejercicio 9. Activar cuotas**

En la unidad F:

1.	Accede a Propiedades → pestaña Cuota.
2.	Activa:
    - Habilitar administración de cuota.
    - Limitar el espacio en disco a: 500 MB.
    - Nivel de advertencia: 450 MB.
    - Denegar espacio en disco a usuarios que superen el límite.
3.	Activa el registro de eventos.

**Ejercicio 10. Cuotas personalizadas**

1.	Crea una entrada específica para el usuario:
    - alumno_prueba
2.	Establece:
    - Límite: 200 MB.
    - Advertencia: 180 MB.
3.	Explica:
    - Qué ocurre si supera el límite.
    - Qué diferencia hay entre límite general y límite específico.

## Parte 6 - Caso práctico completo

**Supuesto**

El disco C: tiene solo un 5 % de espacio libre y el equipo funciona lentamente. Además, varios alumnos han llenado la unidad D: con archivos multimedia.

**Tareas**

1.	Indica qué herramientas usarías para solucionar el problema.
2.	Explica el orden lógico de actuación.
3.	Indica:
    - Cómo liberar espacio en C: sin afectar al sistema.
    - Cómo evitar que vuelva a ocurrir en D:.
4.	Justifica por qué las cuotas son útiles en entornos educativos.

## Entrega

Crea un documento PDF, a partir de un Word o Google Docs, con las siguientes consideraciones:

- El nombre del archivo a entregar en la plataforma Moodle Centros debe tener el siguiente formato: `Apellido1Apellido2_Nombre_SOM_UD4_P2.pdf`.
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