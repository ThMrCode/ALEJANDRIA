Una vez conectado el lidar a nuestro dispositivo, es necesario darle permisos de puerto, para ello primero ubicamos a que puerto esta conectado, revisamos todos los puertos seriales.

```
ls /dev/tty*
```

Tras encontrar nuestro puerto ttyUSBX, usualmente ttyUSB0, leemos sus permisos

```
ls -l /dev/ttyUSB0
```

Agregamos nuestro usuario al grupo dialout, grupo con permisos de acceso a los puertos seriales.

```
sudo usermod -aG dialout $USER
```

Nuestro usuario ha sido modificado así que volvemos a iniciar sesión.

```
su - $USER
```

Verificamos nuestros permisos.

```
ls -la /dev | grep ttyUSB0
```

---

## VIRTUAL BOX
Si nuestro proyecto esta en VirtualBox, debemos entrar a la configuracion de nuestra maquina virtual, quitar los filtros USB si es que existen, y seleccionar Controlador USB 3.0

![[LIDAR_VIRTUALBOX_1.png]]

Luego iniciamos la maquina virtual, y recién entonces conectamos el lidar, y lo añadimos a los dispositivos USB (Silicon Labs).

![[LIDAR_VIRTUALBOX_2.png]]

Otro problema que puede dar VirtualBox es con la interfaz grafica rviz, en caso no funcione, revisar.

```
echo $DISPLAY
```

Si se encuentra vacío añadirlo manualmente.

```
export DISPLAY=:0
```