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
