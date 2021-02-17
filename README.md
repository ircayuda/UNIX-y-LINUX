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

La orden `date` informa sobre la fecha y la hora actuales. Para ello, `date` consulta previamente el reloj del hardware del sistema, el cual incrementa su valor a iontervalos regulares de tiempo.<br/>
Estos intervalos suelen ser pequeños, de manera que pueda obternerse bastante resolución.

```
[y2k@anaconda ~]$ date --help
date: illegal option -- -
usage: date [-jnRu] [-d dst] [-r seconds|file] [-t west] [-v[+|-]val[ymwdHMS]]
            [-I[date | hours | minutes | seconds]]
            [-f fmt date | [[[[[cc]yy]mm]dd]HH]MM[.ss]] [+format]
[y2k@anaconda ~]$

```

```
[y2k@anaconda ~]$ date +"Son las %r del %d de %h de %y"
Son las 04:37:04 p. m. del 17 de feb. de 21
[y2k@anaconda ~]$

```

Son operadores asociados a `%` son:
    * `r` Hora en formato AM-PM
    * `d` Día del mes.
    * `m` Mes
    * `y` Año
    * `w` Día de semana
    * `H` Hora
    * `M` Minutos
    * `S` Segundos
    
De todas formas, la manera más común de utilizar la orden es la siguiente:


```
[y2k@anaconda ~]$ date
miércoles, 17 de febrero de 2021, 16:35:39 CET
[y2k@anaconda ~]$

```


### Sintaxis: `echo` cadena de caracteres

La orden `echo` repide todo lo que le pasemos como parámetro.<br/>
Esta orden se utiliza mucho dentro de los programas de shell que veremos más adelante, así como para visualizar las variables del intérprete de órdenes.<br/>
Las variables comentadas las utiliza el propio shell para almacenar valores de configuración e información.


```
[y2k@anaconda ~]$ echo Esto es para la el canal IRCAyuda @ Undernet.org
Esto es para la el canal IRCAyuda @ Undernet.org
[y2k@anaconda ~]$

```

```
[y2k@anaconda ~]$ echo $TERM
xterm-256color
[y2k@anaconda ~]$

```

```
[y2k@anaconda ~/EJ]$ echo "Crear un archivo con echo" > archivo.txt ; ls -a
.		..		archivo.txt
[y2k@anaconda ~/EJ]$

```
### Sintaxis: `banner` cadena

La orden `banner` se utiliza para visualizar en letras grandes la cadena que le pasemos como parámetro.<br/>
Inicialmente, se desarrolló para etiquetar la salida de las impresoras de línea.<br/>
De esta manera, si varias personas mandan imprimir distintos trabajos, pueden saber dónde<br/>
comienza el suyo por el hecho de tener una cabecera son su nombre que permitirá distinguirlo de los demás.

```
[y2k@anaconda ~/EJ]$ banner -w30 hola
       #                   #
       #####################
       #####################
                  #
                  ##
       #############
       ############
       #
           #### 
         #########
        ##       ##
       #           #
       #          ##
        ##       ##
         #########
           #### 
       #                   #
       #####################
       #####################
          ##
        ######  ## 
       ##    ## ### 
        #    #     #
        ##  ##   ## 
       ########### 
       ##
        
[y2k@anaconda ~/EJ]$ 

```

```
[y2k@anaconda ~]$ banner --help
banner: illegal option -- -
usage: banner [-d] [-t] [-w width] message ...
[y2k@anaconda ~]$ 
```


### Sintaxis: `cal [mes] [año]`

Sin ningún parámetro, `cal` visualiza el calendario correspondiente al mes actual.<br/>
Si le pasamos como parámetro un año, por ej. 2000. mostrará el calendario completo correspondiente al año en custión.


```
[y2k@anaconda ~]$ cal
    Febrero 2021      
do lu ma mi ju vi sá  
    1  2  3  4  5  6  
 7  8  9 10 11 12 13  
14 15 16 17 18 19 20  
21 22 23 24 25 26 27  
28                    
                      
[y2k@anaconda ~]$

```

