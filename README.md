# UNIX y LINUX - Guía Práctica.

Comando básicos Unix y Linux.

## INTRO Información

Vamos a ver a continuación la sintaxis y función de algunas órdenes sencillas con obheto de familiarizarnos con la técnica general utilizada en UNIX para invocar programas.


### Algunas órdenes para comenzar.

Cuando deseamos finalizar una sesión de trabajo, deberemos informar de ello al sistema. <br/>La orden <b>exit</b> se emplea para avisar al sistema de nuestro fin de sesión.<br/>
<b>Sintaxis: exit</b>

```
[y2k@anaconda ~]$ exit
cerrar sesión
root@anaconda:~ #
```

### Sintaxis: `who (am i)`

La orden o comando `who` Nos informa acerca de quién o quiénes están conectados actualmente al sistema. También muestra información,<br/>
en la segunda columna, relativa al terminal asociado a cada usuario, y por último, en la columna tercera, la fecha y hora en la que el usuario entró en sesión.


```
root@anaconda:~ # who
y2k              pts/2        Feb 17 13:27 (192.168.1.200)
root@anaconda:~ # 
```


### Sintaxis: `mail usuario(s)`
El sistema UNIX/LINUX proporciona un mecanismo de correo electrónico o e-mail que permite envíar mensajes de unos usuarios a otros.<br/>
Para enviar un mensaje no es necesario que el usuario destinatario esté conectado en ese momento.<br/>
Ya que toda la correspondencia será depositada en su buzón.


```
[y2k@anaconda ~]$ mail
No mail for y2k
[y2k@anaconda ~]$
```

```
[y2k@anaconda ~]$ mail --help
mail: illegal option -- -
Usage: mail [-dEiInv] [-s subject] [-c cc-addr] [-b bcc-addr] [-F] to-addr ...
            [-sendmail-option ...]
       mail [-dEHiInNv] [-F] -f [name]
       mail [-dEHiInNv] [-F] [-u user]
       mail [-d] -e [-f name]
[y2k@anaconda ~]$
```

```
[luis@anaconda ~]$ mail y2k@localhost
Subject: Prueba de Mensajeria Mail.
Hola, Este es un mensaje Test.
.
EOT
[luis@anaconda ~]$
```

```
[luis@anaconda ~]$ mail y2k@localhost
Subject: Prueba de Mensajeria Mail.
Hola, Este es un mensaje Test.
.
EOT
[luis@anaconda ~]$
```

### Sintaxis: `write usuario`
La orden o comando `write` Se utiliza para comunicarnos con otros usuarios que estén en ese momento conectados a nuestro mismo sistema.<br/>
(write) NO funciona para usuarios en sistemas diferentes. `En este EJ tenemos los usuarios luis y y2k` <br/>
El usuario: luis, escribira al usuario y2k. Para que vea el mensaje en el terminal.


```
[luis@anaconda ~]$ write y2k 
Hola y2k, soy Luis! :)
```

El usuario: `luis` envio un mensaje al usuario `y2k` En tiempo real. Ahora veamos como veria el usuario. y2k. el mensaje.


```
[y2k@anaconda ~]$ ~
Message from y2k@anaconda on pts/1 at 13:50 ...
Hola y2k, soy Luis! :)
```

### Sintaxis: `mesg [y/n]`

Esta orden se utiliza para modificar los derechos de escritura por parte de los otros usuarios en nuestro terminal.<br/>
De tal manera que si alguien nos quiere enviar un mensaje tenemos desactivados estos derechos, no seremos interrunpidos.<br/>
La prohibición de acceso de escritura no afecta al administrador del sistema. `root` .


```
[y2k@anaconda ~]$ mesg
is y
[y2k@anaconda ~]$ mesg n
[y2k@anaconda ~]$ mesg
is n
[y2k@anaconda ~]$
```


### Sintaxis: `date`

Esta orden se 


```
[y2k@anaconda ~]$ date

```




### Sintaxis: `echo`

Esta orden se 


```
[y2k@anaconda ~]$ echo

```



### Sintaxis: `banner`

Esta orden se 


```
[y2k@anaconda ~]$ banner

```



### Sintaxis: `cal`

Esta orden se 


```
[y2k@anaconda ~]$ cal

```



### Sintaxis: `uname`

Esta orden se 


```
[y2k@anaconda ~]$ uname

```




### Sintaxis: `password`

Esta orden se 


```
[y2k@anaconda ~]$ password

```



### Sintaxis: `lpr`

Esta orden se 


```
[y2k@anaconda ~]$ lpr

```



### Sintaxis: `lp`

Esta orden se 


```
[y2k@anaconda ~]$ lp

```

### Sintaxis: `script`

Esta orden se 


```
[y2k@anaconda ~]$ script

```


### Sintaxis: `man`

Esta orden se 


```
[y2k@anaconda ~]$ man

```



## El sistema de archivos.

Concepto de archivo y de sistema de archivos en UNIX.<br/>

Podemos definir de forma genérica el término archivo como un conjunto de datos con un nombre asociado.<br/>
Los archivos suelen residir en dispositivos de almacenamiento secundarios, tales como DVD/CD/USB Pen/HDD/SSD. etc.<br/>
La razón de asignar un nombre a cada archivo es que de este modo tanto los usuarios como los programas pueden hacer referencia a los mismos de una forma lógica.<br/>
Los procesos o programas en ejecución disponen de un conjunto de funciones proporcionadas por el sistema operativo para poder manipular esos archivos.<br/>
Ese conjunto de funciones se conoce con el nombre de llamadas al sistema o `system calls.`<br/>
El concepto de llamada al sistema es más amplio, pues engloba también funciones relacionadas con la manipulación de procesos y dispositivos.


## Manipulación de archivos y directorios.


### Sintaxis: `ls [-lFaRd] [archivo(s)]`

Esta orden se 


```
[y2k@anaconda ~]$ ls

```

### Sintaxis: `pwd`

Esta orden se 


```
[y2k@anaconda ~]$ pwd

```

### Sintaxis: `cd`

Esta orden se 


```
[y2k@anaconda ~]$ cd

```

### Sintaxis: `mkdir` y `rmdir`

Esta orden se 


```
[y2k@anaconda ~]$ mkdir

```

### Sintaxis: `cat`

Esta orden se 


```
[y2k@anaconda ~]$ cat

```


### Sintaxis: `more`

Esta orden se 


```
[y2k@anaconda ~]$ more

```



### Sintaxis: `head` y `tail`

Esta orden se 


```
[y2k@anaconda ~]$ head

```


### Sintaxis: `od`

Esta orden se 


```
[y2k@anaconda ~]$ od

```


### Sintaxis: `cp`

Esta orden se 


```
[y2k@anaconda ~]$ cp

```


### Sintaxis: `mv`

Esta orden se 


```
[y2k@anaconda ~]$ mv

```


### Sintaxis: `ln`

Esta orden se 


```
[y2k@anaconda ~]$ ln

```


### Sintaxis: `rm`

Esta orden se 


```
[y2k@anaconda ~]$ rm

```


### Sintaxis: `file`

Esta orden se 


```
[y2k@anaconda ~]$ file

```


### Sintaxis: `chmod`

Esta orden se 


```
[y2k@anaconda ~]$ chmod

```
