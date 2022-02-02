#include <LiquidCrystal.h>                  //necesaria para el display LCD
#include "DHT.h"                            //necesaria para el sensor DHT11 y DHT22

//Definimos las I/O del display lcd
const int LCD_rs = 2, LCD_en = 3, LCD_d4 = 4, LCD_d5 = 5, LCD_d6 = 6, LCD_d7 = 7;

//El display 2004 (20x4) se llamará lcd
LiquidCrystal lcd(LCD_rs, LCD_en, LCD_d4, LCD_d5, LCD_d6, LCD_d7);

//Constantes
const int sensor_pin_ky015 = 10;            //pin por donde entra la señal del KY-015
#define DHT1 DHT11                          //define el tipo de DHT a DHT11 para el KY-015
const int sensor_pin_dht22 = 11;            //pin por donde entra la señal del DHT22
#define DHT2 DHT22                          //define el tipo de DHT a DHT22 para el DHT22

//declaro variables del programa
float humedad_ky015;                        //aqui almacenamos la humedad leida del ky-015
float temperatura_ky015;                    //aqui almacenamos la temperatura leida del ky-015
float humedad_dht22;                        //aqui almacenamos la humedad leida del dht22
float temperatura_dht22;                    //aqui almacenamos la temperatura leida del dht22

DHT dht11(sensor_pin_ky015, DHT11);         //inicializamos el sensor KY-015 y le llamamos dht11
DHT dht22(sensor_pin_dht22, DHT22);         //inicializamos el sensor DHT22 y le llamamos dht22

void setup() {
  //Configuramos el pueto serie del Arduino Uno
  Serial.begin(9600);                       //Iniciamos la trasmision a 9600 baudios
  
  //Configuramos el lcd
  lcd.begin(20, 4);                         //informamos del tamaño del display

  //Presentamos mensajes de bienvenida
  lcd.print("   ARDUINO  FACIL   ");        //mostramos un mensaje de bienbenida
  lcd.setCursor(0,1);                       //movemos el cursor a 1ª columna y 2ª fila
  lcd.print("     PARA TODOS     ");        //mostramos un mensaje en esa posición
  Serial.println ("Test KY-015 y DHT22");   //mostramos mensaje en el puerto serie
  lcd.setCursor(0,2);                       //movemos el cursor a 1ª columna y 3ª fila
  lcd.print("   MONTAJE PRUEBA   ");        //mostramos un mensaje de bienvenida
  lcd.setCursor(0,3);                       //movemos el cursor a 1ª columna y 4ª fila
  lcd.print("SENSOR KY015 y DHT22");        //mostramos un mensaje en esa posición

  delay(3000);                              //pausamos 3seg para leer los mensajes
  lcd.clear();                              //borramos el lcd entero

  //Ponemos en la esquina superior derecha el modelo de la placa que estamos probando
  //Si no borramos o escribimos encima, se mantendrá visible siempre
  lcd.setCursor(0,0);                       //movemos el cursor a 1ª columna y 1ª fila
  lcd.print("KY-015");                      //mostramos el modelo de la placa
  lcd.setCursor(0,2);                       //movemos el cursor a 1ª columna y 3ª fila
  lcd.print("DHT22");                       //mostramos el modelo del sensor

  dht11.begin ();                           //le indicamos al sensor dht11 que comience a medir
  dht22.begin ();                           //le indicamos al sensor dht22 que comience a medir
}


