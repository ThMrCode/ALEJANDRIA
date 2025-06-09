ROS nace de la necesidad de orden, sincronización e interactividad, y su característica multimáquina evita la necesidad de protocolos de comunicación entre dispositivos, usando un único sistema ROS universal.

---

## CONFIGURACION WIFI
Sea en un único dispositivo o en varios, se debe tener un único roscore, es decir, debemos elegir uno de nuestros dispositivos como dispositivo maestro para ejecutar en el, el roscore.

Una vez hayamos elegido nuestro dispositivo maestro, debemos conectarlo a una red wifi, apuntar su ip, abrir la terminal en el, y ejecutar los comandos.

```
export ROS_MASTER_URI=http://<ip-master>:11311 
export ROS_HOSTNAME=$(hostname)
```

Con ello ya esta configurado para ROS MULTIMAQUINA, entonces ejecutamos roscore.

```
roscore
```

Si queremos agregar un dispositivo, los conectamos a la misma red wifi, si algún dispositivo trabaja con Windows o maquinas virtuales hosteadas por Windows, es necesario configurar la red wifi como privada, [[FIREWALL]]. Si además estamos en una maquina virtual, es necesario configurar el [[ADAPTADOR PUENTE]].

Una vez conectado a la red, es necesario ejecutar los mismos comandos

```
export ROS_MASTER_URI=http://<ip-master>:11311 
export ROS_HOSTNAME=$(hostname)
```

Con ello ya estará sincronizado el ROS MULTIMAQUINA, recordar que todos los dispositivos deben tener la misma versión de ROS.

