# UNIX y LINUX - Guía Práctica.

Comando básicos Unix y Linux.

## INTRO Información

Vamos a ver a continuación la sintaxis y función de algunas órdenes sencillas con objeto de familiarizarnos con la técnica general utilizada en UNIX para invocar programas.


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

### Sintaxis: `uname [ -amnrsv ]`

La orden `uname` se utiliza para obtener información acerca de nuestro sistema UNIX.<br/>
Con ella podemos saber el tipo de máquina que estamos utilizando, la versión del sistema operativo, el tipo de procesador<br/>
etc. Las opciones más comunes son las siguientes:<br/>

* `-a` Visualiza todo acerca de la máquina que estamos utilizando. Es equivalente a todas las opciones que se muestran a continuación.
* `-m` Tipo de hardware utilizado.
* `-n` Nombre de nodo 
* `-r` Actualización del sistema operativo.
* `-s` Nombre del sistema.
* `-v` Versión del sistema operativo. 



```
[y2k@anaconda ~]$ uname -a
FreeBSD anaconda 12.2-STABLE FreeBSD 12.2-STABLE r369150 GENERIC  amd64
[y2k@anaconda ~]$ uname -m
amd64
[y2k@anaconda ~]$ uname -n
anaconda
[y2k@anaconda ~]$ uname -r
12.2-STABLE
[y2k@anaconda ~]$ uname -s
FreeBSD
[y2k@anaconda ~]$ uname -v
FreeBSD 12.2-STABLE r369150 GENERIC 
[y2k@anaconda ~]$

```

### Sintaxis: `passwd [usuario]`

La orden `passwd` se utiliza para modificar nuestra clave de acceso.<br/>
El cambio de palabra clave debe hacerse con frecuencia por razones de seguridad.<br/>
Cuando solicitamos un cambio de clave, `passwd` nos pide siempre nuestra antigua clave de acceso.<br/>
El sistema realiza esta operación de esta forma para comprobar nuestra identidad.<br/>
De esta forma evita que alguien pueda cambiar nuestra contraseña si abandonamos temporalmente el termina.<br/>
De la unica forma que no pide la clave antigua es que el comando sea ejecutado como `root`.


```
[y2k@anaconda ~]$ passwd
Changing local password for y2k
Old Password:
New Password:
Retype New Password:
[y2k@anaconda ~]$

```
Cuado entramos nuestra clave, no mostrará ninguna  información, pero si se esta escribiendo en el sistema.


### Sintaxis: `lpr [-m] [-h] [-#n] archivo(s)`

La orden `lpr` permite enviar archivos a la impresora que haya por defecto para que sean impresos.<br/>
Estos archivos se colocarán en cola de impresión en el orden en que se los pasemos.<br/>
La cola de impresión es una cola que mantiene UNIX, y en ella figuran todos los archivos que deben ser impresos.

Las opciones más comunes de `lpr` son:

 * `-m` (mail) Con esta opción, cuando se termina de imprimir el trabajo. lpr envia correo avisándo que podemos ir a recoger el trabajo. 
 * `-h` Se utiliza para eliminar la cabecera del trabajo que se envia por defecto.
 * `-#n` Sirve para indicar el número de copias que queremos hacer. 


```
[y2k@anaconda ~/EJ]$ lpr archivo.txt
[y2k@anaconda ~/EJ]$ 

```

Si quieres imprimir diferentes copias del mismo archivo tienes que indicarle a lpr las copias que quieres imprimir.


```
[y2k@anaconda ~/EJ]$ lpr -#3 archivo.txt
[y2k@anaconda ~/EJ]$ 

```

Este comando le indica a `lpr` que queremos imprimir 3 copias de el `archivo.txt`


### Sintaxis: `lp [-c] [-m] [-w] [-n] archivo(s)`

La orden `lp` sirve para lo mismo que la orden `lpr`, pero utilizaremos `lp` si nuestro sistema de impresión instalado es el de UNIX SYSTEM V.<br/>
y `lpr` Si es el de Barkeley.

