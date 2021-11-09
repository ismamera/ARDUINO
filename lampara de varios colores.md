## PWN 

(pulse with nodulation)

modulacion por ancho de pulsos 

problema: tengo un arduino que suministra a un led a mayor intensidad de co reiente (a) el brilla mas 

a menor intensidad de corriente el led brilla menos (ver ley de OHM)

si subimos o bajamos el voltaje ,haremos lo mismo con la intensidad 

suponiendo que la resistencia del circuito es la misma

entomcesw si conecto un led con su resistencia de 220 ohmnios a un voltaje de 5v o de 3,3v 

el led brillara mas cn 5v y menos con 3,3v

PULSOS 

un pulso electrico es una señal de voltaje de medida del tiempo

los ojos humanos podemos detectar cambios hata el entorno al 12 H3 apartir de 24-30H3 no somos capaces visualmente 

los pulsos modulados en ancho crean la ilusion de voltajes intermedio entre 0 y 5v para ello usan pulsos muy cortos 

que usaremos atraves de la funcion Analogwrite(pin,0-255) esta funcion cn PWN

los pines con PWN estan marcados con el simbolo ~ (la tilde de de la eñe q se hace cn al+gr+4 )

la funcion nos pide 2 cosas por un lado y lo primero el numero de pin por otro lado un numero entre 0-255

0 significa 0% de voltaje 

255 significa 100% de voltaje (sv)

int significa integer q en castellano significa numero integro 

significa que nuestra variable es un tipo de dato numerico no decimal le asigna un espacio en memoria. otros tipos:

sting que significa cadena de caracteres 

bool significa significa bolcano y es verdadero o falso 

chaz q significa 1 unico caracter 

float que signifia numeros decuimales 

raw sensor valers esto son valores del sensor sin tratar

 










































































