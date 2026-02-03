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