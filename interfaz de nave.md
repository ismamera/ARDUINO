
 # interfaz de nave
 
 
Resumen

El LED verde permanecera encendido hasta que pulses un botón.Cuando el Arduino reciba una señal del botón,la luz verde se apagara y las otras 2 luces empezarán a parpadear.
Introducción teórica

    construir circuito
    programar circuito
    variaciones

➙ ordenador:
input:

    ratón
    teclado
    micro
    webcam

output:

    altavoces
    monitor

➙ teléfono:

    entradas: micrófono, cámaras, pantallas táctil, giroscópio, acelerómetro.

    salidas: pantalla, altavoces, linterna, motor vibración

ARDUINO - 18 pines
Proceso de montaje

Programación - pág 34-35 Resistencias - página 41. 220 - azules

SwitchState = 0; SwitchState es una variable es de tipo "INT" que signifíca que es un número entero.

imagen
Errores:

La mayor parte de los errores de programación fueron por escribir de manera erronea una o dos palabras en el arduino. Los errores del circuito fueron por colocar cables de manera incorrecta.
Variaciones
Añadir botón por hardware

Vamos a añadir un botón al pin 3 de tal forma que solo cuando se pulse el led 3 se encienda. El resto del proyecto ( hardware y software ) es el mismo.

Antes LED 220

Pin 3-----LED/-----ww ---- GND

Después

PIN 3-----LED/----- WW---- GND
































