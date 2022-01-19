 Energia = potencia * tiempo
 
 
    E = P.T
    
 
    
    
 Potencia = intensidad * voltaje
 
 
     P = I.V
     
     
 Intensidad = voltaje divido resistencia
 
 
    I = V/R
    

# MOLINILLO MOTORIZADO



### RESUMEN

I did this project with ANDREE. IN this project we made a circuit in which we connected a battery 


with motor because the arduino board only doesn't has enough power to run this circuit 


we also connected a button by which we can turn on and off the motor.The code we used to


program this circuit is given below.




### IMAGEN



![](https://github.com/Samael696/arduino/blob/main/IMG_20220119_101702.jpg?raw=true)




### CODIGO


``` C++
const int switchPin = 2;

  const int motorPin = 9;

  int switchState = 0;
  
  void setup(){

    pinMode(motorPin, OUTPUT);
    
     pinMode(switchPin, INPUT);
  
  }
  void loop(){

   switchState = digitalRead(switchPin);

   if (switchState == HIGH){
    digitalWrite(motorPin, HIGH);
    
   
  }
else {

  digitalWrite(motorPin, LOW);
}
}
```