Las opciones más comunes de `lp` son:

 * `-c` (copy) Con esta opción, `lp` hace una copia propia del archivo que queremos imprimir, de esta manera podemos modificarlo aunque se esé imprimirndo.
 * `-m` (mail) Con esta opción, cuando se termina de imprimir el trabajo envia un correo avisándonos que podemos ir a recoger el trabajo impreso.
 * `-w` (write) Esta opción es similar a la opción `-m` pero en este caso informa del final de impresión usando write en vez de mail.
 * `-n` Sirve para indicar el número de copias que queremos realizar.
 
```
[y2k@anaconda ~/EJ]$ lp -n3 archivo.txt
[y2k@anaconda ~/EJ]$ 

```

### Sintaxis: `script [-a] [archivo]`

Esta orden se utiliza para almacenar en un archivo todo lo que el usuario teclee a partir del momento en que sea invocada. a si como todo lo que es enviado a la pantalla<br/>
Para dejar de grabar información en el archivo, tenemos que invocar a la orden exit.<br/>
Si deseamos guardar todo el contenido de una sesión en un archivo denominado `csesion`.


```
[y2k@anaconda ~/EJ]$ script csesion
Script started, output file is csesion
[y2k@anaconda ~/EJ]$ uname -a
FreeBSD anaconda 12.2-STABLE FreeBSD 12.2-STABLE r369150 GENERIC  amd64
[y2k@anaconda ~/EJ]$ uptime
 5:38p. m.  up  5:43, 1 user, load averages: 0,33 0,21 0,13
[y2k@anaconda ~/EJ]$ exit
exit

Script done, output file is csesion
[y2k@anaconda ~/EJ]$ 
```

Ahora veamos que a gurdado nuestro archivo creado csesion.

```
[y2k@anaconda ~/EJ]$ cat csesion 
Script started on Wed Feb 17 17:38:44 2021
[y2k@anaconda ~/EJ]$ uname -a
FreeBSD anaconda 12.2-STABLE FreeBSD 12.2-STABLE r369150 GENERIC  amd64
[y2k@anaconda ~/EJ]$ uptime
 5:38p. m.  up  5:43, 1 user, load averages: 0,33 0,21 0,13
[y2k@anaconda ~/EJ]$ exit
exit

Script done on Wed Feb 17 17:38:52 2021
[y2k@anaconda ~/EJ]$

```


### Sintaxis: `man [sección] [-k] orden`

Todas las órdenes vistas, y las que veremos en los siguientes apartados, están descritas en lo que se conoce como Manual del Programador de UNIX.<br/>
Dicho manual está dividido en secciones.

 * `Sección 1:` Órdenes y programas de aplicación.
 * `Sección 2:` Llamadas al sistema.
 * `Sección 3:` Subrutinas.
 * `Sección 4:` Dispositivos.
 * `Sección 5:` Formatos de archivos.
 * `Sección 6:` Juegos.
 * `Sección 7:` Miscelánea.
 * `Sección 8:` Procedimientos de mantenimiento y administración del sistema.
 
 

