# UNIX y LINUX - Guía Práctica.

Comando básicos Unix y Linux.

## INTRO Información

<p>Vamos a ver a continuación la sintaxis y función de algunas órdenes sencillas con obheto de familiarizarnos con la técnica general utilizada en UNIX para invocar programas.</p>


### Algunas órdenes para comenzar.

<p>Cuando deseamos finalizar una sesión de trabajo, deberemos informar de ello al sistema. <br/>La orden <b>exit</b> se emplea para avisar al sistema de nuestro fin de sesión.<br/>
<b>Sintaxis: exit</b></p>

```
[y2k@anaconda ~]$ exit
cerrar sesión
root@anaconda:~ #
```

### Sintaxis: `who (am i)`
<p>La orden o comando `who` nos informa acerca de quién o quiénes están conectados actualmente al sistema. También muestra información,<br/>
en la segunda columna, relativa al terminal asociado a cada usuario, y por último, en la columna tercera, la fecha y hora en la que el usuario entró en sesión.
</p>

```
root@anaconda:~ # who
y2k              pts/2        Feb 17 13:27 (192.168.1.200)
root@anaconda:~ # 
```


### Sintaxis: `mail usuario(s)`
<p> El sistema UNIX/LINUX proporciona un mecanismo de correo electrónico o e-mail que permite envíar mensajes de unos usuarios a otros.<br/>
Para enviar un mensaje no es necesario que el usuario destinatario esté conectado en ese momento.<br/>
Ya que toda la correspondencia será depositada en su buzón.
</p>

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
<p>La orden o comando `write` Se utiliza para comunicarnos con otros usuarios que estén en ese momento conectados a nuestro mismo sistema.<br/>
(write) NO funciona para usuarios en sistemas diferentes. `En este EJ. tenemos usuario: luis \ usuario: y2k`<br/>
El usuario: luis, escribira al usuario y2k. Para que vea el mensaje en el terminal.
</p>

```
[luis@anaconda ~]$ write y2k 
Hola y2k, soy Luis! :)
```

<p>
El usuario: `luis`, envio un mensaje al usuario `y2k`. En tiempo real. Ahora veamos como veria el usuario. y2k. el mensaje.
</p>


```
[y2k@anaconda ~]$ ~
Message from y2k@anaconda on pts/1 at 13:50 ...
Hola y2k, soy Luis! :)
```

