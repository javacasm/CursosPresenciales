* * *

# Curso básico de Arduino

![Createc3D](imagenes/logocreatec3d_2.png)

### José Antonio Vacas @javacasm
![CCbySA](imagenes/CCbySQ_88x31.png)

* * *

# Arduino

## Así lo vemos nosotros

![arduino](imagenes/ArduinoUno_R3_Front_450px.jpg)

[más detalle](imagenes/ArduinoUno_R3_Front.jpg)

* * *

## Así es internamente
#### (mucho por descubrir)

![pinout](imagenes/ccb2f5f1008b324e19add5295cc14e68.jpg)

* * *

# Para hacer un proyecto necesitamos:

* ### Programa

* ### Montaje

#### (descargar el programa en la placa)

* * *

### ¿Qué es un programa? un conjunto de instrucciones ordenadas

#### Programa parpadeo (blink)

* Encendemos
* Esperamos
* Apagamos
* Esperamos
* Volvemos al principio

* * *

## Programando con Bitbloq

### http://bitbloq.bq.com

#### [Instalación del IDE de arduino](http://www.slideshare.net/javacasm/32-instalacin-del-ide)

Programa parpadeo

![programa blink](imagenes/blink.png)

* * *

### Usaremos el led interno

![blink](imagenes/tumblr_mj00x5CdpR1s6tqslo1_500.gif)

#### Ejercicio: Cambiar la velocidad de parpadeo

* * * 

## Con led externo

### Montaje sencillo
![led externo](imagenes/ExampleCircuit_bb.png)

[detalle led](imagenes/300px-LED.png)

* * *
### Montaje con placa prototipo
![led placa](imagenes/led13bb.jpg)

[¿cómo funciona una placa prototipo?](imagenes/breadboard1.gif)

#### Ejercicio: Cambiar el pin utilizado al pin 2

* * *

### Esquema eléctrico

![led externo](imagenes/ExampleCircuit_sch.png)

* * *

## Con un relé usaremos ¡¡grandes corrientes eléctricas!!

![rele](imagenes/relee_arduino.jpg)

![Danger](imagenes/Dangers-of-electric-shock.jpg)


#### Ejercicio: Cambiar al pin del esquema

* * * 
## Veamos un poco de código

	void setup()  				// Función de configuración
	{
	  pinMode(13,OUTPUT);  		// Vamos a usar una salida
	}


	void loop()  // Función de bucle. Se repite por siempre
	{
	  digitalWrite(13,HIGH);  	// Activamos la salida 13
	  delay(1000);				// Esperamos
	  digitalWrite(13,LOW);		// Desativamos la salida 13
	  delay(1000);				// Esperamos
	}							// Cuando termina se vuelve a llamar

#### Ejercicio: Cambiar al pin del esquema
#### Ejercicio: Cambiar el pin utilizado al pin 2

* * * 
# Envío de datos serie

### La comunicación serie se produce via USB entre Arduino y el PC

* Detectamos el puerto
* Configuramos la velocidad
* Necesitamos un programa para ver los datos

## Vamos a enviar "Encendido" y "Apagado" al PC
![ParpadeoSerie](imagenes/ParpadeoSerie.png)

* * * 
# Escritura de valores analógicos

## Usando técnicas como PWM podemos simular valores intermedios: 0 - 255
### (sólo en algunos pines)

## Vamos a hacer que cambie: usaremos una variable

![analogWrite](imagenes/AnalogWrite.png)

### Si vemos el código

	void setup()						// configuracion
	{
	  pinMode(5,OUTPUT);				// Usaremos la patilla 5 como salida
	}

	void loop()
	{
	  int valorSalida=0;				// la variable valorSalida empieza en 0
	  while (valorSalida < 256) {		// Haremos el bucle hasta que llegemos a 256
	    analogWrite(5,valorSalida);		// pasamos el valor a la patilla 5
	    delay(100);						// Esperamos 0,1 segundos
	   }

	}