```
[y2k@anaconda ~/EJ]$ man clear
TPUT(1)                 FreeBSD General Commands Manual                TPUT(1)

NAME
     tput, clear - terminal capability interface

SYNOPSIS
     tput [-T term] [attribute ...]
     clear

DESCRIPTION
     The tput utility makes terminal-dependent information available to users
     or shell applications.

     The clear utility executes the
           tput clear
     command, ignoring any arguments.

     The only option to tput is:

     -T  The terminal name as specified in the termcap(5) database, for
         example, "vt100" or "xterm".  If not specified, tput retrieves the
         "TERM" variable from the environment unless that too is not
         specified, in which case an error message will be sent to standard
         error and the error status will be 2.

     The tput utility outputs a string for each attribute that is of type
     string; a number for each of type integer.  Otherwise, tput exits 0 if
     the terminal has the capability and 1 if it does not, without further
     action.

     If an attribute is of type string, and takes arguments (e.g. cursor
     movement, the termcap "cm" capability) the arguments are taken from the
     command line immediately following the attribute.

     The following special attributes are available.  The first three use the
     capabilities of the specified terminal, and only work if compatible with
     the utility's terminal.

     clear         Clear the screen (the termcap(5) "cl" capability).
:...skipping...
TPUT(1)                 FreeBSD General Commands Manual                TPUT(1)

NAME
     tput, clear - terminal capability interface

SYNOPSIS
     tput [-T term] [attribute ...]
     clear

DESCRIPTION
     The tput utility makes terminal-dependent information available to users
     or shell applications.

     The clear utility executes the
           tput clear
     command, ignoring any arguments.

     The only option to tput is:

     -T  The terminal name as specified in the termcap(5) database, for
         example, "vt100" or "xterm".  If not specified, tput retrieves the
         "TERM" variable from the environment unless that too is not
         specified, in which case an error message will be sent to standard
         error and the error status will be 2.

     The tput utility outputs a string for each attribute that is of type
     string; a number for each of type integer.  Otherwise, tput exits 0 if
     the terminal has the capability and 1 if it does not, without further
     action.

     If an attribute is of type string, and takes arguments (e.g. cursor
     movement, the termcap "cm" capability) the arguments are taken from the
     command line immediately following the attribute.

     The following special attributes are available.  The first three use the
     capabilities of the specified terminal, and only work if compatible with
     the utility's terminal.

     clear         Clear the screen (the termcap(5) "cl" capability).

     init          Initialize the terminal (the termcap(5) "is" capability).

     reset         Reset the terminal (the termcap(5) "rs" capability).

     longname      Print the descriptive name of the user's terminal type.

ENVIRONMENT
     TERM      The terminal name, if set and -T is not used.

EXIT STATUS
     The exit status of tput is as follows:

[y2k@anaconda ~/EJ]$

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

Vamos a ver seguidamente una serie de órdenes empleadas para manipular archivos y directorios.


### Sintaxis: `ls [-lFaRd] [archivo(s)]`

La orden `ls` se utiliza para listar los archivos contenidos en un determinado directorio.<br/>
Si no le especifica ningún archivo o directorio como argumento en la línea de órdenes, por defecto se visualiza el contenido del directorio de trabajo actual.

```
[y2k@anaconda ~/UNIXyLINUX]$ ls
guia.txt	info.php	intro.html	style.css
[y2k@anaconda ~/UNIXyLINUX]$

```

```
[y2k@anaconda ~/UNIXyLINUX]$ ls -l
total 2
-rw-r--r--  1 y2k  y2k  7 17 feb.  16:30 guia.txt
-rw-r--r--  1 y2k  y2k  7 17 feb.  16:30 info.php
-rw-r--r--  1 y2k  y2k  7 17 feb.  16:30 intro.html
-rw-r--r--  1 y2k  y2k  7 17 feb.  16:30 style.css
[y2k@anaconda ~/UNIXyLINUX]$
```

```
[y2k@anaconda ~/UNIXyLINUX]$ ls -al
total 19
drwxr-xr-x   2 y2k  y2k   6 17 feb.  16:30 .
drwxr-xr-x  20 y2k  y2k  35 17 feb.  16:48 ..
-rw-r--r--   1 y2k  y2k   7 17 feb.  16:30 guia.txt
-rw-r--r--   1 y2k  y2k   7 17 feb.  16:30 info.php
-rw-r--r--   1 y2k  y2k   7 17 feb.  16:30 intro.html
-rw-r--r--   1 y2k  y2k   7 17 feb.  16:30 style.css
[y2k@anaconda ~/UNIXyLINUX]$

```

```
y2k@anaconda ~/UNIXyLINUX]$ ls -ld /etc
drwxr-xr-x  25 root  wheel  111 17 feb.  17:06 /etc
[y2k@anaconda ~/UNIXyLINUX]$

