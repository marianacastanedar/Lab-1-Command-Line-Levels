## Bandit Level 0
**Objetivo:**  
Conectarse al servidor y encontrar la contraseña para el siguiente nivel.

**Comandos utilizados:**
```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
```

**Explicación:**
Pues básicamente me conecté por SSH con el usuario bandit0 y contraseña bandit0. Una vez adentro, usé `ls` para ver qué archivos había y ahí estaba el archivo `readme`. Le hice `cat` para leerlo y ahí salió la contraseña del siguiente nivel.

**Contraseña obtenida:**
 ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## Bandit Level 1
**Objetivo:**  
Leer un archivo con nombre especial (-) para obtener la contraseña del siguiente nivel.

**Comandos utilizados:**
```bash
ls
cat ./-
```

**Explicación:**
El archivo se llamaba `-`, que es un carácter especial en bash. Si intentas hacer `cat -` se queda esperando input del teclado porque `-` representa stdin. La solución fue usar `cat ./-` para especificar la ruta relativa del archivo y que bash lo interprete como un archivo literal.

**Contraseña obtenida:**
263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## Bandit Level 2
**Objetivo:**  
Leer un archivo que contiene espacios y guiones en su nombre.

**Comandos utilizados:**
```bash
ls
cat -- "--spaces in this filename--"
```

**Explicación:**
El archivo se llamaba `--spaces in this filename--`. Tenía dos problemas: espacios en el nombre y empezaba con `--` que bash interpreta como opciones del comando. La solución fue usar `cat --` para indicarle a cat que lo siguiente no son opciones, sino el nombre del archivo, y ponerlo entre comillas por los espacios.

**Contraseña obtenida:**
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## Bandit Level 3
**Objetivo:**  
Encontrar la contraseña en un archivo oculto dentro del directorio inhere.

**Comandos utilizados:**
```bash
cd inhere
ls -a
cat ...Hiding-From-You
```

**Explicación:**
Entré al directorio `inhere` y usé `ls -a` para listar todos los archivos, incluyendo los ocultos (los que empiezan con punto). Ahí apareció el archivo `...Hiding-From-You` que tenía tres puntos al inicio. Le hice `cat` y salió la contraseña.

**Contraseña obtenida:**
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## Bandit Level 4
**Objetivo:**  
Encontrar el único archivo legible por humanos en el directorio inhere.

**Comandos utilizados:**
```bash
cd inhere
ls
file ./*
cat ./-file07
```

**Explicación:**
Entré al directorio `inhere` y había un montón de archivos que empezaban con guión. Usé `file ./*` para verificar el tipo de cada archivo. Todos decían "data" excepto `-file07` que decía "ASCII text", o sea, el único legible. Le hice `cat ./-file07` (con `./` porque empieza con guión) y salió la contraseña.

**Contraseña obtenida:**
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## Bandit Level 5
**Objetivo:**  
Encontrar un archivo con propiedades específicas: legible por humanos, 1033 bytes de tamaño y no ejecutable.

**Comandos utilizados:**
```bash
cd inhere
find . -type f -size 1033c ! -executable
cat ./maybehere07/.file2
```

**Explicación:**
Entré al directorio `inhere` que tenía un montón de subdirectorios. Usé `find` con filtros para buscar archivos (`-type f`) de exactamente 1033 bytes (`-size 1033c`) que no fueran ejecutables (`! -executable`). El comando encontró `./maybehere07/.file2`. Le hice `cat` y salió la contraseña.

**Contraseña obtenida:**
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## Bandit Level 6
**Objetivo:**  
Encontrar un archivo en todo el servidor con propiedades específicas: usuario bandit7, grupo bandit6 y 33 bytes de tamaño.

**Comandos utilizados:**
```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password
```

**Explicación:**
Usé `find` desde la raíz del sistema (`/`) para buscar en todo el servidor. Filtré por archivos (`-type f`) del usuario bandit7 (`-user bandit7`), grupo bandit6 (`-group bandit6`) y tamaño de 33 bytes (`-size 33c`). El `2>/dev/null` redirige los errores de permisos denegados para que no llenen la pantalla. Encontró el archivo en `/var/lib/dpkg/info/bandit7.password`, le hice `cat` y salió la contraseña.

**Contraseña obtenida:**
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## Bandit Level 7
**Objetivo:**  
Encontrar la contraseña que está al lado de la palabra "millionth" en el archivo data.txt.

**Comandos utilizados:**
```bash
grep millionth data.txt
```

**Explicación:**
El archivo `data.txt` tenía un montón de líneas. Usé `grep` para buscar la palabra "millionth" y me mostró solo la línea que la contenía. Ahí estaba la contraseña al lado.

**Contraseña obtenida:**
dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## Bandit Level 8
**Objetivo:**  
Encontrar la única línea de texto que aparece solo una vez en el archivo data.txt.

**Comandos utilizados:**
```bash
sort data.txt | uniq -u
```

**Explicación:**
El archivo `data.txt` tenía muchas líneas repetidas y solo una única. Usé `sort` para ordenar todas las líneas (requisito para que `uniq` funcione correctamente) y luego `uniq -u` para mostrar solo las líneas que aparecen una sola vez. Salió la contraseña.

**Contraseña obtenida:**
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## Bandit Level 9
**Objetivo:**  
Encontrar la contraseña en un archivo que contiene datos binarios, precedida por varios caracteres '='.

**Comandos utilizados:**
```bash
strings data.txt | grep "=="
```

**Explicación:**
El archivo `data.txt` tenía datos binarios mezclados con texto. Usé `strings` para extraer solo las cadenas de texto legibles y luego `grep "=="` para filtrar las líneas que contenían varios signos igual. Ahí apareció la contraseña precedida por `==========`.

**Contraseña obtenida:**
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey