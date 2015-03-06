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

![pinout](imagenes/ccb2f5f1008b324e19add5295cc14e68.jpg)

* * *

# Parpadeo (blink)

### Necesitamos:

### * Programa

### * Montaje

#### (descargar el programa en la placa)


* * *

### ¿Qué es un programa?

#### Programa parpadeo

* Encendemos
* Esperamos
* Apagamos
* Esperamos
* Volvemos al principio

* * *

## Programa bitbloq

### http://bitbloq.bq.com

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

[Placa prototipo](imagenes/breadboard1.gif)

#### Ejercicio: Cambiar el pin utilizado al pin 2

* * *

### Esquema
![led externo](imagenes/ExampleCircuit_sch.png)

* * *

## Con relé

![rele](imagenes/relee_arduino.jpg)

#### Ejercicio: Cambiar al pin del esquema

* * * 
## Veamos un poco de código

	void setup()
	{
	  pinMode(13,OUTPUT);
	}


	void loop()
	{
	  digitalWrite(13,HIGH);
	  delay(1000);
	  digitalWrite(13,LOW);
	  delay(1000);

	}

#### Ejercicio: Cambiar al pin del esquema
#### Ejercicio: Cambiar el pin utilizado al pin 2
* * * 
# Agradecimientos:

[Arduino](http://arduino.cc)
[Adafruit](http://adafruit.com)
[Sparkfun](http://sparkfun.com)
[wikipedia](http://es.wikipedia.org)