```
### Sintaxis: `pwd`

Esta orden muestra nuestro directorio de trabajo actual, tal y como indican sus iniciales (Print Working Directory)<br/>
en forma de camino absoluto. Cuando nos movemos mucho por el árbol de directorios, esta orden es de suma utilidad.


```
[y2k@anaconda ~/UNIXyLINUX]$ pwd
/home/y2k/UNIXyLINUX
[y2k@anaconda ~/UNIXyLINUX]$

```

### Sintaxis: `cd [directorio]`

La orden `cd` (Change Directory) se emplea para poder movernos de unos directorios a otros.<br/>
El camino que le pasamos como argumento a cd, tal y como se muestra en la sintaxis.<br/>
Puede ser un nombre de camino absoluto o relativo.<br/>
Si a `cd` no le indicamos ninguna ruta, volvera al directorio `HOME` del usuario.


```
[y2k@anaconda ~]$ cd /usr/ports/irc/undernet-ircu/
[y2k@anaconda /usr/ports/irc/undernet-ircu]$ cd
[y2k@anaconda ~]$

```

```
[y2k@anaconda /usr/ports/irc/undernet-ircu]$ cd ..
[y2k@anaconda /usr/ports/irc]$

```

### Sintaxis: `mkdir` y `rmdir`

El árbol de directorios de UNIX nos es estático, sino que los usuarios tienen la posibilida de crear sys propios directorios para distribuir mjor su info.<br/>
Los nuevos directorios no pueden ser creados en cualquier nodo del árbol.<br/>
La mayoría de las veces, cada usuario sólo podrá crear nuevos directorios a partir de su directorio de inicio o HOME.<br/>
Des esta manera cada persona personaliza su información sin perjudicar al resto. mkdir (Make Directory).

```
[y2k@anaconda ~]$ mkdir luis
[y2k@anaconda ~]$
```
Ahora con el directorio o carpeta `luis` creada, podemos entrar a ella con `cd luis`

```
[y2k@anaconda ~]$ cd luis
[y2k@anaconda ~/luis]$
```

Si queremos eliminar el directorio `luis` tendremos que salir de el con `cd ..` o `cd`


```
[y2k@anaconda ~/luis]$ cd ..
[y2k@anaconda ~]$ rmdir luis
[y2k@anaconda ~]$ cd luis
```

Si intentamos entrar al directorio borrado no tendremos acceso y el terminal nos indicara que ese directorio no esta creado.

```
[y2k@anaconda ~]$ cd luis
-bash: cd: luis: No such file or directory
[y2k@anaconda ~]$
```

### Sintaxis: `cat [archivo(s)]`

La orden `cat` sirve para visualizar el contenido de archivos de texto (ASCII) por la pantalla.<br/>
Si a `cat` no le pasamos como argumento ningún archivo de texto, entonces leerá caracteres de la entrada estándar (teclado)<br/>
hasta que pulsemos CTRL-D (^d). Una vez hecho esto, visualizará lo que acabamos de escribir.


```
[y2k@anaconda ~/EJ]$ cat archivo.txt 

EJemplo de comando CAT
Vemos como muestra la info del archivo.txt indicado!
[y2k@anaconda ~/EJ]$ 

```

```
[y2k@anaconda ~/EJ]$ cat prog.c 
#include <stdio.h>

main (int argc, char *argv[])
{
int x;
for (x = 0; x < argc; x++)
puts(argv[x]);
}
[y2k@anaconda ~/EJ]$
```

### Sintaxis: `more [archivo(s)]`

La orden `more` imprime por pantalla el contenido del archivo de textoque le pasemos como argumento.<br/>
En este caso y a diferencia de lo que ocurría con `cat` que mostraba todo el archivo de forma continua, la visualización se hace pantalla a pantalla.


```
y2k@anaconda ~/EJ]$ more prog.c 
/************
*
* Programa para EJ de IRCAYUDA
*
* Esto es para mostrar la funcion del comando more.
*
* En un archivo extenso y que no se quiere imprimir todo.
*
*
*
* Veamos como el comando more interpreta este archivo.
*
*
* Code by y2k
*
**************/

--More--(72%)