void loop() {
  delay(2000);                              //esperamos 2 segundos antes de empezar

  //Leemos el sensor y almacenamos los valores
  humedad_ky015 = dht11.readHumidity();             //leemos la humedad y almacenamos
  temperatura_ky015 = dht11.readTemperature();      //leemos la temperatura y almacenamos
  humedad_dht22 = dht22.readHumidity();             //leemos la humedad y almacenamos
  temperatura_dht22 = dht22.readTemperature();      //leemos la temperatura y almacenamos

  //Comprobamos si la lectura a fallado. La instruccion isnan, comprueba si la variable
  //que le pasamos tiene un valor representativo.  
  //Primero al dht11 incluido en la placa ky-015
  if (isnan(humedad_ky015) || isnan(temperatura_ky015)) {
    //Si la lectura es incorrecta
    lcd.setCursor(0,1);                             //movemos el cursor a 1ª columna y 2ª fila
    lcd.print("Error de lectura    ");              //mostramos el mensaje de error en el LCD
    Serial.print ("Error de lectura en KY-015");    //mostramos el mensaje de error en el serial
  }
  else {
    //Si la lectura es correcta
    lcd.setCursor(9,0);                     //movemos el cursor a 10ªcolumna y 1ª fila
    lcd.print ("H=");                       //mostramos el mensaje de humedad con la H
    lcd.print (humedad_ky015,1);            //mostramos el valor de la humedad con un decimal
    lcd.print ('%');                        //mostramos el simbolo de porcentaje
  

    lcd.setCursor (0,1);                    //movemos el cursor a 1ª columna y 2ª fila
    lcd.print("                    ");      //borramos la 2ª fila entera por si ha aparecido el
                                            //mensaje de error
    lcd.setCursor (9,1);                    //movemos de nuevo el cursos a 10ª columna y 2ª fila
    lcd.print ("T=");                       //mostramos el mensaje de temperatura con la T
    lcd.print (temperatura_ky015,1);        //mostramos el valor de la temperatura con un decimal
    lcd.print (char(223));                  //mostramos el caracter º con el valor 223
    lcd.print ('C');                        //mostramos la letra C

    Serial.print("KY-015: ");               //mandamos texto al visor serie
    Serial.print("Humedad = ");             //mandamos texto al visor serie
    Serial.print(humedad_ky015,1);          //mandamos el valor medido de humedad con 1 decimal
    Serial.print(" %\t");                   //mandamos el simbolo % y un tabulador
    Serial.print("Temperatura = ");         //mandamos texto al visor serie
    Serial.print(temperatura_ky015,1);      //mandamos el valor medido de temperatura con 1 decimal
    Serial.print("ºC");                     //mandamos texto al visor serie
  }

  //Comprobamos si la lectura a fallado. La instruccion isnan, comprueba si la variable
  //que le pasamos tiene un valor representativo.
  //Ahora al dht22
  if (isnan(humedad_dht22) || isnan(temperatura_dht22)) {
    //Si la lectura es incorrecta
    lcd.setCursor(0,3);                               //movemos el cursor a 1ª columna y 4ª fila
    lcd.print("Error de lectura    ");                //mostramos el mensaje de error en el LCD
    Serial.println ("    Error de lectura en DHT22"); //mostramos el mensaje de error en el serial y
                                                      //pasamos de linea
  }
  else {
    //Si la lectura es correcta
    lcd.setCursor(9,2);                     //movemos el cursor a 10ªcolumna y 3ª fila
    lcd.print ("H=");                       //mostramos el mensaje de humedad con la H
    lcd.print (humedad_dht22,1);            //mostramos el valor de la humedad con un decimal
    lcd.print ('%');                        //mostramos el simbolo de porcentaje
  

    lcd.setCursor (0,3);                    //movemos el cursor a 1ª columna y 4ª fila
    lcd.print("                    ");      //borramos la 2ª fila entera por si ha aparecido el
                                            //mensaje de error
    lcd.setCursor (9,3);                    //movemos de nuevo el cursos a 10ª columna y 4ª fila
    lcd.print ("T=");                       //mostramos el mensaje de temperatura con la T
    lcd.print (temperatura_dht22,1);        //mostramos el valor de la temperatura con un decimal
    lcd.print (char(223));                  //mostramos el caracter º con el valor 223
    lcd.print ('C');                        //mostramos la letra C

    Serial.print("\tDHT22: ");              //mandamos texto al visor serie
    Serial.print("Humedad = ");             //mandamos texto al visor serie
    Serial.print(humedad_dht22,1);          //mandamos el valor medido de humedad con 1 decimal
    Serial.print(" %\t");                   //mandamos el simbolo % y un tabulador
    Serial.print("Temperatura = ");         //mandamos texto al visor serie
    Serial.print(temperatura_dht22,1);      //mandamos el valor medido de temperatura con 1 decimal
    Serial.println("ºC");                   //mandamos texto al visor serie pasamos linea

    
  }  
}

