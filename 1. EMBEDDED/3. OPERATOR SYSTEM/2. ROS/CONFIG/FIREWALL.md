Windows nunca permitirá comunicación de otros dispositivos al nuestro en redes publicas, para ello debemos establecer la red de comunicación como red privada en el firewall de Windows, configuración de redes.

![[FIREWALL_1.png]]

![[FIREWALL_2.png]]

Además el firewall no permitirá la comunicación por nuestros puertos a menos que creemos reglas que la permitan. 

Nos dirigimos al firewall de Windows.

![[FIREWALL_4.png]]

Configuración Avanzada.

![[FIREWALL_5.png]]

En Reglas de entrada cliquear nueva regla.

![[FIREWALL_6.png]]

Para la regla que permita el ping entre dispositivos seleccionar 
- Tipo: Personalizada
- Programa: Todos los Programas
- Protocolo y Puertos: Tipo de Protocolo ICMPv4
- Ámbito: Cualquier Dirección IP
- Acción: Permitir la Conexión
- Perfil: Dominio Privado y Publico
- Nombre: PING_REGLA 
- Clic en Finalizar

Para la regla que permita el ros entre dispositivos seleccionar 
- Tipo: Puerto
- Protocolo y Puertos: TCP, Puertos Locales Específicos: 11311, 11411
- Acción: Permitir la Conexión
- Perfil: Dominio Privado y Publico
- Nombre: ROS_REGLA 
- Clic en Finalizar

![[FIREWALL_3.png]]
