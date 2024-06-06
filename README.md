# ELEVADOR-3-NIVELES-CON-USART


El código configura y controla un elevador de tres niveles usando periféricos GPIO y USART del microcontrolador STM32. El elevador puede ser llamado a través de un teclado matricial y muestra su posición actual y destino cuando es precionada la llamada, en un display de 7 segmentos.

**Variables Globales**
piso_actual: ```uint8_t piso_actual = 0;```
Guarda el piso actual en el que se encuentra el elevador.
```escrito: uint8_t escrito = 0;```
Guarda el último valor mostrado en el display de 7 segmentos.
```val: uint8_t val = 0;```
Variable temporal usada para diversas operaciones.

**Funciones**
```main:``` Función principal que configura el sistema y entra en un bucle infinito para manejar la lógica del elevador.

```init:``` Configura los puertos GPIO para los displays y otros componentes del elevador.

```keyboard_config:```     Configura los pines GPIO para el teclado y los sensores infrarrojos.

```key_pressed:```   Lógica para detectar y manejar las pulsaciones de teclas, controla el movimiento del elevador y muestra la posición en el display.

```print_bcd_7_segment_decoder_CC:```     Muestra un número en el display de 7 segmentos.

```delayMs:```    Implementa un retraso en milisegundos (no definida en el código proporcionado, pero generalmente está implementada en otro lugar.

**Control del Display de 7 Segmentos**
La función ```print_bcd_7_segment_decoder_CC``` se encarga de encender los segmentos correctos para mostrar números del 0 al 9 y letras A, b, C, d. Utiliza el registro ODR (Output Data Register) de GPIOB para controlar los segmentos del display.

**Control del Motor del Elevador**
Subir: Se activa el pin PC10.
Bajar: Se activa el pin PC11.

**Comunicación Serial (USART2)**
Configura los pines PA2 y PA3 para transmisión (TX) y recepción (RX).
Inicializa el USART2 con una velocidad de 9600 baudios.
Funciones ```USART2_write```, ```USART2_putstring```, ```USART2_putstring_E``` para enviar datos por el puerto serial.

**Explicación de la Configuración de GPIO**
Pines GPIO: Configurados para diferentes funciones:

PB2, PB3, PB4, PB6, PB7, PB8, PB9: Configurados para controlar los segmentos del display de 7 segmentos.

PA0 y PA1: Configurados para habilitar los displays comunes.

PC5, PC6, PC8, PC9: Configurados como entradas para las filas del teclado.

PC10 y PC11: Configurados para controlar el motor del elevador (subir y bajar).

PC1: Configurado como entrada para sensor infrarojo, y este detiene el elevador en el nivel 1

PC2: Configurado como entrada para sensor infrarojo, y este detiene el elevador en el nivel 2

PC3: Configurado como entrada para sensor infrarojo, y este detiene el elevador en el nivel 3


En conclusion: 
tenemos el elevador con 3 niveles, por cada nivel tenemos un sensor que al determinar el boton seleccionado es donde tendra el paro de la cabina, todo es controlado por un teclado matricial de 4x4, y un led que me indica el boton precionado y nivel destino, tambien tenemos la comunicacion serial con la consola de arduino, con la que podemos observar los mensajes enviados desde una comunicacion serial USART2.
para el cambio de giro tenemos un drive L298 que es practicamente un puente H que nos permite el control de direccion para un motor DC normal, el cual el drive funciona y controla todo con 5v externos desde una fuente 
![captura elevador ](https://github.com/ByronRC89/ELEVADOR-3-NIVELES-CON-USART/assets/159856194/c549aec9-89e8-4ed9-b088-c5bd77eee7b4)

https://www.youtube.com/watch?v=oT3lck19TvE


