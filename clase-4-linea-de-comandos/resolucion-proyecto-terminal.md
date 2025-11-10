#### EJERCICIO 1

```bash
cd thecmdchallenge/
```

#### EJERCICIO 2

```bash
pwd
```

#### EJERCICIO 3

```bash
ls --all
```

#### EJERCICIO 4

```bash
ls -R
```

#### EJERCICIO 5

```bash
clear
```

#### EJERCICIO 6

```bash
cd small-name

cat /bigger-name-than-before/omg-this-folder-has-a-huuuuuuge-name-and-i-tired-to-type/this-is-probably-the-longest-folder-name-you-have-ever-seen-but-believe--im-sure-there-are-other-folder-bigger-than-this-one-because-people-sometimes-like-to-assign-huge-names-to-their-personal-stuff-supercalifragilisticexpialidocious/trophy.txt
```

#### EJERCICIO 7

```bash
cd funcode/

ls *.js
```

#### EJERCICIO 8

```bash
mkdir not-that-funny
```

#### EJERCICIO 9

```bash
ls ../boringfolder/ -R
cp ../boringfolder/even-more-boring/i-cant-believe-how-boring/the-ultimate-boring-inception/the-mostboring-text.txt  not-that-funny/lol.txt
# tambien podemos copiar y luego renombrar con move
mv nombre_antiguo nombre_nuevo
```

#### EJERCICIO 10

```bash
mv kids.jpg ./images/hello/
```

#### EJERCICIO 11

```bash
 rm -rf small-name/
```

#### EJERCICIO 12

```bash
find . -name "the-ultimate-joke.txt"
cat {{directorio proporcionado por el find}}
```

#### EJERCICIO 13

```bash
rm -rf boringfolder/
```

#### EJERCICIO 12

```bash
vi kamehameha/dragon-ball-jokes.md
```

#### EJERCICIO 12

Tenemos los siguientes comandos para ejecumtar dentro del editor de texto

| Comando               | Acción                                                                          |
| --------------------- | ------------------------------------------------------------------------------- |
| `i`                   | Entrar en modo de inserción (insertar texto antes del cursor)                   |
| `a`                   | Entrar en modo de inserción (insertar texto después del cursor)                 |
| `ESC`                 | Volver al modo comando                                                          |
| `x`                   | Borrar el carácter bajo el cursor                                               |
| `dd`                  | Borrar la línea actual                                                          |
| `dw`                  | Borrar la palabra actual                                                        |
| `h`, `j`, `k`, `l`    | Mover el cursor a la izquierda, abajo, arriba y derecha, respectivamente        |
| `Ctrl-F`              | Avanzar una pantalla                                                            |
| `Ctrl-B`              | Retroceder una pantalla                                                         |
| `Ctrl-D`              | Desplazarse media pantalla hacia adelante                                       |
| `Ctrl-U`              | Desplazarse media pantalla hacia atrás                                          |
| `:w`                  | Guardar los cambios                                                             |
| `:q`                  | Salir del editor (sin guardar si hay cambios sin guardar)                       |
| `:wq`                 | Guardar y salir                                                                 |
| `:q!`                 | Salir sin guardar los cambios                                                   |
| `n` (ej. `3dd`)       | Ejecutar un comando n veces (por ejemplo, `3dd` borra tres líneas)              |
| `u`                   | Deshacer el último cambio                                                       |
| `^`                   | Mover el cursor al principio de la línea                                        |
| `$`                   | Mover el cursor al final de la línea                                            |
| `G`                   | Ir al final del archivo                                                         |
| `:número`             | Ir a una línea específica (por ejemplo, `:10` va a la línea 10)                 |
| `cw`                  | Cambiar la palabra actual                                                       |
| `y` / `yy`            | Copiar el carácter o línea según el contexto (por ejemplo, `yy` copia la línea) |
| `p`                   | Pegar el contenido copiado/cortado después del cursor                           |
| `/texto`              | Buscar la siguiente ocurrencia de "texto"                                       |
| `?texto`              | Buscar la anterior ocurrencia de "texto"                                        |
| `n`                   | Ir a la siguiente coincidencia de la búsqueda                                   |
| `N`                   | Ir a la coincidencia anterior de la búsqueda                                    |
| `:s/antiguo/nuevo/g`  | Reemplazar todas las ocurrencias de "antiguo" por "nuevo" en la línea actual    |
| `vi nombre_archivo`   | Inicia vi para editar nombre_archivo (lo crea si no existe)                     |
| `vi +45 archivo`      | Abre archivo y posiciona el cursor en la línea 45                               |
| `vi +/patrón archivo` | Abre archivo y posiciona el cursor en la primera ocurrencia de "patrón"         |

[Guía de comandos vi (Oracle)](https://docs.oracle.com/cd/E19620-01/805-7644/6j76klopr/index.html)
