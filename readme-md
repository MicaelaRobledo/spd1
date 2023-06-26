## Integrante:
- Micaela Robledo.


## Proyecto: Ascensor de montacargas



## Descripción
Se nos pide armar un modelo de montacarga funcional como maqueta para un hospital. El
objetivo es que implementes un sistema que pueda recibir ordenes de subir, bajar o pausar
desde diferentes pisos y muestre el estado actual del montacargas en el display 7
segmentos.

## Función principal
1- Implementa un algoritmo que permita que el elevador suba y baje o frene presionando los botones correspondientes.
2- Deberán buscar una forma para pausar el montacargas cuando el usuario lo determine.



~~~ C++ (lenguaje en el que esta escrito)
//variables 
#define boton_subir 4
#define boton_bajar 3
#define boton_parar 2

#define led_verde 13
#define led_rojo 12
#define led_azul A2

#define LED_G 11
#define LED_F 10
#define LED_A 9
#define LED_B 8
#define LED_E 5
#define LED_D 6
#define LED_C 7

#define foto_resistencia A0
#define flexion A3
#include <Servo.h>
Servo myServo;

int piso = 0;
bool elevador_subiendo = false;
bool elevador_bajando = false;
int subir;
int bajar;
int parar;
int intensidad = 0;
int flex;
int posicion_servo;
    

void setup() 
{
  pinMode(boton_subir, INPUT);
  pinMode(boton_bajar, INPUT);
  pinMode(boton_parar, INPUT);
  
  pinMode(led_rojo, OUTPUT);
  pinMode(led_verde, OUTPUT);
  pinMode(led_azul, OUTPUT);
  
  pinMode(LED_G, OUTPUT);
  pinMode(LED_F, OUTPUT);
  pinMode(LED_A, OUTPUT);
  pinMode(LED_B, OUTPUT);
  pinMode(LED_E, OUTPUT);
  pinMode(LED_D, OUTPUT);
  pinMode(LED_C, OUTPUT);
  
  myServo.attach(A1);
  Serial.begin(9600);
}

void loop() 
{
  
  bajar = digitalRead(boton_bajar);
  parar = digitalRead(boton_parar);
  subir = digitalRead(boton_subir);
  if(subir == HIGH || elevador_subiendo == true)
  {
    	subir_piso();   	
  }
  
  if(bajar == HIGH || elevador_bajando == true)
  {
     	bajar_piso();
  }
  
  if(parar == HIGH)
  {
      	parar_piso();
  }
  mostrar_piso();
  prender_foto_resistencia();
  
}

//ascensor suba
void subir_piso() 
{	
    if(piso < 9)
  	{	 
      	prender_servo();
      	prender_led_verde();
      	piso++;
        Serial.println("el ascensor esta subiendo");
      	elevador_subiendo = true;
  	}
    else
    {	
      	intensidad = 150;
       	elevador_subiendo = false;
      	prender_led_rojo();	
    }
}

//ascensor baje
void bajar_piso() 
{
  	if(piso > 0)
  	{
       prender_servo();
       prender_led_verde();
       piso--;
       Serial.println("el ascensor esta bajando");
       elevador_bajando = true;
    }
  	else
  	{	
      	intensidad = 150;
        elevador_bajando = false;
      	prender_led_rojo();	
    }
}

//ascensor parar
void parar_piso()
{
	prender_led_rojo();
  	Serial.println("el ascensor se detuvo");
   	elevador_bajando = false;
  	elevador_subiendo = false;
  	
}

void prender_foto_resistencia()
{
  intensidad = analogRead(foto_resistencia);
  
  if(intensidad > 307)
  { 
  	digitalWrite(led_azul, HIGH); //Si hay luz ambiente prende el bombillo
  }
  else
  {
 	digitalWrite(led_azul, LOW); //Si no hay luz ambiente apaga el bombillo
  }
}

void prender_led_verde()
{
    delay(3000);
	digitalWrite(led_verde, HIGH);
   	digitalWrite(led_rojo, LOW);
}

void prender_led_rojo()
{
    delay(3000);
  	digitalWrite(led_verde, LOW);
    digitalWrite(led_rojo, HIGH); 
} 

void prender_servo()
{
  flex = analogRead(flexion);
  posicion_servo = map(flex, 770, 950, 0, 180);
  posicion_servo = constrain(posicion_servo, 0, 180);
  myServo.write(posicion_servo);
}  

//numero de piso
void mostrar_piso() 
{
  switch(piso) 
  {
    case 0:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_F, HIGH);
      digitalWrite(LED_E, HIGH);
      digitalWrite(LED_D, HIGH);
      digitalWrite(LED_C, HIGH);
    break;
    case 1:
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_C, HIGH);
    break;
    case 2:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_G,HIGH);
      digitalWrite(LED_E, HIGH);
      digitalWrite(LED_D, HIGH);
    break;
    case 3:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_G,HIGH);
      digitalWrite(LED_C, HIGH);
      digitalWrite(LED_D, HIGH);
    break;
    case 4:
      digitalWrite(LED_F, HIGH);
      digitalWrite(LED_G, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_C, HIGH);
    break;
    case 5:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_F,HIGH);
      digitalWrite(LED_G,HIGH);
      digitalWrite(LED_C,HIGH);
      digitalWrite(LED_D, HIGH);
    break;
    case 6:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_F,HIGH);
      digitalWrite(LED_G,HIGH);
      digitalWrite(LED_E,HIGH);
      digitalWrite(LED_D, HIGH);
      digitalWrite(LED_C, HIGH);
    break;
    case 7:
      digitalWrite(LED_A,HIGH);
      digitalWrite(LED_B,HIGH);
      digitalWrite(LED_C,HIGH);
    break;
    case 8:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_G, HIGH);
      digitalWrite(LED_F, HIGH);
      digitalWrite(LED_E, HIGH);
      digitalWrite(LED_D, HIGH);
      digitalWrite(LED_C,HIGH);
    break;
    case 9:
      digitalWrite(LED_A, HIGH);
      digitalWrite(LED_F, HIGH);
      digitalWrite(LED_B, HIGH);
      digitalWrite(LED_G, HIGH);
      digitalWrite(LED_C, HIGH);
    break;
  }
  Serial.println(piso);
  delay(3000);
  // Apagar todos los LEDs
  digitalWrite(LED_A, LOW);
  digitalWrite(LED_B, LOW);
  digitalWrite(LED_C, LOW);
  digitalWrite(LED_D, LOW);
  digitalWrite(LED_E, LOW);
  digitalWrite(LED_F, LOW);
  digitalWrite(LED_G, LOW);
}
~~~

## :robot: Link al proyecto
- [proyecto](https://www.tinkercad.com/things/hstYunIvcDW-micaela-robledo-1d/editel?sharecode=Bt_0MaJ5_o5RbnArsnybER7h64Q8Yn_rGWaq4thZlSM)