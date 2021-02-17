# UNIX y LINUX - Guía Práctica.

Comando básicos Unix y Linux.

## INTRO Información

<p>Vamos a ver a continuación la sintaxis y función de algunas órdenes sencillas con obheto de familiarizarnos con la técnica general utilizada en UNIX para invocar programas.</p>


### Algunas órdenes para comenzar.

<p>Cuando deseamos finalizar una sesión de trabajo, deberemos informar de ello al sistema. <br/>La orden <strong>exit</strong> se emplea para avisar al sistema de nuestro fin de sesión.<br/>
<strong>Sintaxis: exit</strong></p>

```
[y2k@anaconda ~]$ exit
cerrar sesión
root@anaconda:~ #
```

### Sintaxis: who (am i)
<p>La orden o comando <strong>who</strong> nos informa acerca de quién o quiénes están conectados actualmente al sistema. También muestra información,<br/>
en la segunda columna, relativa al terminal asociado a cada usuario, y por último, en la columna tercera, la fecha y hora en la que el usuario entró en sesión.
</p>

```
root@anaconda:~ # who
y2k              pts/2        Feb 17 13:27 (192.168.1.200)
root@anaconda:~ # 
```
