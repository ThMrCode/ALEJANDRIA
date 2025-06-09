Es el Sistema Maestro del Sistema Operativo. Debemos recordar que un procesador es un sistema lógico secuencial, es decir, ejecuta instrucciones en secuencia.

---

Las instrucciones tienen forma de bytes, por ejemplo:

```
mov rax, 0x123448 
C7 C0 34 12 00 00
```

El procesador va iterando sobre la memoria, lee un bloque y ejecuta su instrucción, y luego lee el siguiente y hace lo mismo, y así sucesivamente. 

Para que sea posible entonces ejecutar las distintas tareas que demanda un sistema operativo, es necesario orden, sincronización, e interactividad, una manera de comunicar las tareas lógicas con el hardware, una manera de comunicar las tareas con otras tareas, etc. Y, en esencia, ello es lo que hace un kernel.

---

## STACK PROCESSES
Para solucionar el problema del multitasking, orden y sincronización, el kernel se ejecuta como un bucle permanente que va realizando una cola de tareas, los procesos, cada proceso tiene un identificador asignado, y un quantum de tiempo asignado para su ejecución, si no se termina en dicho quantum de tiempo, como suele suceder, se guarda el estado de la memoria del proceso, y se sigue con la cola haciendo lo mismo para cada proceso hasta su siguiente iteración, seudocódigo adjunto.

```
stack processes;
while(true) {
	for process in processes {
		executeQuantum(process);
		saveStateMemory(process);
	}
}
```

## COMUNICATION PROCESSES
Para el problema de la interactividad se definen protocolos de comunicación entre los procesos y el kernel, si el proceso desea comunicarse con otros, o si desea comunicarse con el hardware, el no hará directamente dicha comunicación, sino mas bien, se comunicara con el kernel mediante las System Calls, y el kernel se encargara del resto, seudocódigo adjunto.

```
kernelCall("Hi Kernel I need to show something in the Screen, please do it")
```