```
Vemos como indica que el archivo se visualiza en un 72%. Si queremos ver más info de dicho archivo.<br/>
Utilizaremos la tecla INTRO (ENTER).


### Sintaxis: `head [-N] archivo(s)` y `tail [-N] archivo(s)` 

Las órdenes `head` y `tail` se pueden utilizar para vsualizar las primeras `N` líneas o últimas `N` líneas de un archivo de texto, respectivamente.<br/>
Esto puede ser útil, porque muchas veces no necesitamos visualizar el archivo de texto por completom sino que nos basta con algunas líneas.


```
[y2k@anaconda ~/EJ]$ head -5 prog.c 
/************
*
* Programa para EJ de IRCAYUDA
*
* Esto es para mostrar la funcion del comando more.
[y2k@anaconda ~/EJ]$

```

Vemos como `head` muestra las primeras 5 líneas del archivo indicado.

```
[y2k@anaconda ~/EJ]$ tail -4 prog.c 
int x;
for (x = 0; x < argc; x++)
puts(argv[x]);
}
[y2k@anaconda ~/EJ]$
```
Vemos como `tail` muestra las últimas 4 líneas del archivo indicado.


### Sintaxis: `od [ -bcdfox ] [archivo(s)]`

La orden `od` (Volcado octal, Octal dump) se utiliza para realizar un volcado, en octal del contenido de un archivo.<br/>
Si a `od` no se les especifica ningún archivo, leerá de la entrada extándar hasta detectar el final de archivo `Ctrl-d`<br/>
y despues visualiza lo escrito en octal.

```
[y2k@anaconda ~/EJ]$ od -c prog.c 
0000000    /   *   *   *   *   *   *   *   *   *   *   *   *  \n   *  \n
0000020    *       P   r   o   g   r   a   m   a       p   a   r   a    
0000040    E   J       d   e       I   R   C   A   Y   U   D   A  \n   *
0000060   \n   *       E   s   t   o       e   s       p   a   r   a    
0000100    m   o   s   t   r   a   r       l   a       f   u   n   c   i
0000120    o   n       d   e   l       c   o   m   a   n   d   o       m
0000140    o   r   e   .  \n   *  \n   *       E   n       u   n       a
0000160    r   c   h   i   v   o       e   x   t   e   n   s   o       y
0000200        q   u   e       n   o       s   e       q   u   i   e   r
0000220    e       i   m   p   r   i   m   i   r       t   o   d   o   .
0000240   \n   *  \n   *  \n   *  \n   *       V   e   a   m   o   s    
0000260    c   o   m   o       e   l       c   o   m   a   n   d   o    
0000300    m   o   r   e       i   n   t   e   r   p   r   e   t   a    
0000320    e   s   t   e       a   r   c   h   i   v   o   .  \n   *  \n
0000340    *  \n   *       C   o   d   e       b   y       y   2   k  \n
0000360    *  \n   *   *   *   *   *   *   *   *   *   *   *   *   *   *
0000400    /  \n  \n  \n  \n   #   i   n   c   l   u   d   e       <   s
0000420    t   d   i   o   .   h   >  \n  \n   m   a   i   n       (   i
0000440    n   t       a   r   g   c   ,       c   h   a   r       *   a
0000460    r   g   v   [   ]   )  \n   {  \n   i   n   t       x   ;  \n
0000500    f   o   r       (   x       =       0   ;       x       <    
0000520    a   r   g   c   ;       x   +   +   )  \n   p   u   t   s   (
0000540    a   r   g   v   [   x   ]   )   ;  \n   }  \n                
0000554
[y2k@anaconda ~/EJ]$

```

La orden `od` acepta diversas opciones, las  mas comunes son:

 * `-b` Visualiza los bytes como números en código octal.
 * `-c` Visualiza los bytes como caracteres.
 * `-d` Visualiza las palabras (16 bits) como números decimales sin signo.
 * `-f` Visualiza el contenido del archivo como números de forma flotante de (32 bits)
 * `-o` Visualiza las palabras como números en octal sin signo (opción por defecto).
 * `-x` Visualiza las palabras en código hexadecimal.
 


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