* * *
# Led RGB: 3 led (Red,Green,Blue) con una de las patillas común

## Positivo (Ánodo) Común

![LedRGBPcomun](imagenes/LedRGBPcomun.jpg)

## Negativo (Cátodo) Común

![LedRGBNcomun](imagenes/LedRGBNComun.png)

## Tiras de leds: Necesitamos más potencia por lo que usaremos un transistor como amplificador.

### El montaje es sencillo

![ledstripbjt](imagenes/ledstripbjt.gif)

* * *

# Lectura de datos analógicos

* ## Sensores (luz, temperatura)

* ## Potenciómetro: resistencia variable (mando de volumen)

### Se leen valores enteros entre 0 y 1023
### Equivalen a los valores de 0V y 5V

* * * 
# Potenciómetro regulando una salida

![lecturaAnalogica](imagenes/arduino_pot_led.png)

![SalidaAnalogicaProporcional](imagenes/SalidaAnalogicaProporcional.png)

### El código:

	void setup()
	{
	  pinMode(5,OUTPUT);
	}


	void loop()
	{
	  int valorPotenciometro=analogRead(0);				 	// Leemos el valor
	  int ValorSalida=map(valorPotenciometro,0,1023,0,255);	// Convertimos al rango de salida
	  analogWrite(5,ValorSalida);							// Escribimos el valor en la salida
	}

### Ejercicio: usar 3 potenciómetros para controlar los colores de un led RGB

* * * 

# Para los sensores:

* Haremos la lectura
* Conversiones: traducimos a valores físicos (aritmética/mapeo)
* Calibraciones: establecemos valores de referencia

* * *
# Sensor de temperatura LM35: viene calibrado y linealizado

![lm35](imagenes/Arduino_lm35_board_setup.jpg)

## Usamos la fórmula del fabricante

temperatura = valorAnalogico*5*100/1024 

[pinout lm35](imagenes/tmp36pinout.gif)

* * * 
## El código quedaría así:

### Enviaremos el dato leído al pc con la función __ Serial __

	int sensorPin=A0;

	void setup()
	{
		Serial.begin(9600);  // Configuramos la conexión
	}

	void loop()
	{
		int sensorValue= analogRead(sensorPin);  // Leemos el valor analógico
		float temperatura=(sensorValue*5*100)/1024; // float para tener decimales
		Serial.println(temperatura);			// Enviamos el dato al PC
		delay(1000);
	}

* * *

# Pulsaciones: botones

## Montaje 

![boton](imagenes/button.png)

## Programa
### Usamos una sentencia condicional: si se cumple esto...se hace aquello
![boton](imagenes/Boton_Led.png)

### Su código

	void setup()
	{
	  pinMode(2,INPUT_PULLUP);  // Usamos 2 como entrada
	  pinMode(13,OUTPUT);		// Usamos 13 como salida
	}


	void loop()
	{
	  if (digitalRead(2) == HIGH)  	// Si el pulsador está pulsado
	  {
	    digitalWrite(13,HIGH);		//Encendemos el led 13
	  }
	  else 							// Si NO se cumple
	  {		
	    digitalWrite(13,LOW);		// Lo apagamos
	  }
	}

* * *

# LCD

* * *
¿Qué es una librería?

Ejemplo: [lcd](http://arduino.cc/en/pmwiki.php?n=Reference/LiquidCrystal) o [servo](http://arduino.cc/en/pmwiki.php?n=Reference/Servo)

[Librería LCD MF](https://bitbucket.org/fmalpartida/new-liquidcrystal/wiki/Home)
[Ejemplos lcd](http://arduino-info.wikispaces.com/LCD-Blue-I2C#v3)
[Ejemplo bq](http://diwo.bq.com/programando-lcd/)

* * *

# Agradecimientos:

[Arduino](http://arduino.cc)
[Adafruit](http://adafruit.com)
[Sparkfun](http://sparkfun.com)
[wikipedia](http://es.wikipedia.org)
[José Pujol](https://tecnopujol.wordpress.com)