```
[y2k@anaconda ~]$ cal 2000
                            2000
       Enero                Febrero                Marzo          
do lu ma mi ju vi sá  do lu ma mi ju vi sá  do lu ma mi ju vi sá  
                   1         1  2  3  4  5            1  2  3  4  
 2  3  4  5  6  7  8   6  7  8  9 10 11 12   5  6  7  8  9 10 11  
 9 10 11 12 13 14 15  13 14 15 16 17 18 19  12 13 14 15 16 17 18  
16 17 18 19 20 21 22  20 21 22 23 24 25 26  19 20 21 22 23 24 25  
23 24 25 26 27 28 29  27 28 29              26 27 28 29 30 31     
30 31                                                             

       Abril                  Mayo                 Junio          
do lu ma mi ju vi sá  do lu ma mi ju vi sá  do lu ma mi ju vi sá  
                   1      1  2  3  4  5  6               1  2  3  
 2  3  4  5  6  7  8   7  8  9 10 11 12 13   4  5  6  7  8  9 10  
 9 10 11 12 13 14 15  14 15 16 17 18 19 20  11 12 13 14 15 16 17  
16 17 18 19 20 21 22  21 22 23 24 25 26 27  18 19 20 21 22 23 24  
23 24 25 26 27 28 29  28 29 30 31           25 26 27 28 29 30     
30                                                                

       Julio                 Agosto              Septiembre       
do lu ma mi ju vi sá  do lu ma mi ju vi sá  do lu ma mi ju vi sá  
                   1         1  2  3  4  5                  1  2  
 2  3  4  5  6  7  8   6  7  8  9 10 11 12   3  4  5  6  7  8  9  
 9 10 11 12 13 14 15  13 14 15 16 17 18 19  10 11 12 13 14 15 16  
16 17 18 19 20 21 22  20 21 22 23 24 25 26  17 18 19 20 21 22 23  
23 24 25 26 27 28 29  27 28 29 30 31        24 25 26 27 28 29 30  
30 31                                                             

      Octubre              Noviembre             Diciembre        
do lu ma mi ju vi sá  do lu ma mi ju vi sá  do lu ma mi ju vi sá  
 1  2  3  4  5  6  7            1  2  3  4                  1  2  
 8  9 10 11 12 13 14   5  6  7  8  9 10 11   3  4  5  6  7  8  9  
15 16 17 18 19 20 21  12 13 14 15 16 17 18  10 11 12 13 14 15 16  
22 23 24 25 26 27 28  19 20 21 22 23 24 25  17 18 19 20 21 22 23  
29 30 31              26 27 28 29 30        24 25 26 27 28 29 30  
                                            31                    
[y2k@anaconda ~]$

```

```
[y2k@anaconda ~]$ cal 2 2000
    Febrero 2000      
do lu ma mi ju vi sá  
       1  2  3  4  5  
 6  7  8  9 10 11 12  
13 14 15 16 17 18 19  
20 21 22 23 24 25 26  
27 28 29              
                      
[y2k@anaconda ~]$

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


### Sintaxis: `umask`

Esta orden se 


```
[y2k@anaconda ~]$ umask

```


### Sintaxis: `which`

Esta orden se 


```
[y2k@anaconda ~]$ which

```


### Sintaxis: `whereis`

Esta orden se 


```
[y2k@anaconda ~]$ whereis

```


### Sintaxis: `id`

Esta orden se 


```
[y2k@anaconda ~]$ id

```


### Sintaxis: `su`

Esta orden se 


```
[y2k@anaconda ~]$ su

```


### Sintaxis: `newgrp`

Esta orden se 


```
[y2k@anaconda ~]$ newgrp

```


### Sintaxis: `mdir`

Esta orden se 


```
[y2k@anaconda ~]$ mdir

```


### Sintaxis: `mattrib`

Esta orden se 


```
[y2k@anaconda ~]$ mattrib

```


### Sintaxis: `mmf`

Esta orden se 


```
[y2k@anaconda ~]$ mmd

```


### Sintaxis: `mcopy`

Esta orden se 


```
[y2k@anaconda ~]$ mcopy

```


### Sintaxis: `mmove`

Esta orden se 


```
[y2k@anaconda ~]$ mmove

```


### Sintaxis: `mrd`

Esta orden se 


```
[y2k@anaconda ~]$ mrd

```


### Sintaxis: `mcd`

Esta orden se 


```
[y2k@anaconda ~]$ mcd

```


### Sintaxis: `mdel`

Esta orden se 


```
[y2k@anaconda ~]$ mdel

```


### Sintaxis: `mformat`

Esta orden se 


```
[y2k@anaconda ~]$ mformat

```


### Sintaxis: `mren`

Esta orden se 


```
[y2k@anaconda ~]$ mren

```


### Sintaxis: `mtype`

Esta orden se 


```
[y2k@anaconda ~]$ mtype

```
