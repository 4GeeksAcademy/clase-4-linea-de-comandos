# Introducción a la línea de comandos (Terminal)

La línea de comandos, también llamada terminal o consola, es una herramienta que permite interactuar con el sistema operativo escribiendo instrucciones (comandos). Es muy útil para programadores y administradores de sistemas.

## ✅ ¿Para qué sirve la terminal?

- Navegar entre carpetas y archivos.
- Crear, copiar, mover y eliminar archivos y carpetas.
- Instalar y ejecutar programas.
- Automatizar tareas repetitivas.

## ✅ ¿Cómo funciona?

- Escribes un comando, pulsas Enter y el sistema ejecuta la orden.
- Puedes combinar comandos y usar opciones para tareas más avanzadas.

---

## ✅ Comandos más importantes (índice)

1. [Navegación](#navegación)
2. [Archivos y carpetas](#archivos-y-carpetas)
3. [Otros comandos útiles](#otros-comandos-útiles)
4. [Comando rm: explicación y precauciones](#comando-rm-explicación-y-precauciones)

---

### Navegación

- `pwd` — Muestra la ruta de la carpeta actual (en Windows: `cd` sin argumentos)
- `ls` — Lista los archivos y carpetas (en Windows: `dir`)
- `cd nombre_carpeta` — Cambia de carpeta
- `cd ..` — Sube una carpeta
- `cd /` — Va a la raíz del sistema

### Archivos y carpetas

- `mkdir nombre` — Crea una carpeta nueva
- `touch archivo.txt` — Crea un archivo vacío (en Windows: `type nul > archivo.txt`)
- `rm archivo.txt` — Elimina un archivo
- `rm -r carpeta` — Elimina una carpeta y su contenido
- `rmdir carpeta` — Elimina una carpeta vacía
- `cp origen destino` — Copia archivos o carpetas
- `mv origen destino` — Mueve o renombra archivos o carpetas

### Otros comandos útiles

- `clear` — Limpia la pantalla de la terminal (en Windows: `cls`)
- `cat archivo.txt` — Muestra el contenido de un archivo
- `echo texto` — Muestra un texto en pantalla
- `tree` — Muestra la estructura de carpetas y archivos en forma de árbol (puede requerir instalación)
- `find . -name "archivo.txt"` — Busca archivos por nombre en la carpeta actual y subcarpetas

### Uso del Find

#### 🔤 Coincidencias por nombre o patrón

| Opción   | Descripción                                                 | Sensibilidad a mayúsculas/minúsculas | Ejemplo                              |
| -------- | ----------------------------------------------------------- | ------------------------------------ | ------------------------------------ |
| `-name`  | Busca archivos que coincidan exactamente con el nombre dado | Sí                                   | `find . -name "archivo.txt"`         |
| `-iname` | Igual que `-name`, pero no distingue mayúsculas/minúsculas  | No                                   | `find . -iname "archivo.txt"`        |
| `-regex` | Busca por expresión regular en la ruta completa             | Sí                                   | `find . -regex ".*\.txt"`            |
| `-path`  | Coincide con una ruta específica                            | Sí                                   | `find . -path "./docs/archivo.txt"`  |
| `-ipath` | Igual que `-path`, pero no distingue mayúsculas/minúsculas  | No                                   | `find . -ipath "./docs/ARCHIVO.TXT"` |

#### 📂 Tipo de archivo

| Opción    | Descripción         | Ejemplo             |
| --------- | ------------------- | ------------------- |
| `-type f` | Solo archivos       | `find . -type f`    |
| `-type d` | Solo directorios    | `find . -type d`    |
| `-type l` | Enlaces simbólicos  | `find / -type l`    |
| `-type s` | Sockets             | `find /var -type s` |
| `-type p` | Pipes (named pipes) | `find /tmp -type p` |

#### ⏰ Por fecha de modificación / acceso

| Opción      | Descripción                         | Ejemplo            |
| ----------- | ----------------------------------- | ------------------ |
| `-mtime n`  | Modificados hace exactamente n días | `find . -mtime 3`  |
| `-mtime -n` | Modificados en los últimos n días   | `find . -mtime -7` |
| `-mtime +n` | Modificados hace más de n días      | `find . -mtime +7` |
| `-atime n`  | Último acceso hace n días           | `find . -atime 1`  |
| `-mmin n`   | Modificados hace n minutos          | `find . -mmin 30`  |
| `-amin n`   | Último acceso hace n minutos        | `find . -amin 10`  |

```bash
find . -type f -mtime -1
```

#### 📏 Por tamaño

| Opción        | Descripción                  | Ejemplo              |
| ------------- | ---------------------------- | -------------------- |
| `-size +100M` | Archivos de más de 100 MB    | `find . -size +100M` |
| `-size -10k`  | Archivos de menos de 10 KB   | `find . -size -10k`  |
| `-size 1G`    | Archivos de exactamente 1 GB | `find . -size 1G`    |

```bash
find /var/log -type f -size +50M
```

#### 👤 Por propietario o grupo

| Opción          | Descripción                       | Ejemplo                   |
| --------------- | --------------------------------- | ------------------------- |
| `-user usuario` | Archivos de un usuario específico | `find /home -user alvaro` |
| `-group grupo`  | Archivos de un grupo específico   | `find /var -group admin`  |
| `-nouser`       | Archivos sin usuario válido       | `find /tmp -nouser`       |
| `-nogroup`      | Archivos sin grupo válido         | `find /tmp -nogroup`      |

```bash
find /home -user alvaro
```

#### 🔒 Por permisos

| Opción       | Descripción                                          | Ejemplo             |
| ------------ | ---------------------------------------------------- | ------------------- |
| `-perm 644`  | Exactamente con permisos 644                         | `find . -perm 644`  |
| `-perm -u=x` | Archivos donde el usuario tiene permiso de ejecución | `find . -perm -u=x` |
| `-perm /g=w` | Archivos donde el grupo tiene permiso de escritura   | `find . -perm /g=w` |

```bash
find . -type f -perm -u=x
```

#### ⚙️ Ejecutar acciones sobre lo encontrado

| Opción                | Descripción                                                     | Ejemplo                           |
| --------------------- | --------------------------------------------------------------- | --------------------------------- |
| `-print`              | Muestra la ruta de cada archivo encontrado (por defecto)        | `find . -type f -print`           |
| `-exec comando {} \;` | Ejecuta un comando por cada archivo encontrado                  | `find . -type f -exec rm {} \;`   |
| `-exec comando {} +`  | Ejecuta el comando con varios archivos a la vez (más eficiente) | `find . -type f -exec ls -l {} +` |
| `-delete`             | Borra los archivos encontrados                                  | `find . -type f -delete`          |

```bash
find . -type f -name "*.log" -delete
```

#### 🔁 Combinaciones lógicas

| Operador | Descripción                          | Ejemplo                                 |
| -------- | ------------------------------------ | --------------------------------------- |
| `-and`   | Combina dos condiciones (ambas)      | `find . -type f -and -name "*.log"`     |
| `-or`    | Combina dos condiciones (una u otra) | `find . -name "*.txt" -or -name "*.md"` |
| `!`      | Niega una condición                  | `find . -type f ! -name "*.log"`        |

```bash
find . -type f -name "*.log" -delete
```
---

## Comando rm: explicación y precauciones

El comando `rm` (remove) se usa para borrar archivos y carpetas. ¡Cuidado! Lo que borres con `rm` no va a la papelera, se elimina permanentemente.

- `rm archivo.txt` — Borra un archivo.
- `rm -r carpeta` — Borra una carpeta y todo su contenido.
- `rm -f archivo.txt` — Borra sin pedir confirmación.
- `rm -rf carpeta` — Borra una carpeta y todo dentro, sin pedir confirmación (¡mucho cuidado!).

### Esquema visual:

```
/home/usuario/
│
├── documentos/
│     ├── trabajo.docx
│     └── tareas.txt
├── fotos/
│     └── verano.jpg
└── notas.txt
```

Si ejecutas:

```bash
rm notas.txt
```

Solo se borra el archivo `notas.txt`.

Si ejecutas:

```bash
rm -r fotos
```

Se borra la carpeta `fotos` y todo lo que contiene (`verano.jpg`).

Si ejecutas:

```bash
rm -rf documentos
```

Se borra la carpeta `documentos` y todos sus archivos.

> ⚠️ Usa `rm` con precaución. Si tienes dudas, revisa dos veces el nombre antes de pulsar Enter.

---

## Consejos

- Usa la tecla Tab para autocompletar nombres de archivos o carpetas.
- Usa las flechas arriba/abajo para repetir comandos anteriores.
- ¡No tengas miedo de experimentar! Puedes buscar ayuda con `comando --help`.

¿Quieres practicar? Abre la terminal en tu sistema y prueba estos comandos en una carpeta de prueba.
