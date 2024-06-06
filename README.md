# ELEVADOR-3-NIVELES-CON-USART


El código configura y controla un elevador de tres niveles usando periféricos GPIO y USART del microcontrolador STM32. El elevador puede ser llamado a través de un teclado matricial y muestra su posición actual y destino cuando es precionada la llamada, en un display de 7 segmentos.

Variables Globales
piso_actual: ```uint8_t piso_actual = 0;```
Guarda el piso actual en el que se encuentra el elevador.
```escrito: uint8_t escrito = 0;```
Guarda el último valor mostrado en el display de 7 segmentos.
```val: uint8_t val = 0;```
Variable temporal usada para diversas operaciones.
