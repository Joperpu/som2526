# Práctica 3.6 - Administración de usuarios, grupos y permisos

## Descripción de la tarea

Realiza una captura de pantalla para cada uno de los ejercicios que lo requiera. Además, crea el siguiente árbol de directorios y archivos:

```bash
/lab
├── permisos
│   ├── compartida/
│   ├── docs/
│   │   └── manual.txt
│   ├── privada/
│   │   └── secret.txt
│   ├── publica/
│   │   └── aviso.txt
│   ├── scripts/
│   │   └── backup.sh
│   └── tmp/
└── proyectos
    ├── proyA/
    │   └── README.md
    └── proyB/
        └── README.md
```

## Ejercicios


1. Muestra tu propia entrada con getent passwd $USER y explica los 7 campos.
2. Localiza UID_MIN y UID_MAX en /etc/login.defs y anótalos.
3. Muestra los grupos existentes con getent group | head -n 10 y explica los campos.
4. Verifica que /etc/shadow y /etc/gshadow solo son legibles por root (ls -l).
5. Crea los grupos: docentes, alumnos, proyectos.
6. Crea los usuarios (con HOME, shell bash):
    - alumno1 y alumno2 en grupo principal propio y grupos suplementarios alumnos.
    - mlopez en grupo principal docentes y suplementarios proyectos.
    - Usuario de sistema appsvc sin login interactivo y sin HOME.
7. Asigna contraseña a alumno1 y mlopez con passwd.
8. Fuerza cambio de clave en próximo login para alumno1.
9. Establece a mlopez: máximo 90 días, aviso 7, mínimo 1 día.
10. Bloquea y desbloquea la contraseña de alumno2. Verifica estado con passwd -S.
11. Añade alumno1 y alumno2 al grupo proyectos (sin perder grupos actuales).
12. Renombra el grupo docentes a profesores y cambia su GID.
13.	Establece/retira una contraseña de grupo en proyectos con gpasswd y comprueba el efecto al usar newgrp.
14.	Cambia la shell de alumno2 a /bin/bash.
15.	Renombra mlopez a marta.lopez y mueve su HOME a /srv/users/marta.lopez preservando contenido.
16.	Cambia el grupo principal de alumno1 a alumnos. Verifica con id.
17. Cierra procesos de alumno2 si los hubiera y elimina la cuenta conservando el HOME.
18. Elimina alumno2 definitivamente con userdel -r.
19. Busca posibles ficheros huérfanos por UID de usuarios eliminados en /lab y documéntalo.
20. En /lab/permisos/docs, fija manual.txt a 644 y explica quién puede leer/escribir/ejecutar.
21. En /lab/permisos/scripts, establece backup.sh a 750 y ejecútalo desde un usuario sin permisos: justifica el resultado.
22. Cambia permisos simbólicos y octales mostrando equivalencias (ej.: u+x, g-w, 640 ↔ u=rw,g=r,o=).
23. En /lab/permisos/privada, deja permisos r--r----- y prueba:
    - Listar nombres, listar con detalles y entrar con cd.
    - Acceder a secret.txt con ruta completa. Resume en una tabla qué combinaciones de r/x permiten cada acción.
24. En /lab/permisos/publica, configura 755 y comprueba acceso desde otra cuenta.
25. Cambia propietario y grupo de /lab/permisos/docs/manual.txt a marta.lopez:profesores.
26. Cambia el grupo de /lab/permisos/compartida a proyectos de forma recursiva.
27. Explica la diferencia entre chown :grupo y chgrp.
28. Asigna a /lab/proyectos el grupo proyectos y permisos 2775 (setgid).
29. Haz lo mismo dentro de proyA y proyB y comprueba que los archivos creados por distintos usuarios del grupo heredan el grupo correcto.
30. Ajusta los permisos efectivos para trabajo colaborativo (p. ej., 664 para archivos y 775 para directorios) y comenta el papel de la umask (usa umask y un ejemplo práctico).
31.	Configura /lab/permisos/tmp con permisos 1777.
32.	Prueba que un usuario no puede borrar el fichero de otro dentro de esa carpeta y explica por qué.
	
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