## Titulos 




## Código

Aquí el código entero [Enlace](https://github.com/ismamera/ARDUINO/blob/main/molinillo.ino)

https://github.com/ismamera/ARDUINO/blob/main/molinillo.ino



```C++

const int switchPin = 2;
const int motorPin = 9;
int switchState = 0;
void setup(){
pinMode(motorPin, OUTPUT);
pinMode(switchPin, INPUT);
}
void loop(){
  switchState = digitalRead(switchPin);
  if (switchState == HIGH) {
    digitalWrite(motorPin, HIGH);
  }
  else {
  
  }
}
```


hoy en classe ha tocado hacer un proyecto cn el arduino el cual se trataaba

de conectar una bateria y un molinillo y hacerlo funcionar mediante un codigo de arduino.

He tenido un roblema y es q mi ordenador no podia hacverlo funionar por un error q yo desconozco 

Evuelto hacer otra prueba cn el arduino y emos detectado un fallo el cuial era q aunq le dieramos 

al boton o no le dieramos el motor del molinillo se activaba solo y enpezaba ha funcionar 

emos abierto la prueba para ver si era el boton si funcionaba y emos visto q si funcionaba pero a la hora de la verdad no iba nunca 

y mientras probabamos ha echo algun cortocircuito y no sabiamos porq era 


















































