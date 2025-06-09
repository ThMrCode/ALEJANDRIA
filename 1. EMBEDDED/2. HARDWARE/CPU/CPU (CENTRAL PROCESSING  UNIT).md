Modulo que ejecuta instrucciones, una a la vez, su catalogo de instrucciones queda definido por su arquitectura, estas instrucciones tienen representación binaria.

---

Cuando se diseña una CPU nunca se produce, pues siempre lleva mas componentes acoplados según su destino de aplicación. Las empresas compran el diseño de la CPU, y a partir de ella, pueden diseñar

- **MCU (MICROCONTROLLING UNIT)**: CPU + memorias + periféricos
    
- **MPU (MICROPROCESSING UNIT)**: CPU + mínimo soporte
    
- **CPU (GENERAL PURPOSE)**: CPU para computadoras y servidores

En la familia ARM, el propósito de los CPUS se clasifica en

- **ARM CORTEX-M**: MCU
    
- **ARM CORTEX-A**: MPU

---

Toda CPU es en si un circuito digital, con terminales de entrada y salida, sus partes están completamente aisladas de los periféricos y demás externos, la única conexión entre el CPU es la interfaz BUS en sus terminales.

### CPU (PARTS)

- **ALU (ARICMETIC LOGIC UNIT)**: realiza las operaciones matemáticas y lógicas.
    
- **Unidad de control**: interpreta las instrucciones y controla el flujo.
    
- **Registros**: pequeñas memorias dentro del CPU para guardar datos temporales.

### CPU (TERMINALS)
- **Interfaz BUS**: Encargada de la conexión entre el CPU y externos, memoria, periféricos.
 