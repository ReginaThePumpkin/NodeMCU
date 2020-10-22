# Contador de 7 bits
Contador de 7 bits implementado con un Node MCU. 

# Circuito
![circuito](https://github.com/ReginaThePumpkin/NodeMCU/blob/master/7-bit_counter/images/circuito.png)

![node](https://github.com/ReginaThePumpkin/NodeMCU/blob/master/7-bit_counter/images/node.jpeg)

# Código de arduino (sketch.ino)

Este código implementa el contador de 7 bits en un Node MCU

## Asignación de pines a variables
``` ino
  //Asigna los pines a variables
  #define LED_0 D2
  #define LED_1 D3
  #define LED_2 D4
  #define LED_3 D5
  #define LED_4 D6
  #define LED_5 D7
  #define LED_6 D8
```
## Configuración de pines como salidas
``` ino
  void setup()
  {
    //Seteando los pines como salidas
    pinMode(LED_0, OUTPUT);
    pinMode(LED_1, OUTPUT);
    pinMode(LED_2, OUTPUT);
    pinMode(LED_3, OUTPUT);
    pinMode(LED_4, OUTPUT);
    pinMode(LED_5, OUTPUT);
    pinMode(LED_6, OUTPUT);
  }
```
## Función que enciende y prende los leds de acuerdo a los parámetros
``` ino
  /*
   * Controla los leds que prenden y los que apagan para cada caso
  */
  void prende(int _a, int _b, int _c, int _d, int _e, int _f, int _g){
    if(_a){digitalWrite(LED_0, HIGH);}
    else digitalWrite(LED_0, LOW); 

    if(_b){digitalWrite(LED_1, HIGH);}
    else digitalWrite(LED_1, LOW); 

    if(_c){digitalWrite(LED_2, HIGH);}
    else digitalWrite(LED_2, LOW); 

    if(_d){digitalWrite(LED_3, HIGH);}
    else digitalWrite(LED_3, LOW); 

    if(_e){digitalWrite(LED_4, HIGH);}
    else digitalWrite(LED_4, LOW); 

    if(_f){digitalWrite(LED_5, HIGH);}
    else digitalWrite(LED_5, LOW); 

    if(_g){digitalWrite(LED_6, HIGH);}
    else digitalWrite(LED_6, LOW); 
  }
```
## Función que enciende todos los leds
``` ino
  /*
   * Prende todos los leds a modo de indicador
  */
  void prende_todo(){
      digitalWrite(LED_0, HIGH);
      digitalWrite(LED_1, HIGH);
      digitalWrite(LED_2, HIGH);
      digitalWrite(LED_3, HIGH);
      digitalWrite(LED_4, HIGH);
      digitalWrite(LED_5, HIGH);
      digitalWrite(LED_6, HIGH);
      delay(2000);
  }
```
# Void loop
En el void loop se controla todo, tenemos una función que asigna el valor de los bits asignandóles valores al convertir los números de 0 a 127 a base binaria.
``` ino
  void loop()
  {
    int a,b,c,d,e,f,g;
    for(int i=0; i<=127; i++){
      //El módulo a 2 determina si el bit correspondiente está encendido o apagado
      a = i%2;
      b = i/2 %2;
      c = i/4 %2;
      d = i/8 %2;
      e = i/16 %2;
      f = i/32 %2;
      g = i/64 %2;
      //Enviamos como parámetros los valores del número en binario (Los bits)
      prende(a,b,c,d,e,f,g);
      delay(250);
    }
    prende_todo();
  }
```
# Vídeo demostrativo en mi canal de youtube
[demo](https://www.youtube.com/watch?v=L56_J5pGeAk)
