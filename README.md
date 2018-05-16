Multiples_variables
=============

-	[Introducción](#introducción)

Introducción
------------

La finalidad de este repositorio es mostrar como enviar multiples variables en un solo mensaje a través de Sigfox. 
Se utilizará el sensor BME280 el cual nos proporciona cuatro variables diferentes: temperatura, presión, 
altura y humedad (Se puede utilizar otro tipo de sensores). Estas cuatro variables las introduciremos 
en nuestro payload, que posteriormente será enviado hacia el backend de Sigfox.

El programa del sensor BM280 y las librerías fueron tomadas del Github de Adafruit (https://github.com/adafruit/Adafruit_BME280_Library)

Conexión
--------

El sensor se conecta de acuerdo a la imagen de abajo

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme1.png?raw=true)

Una vez conectado, cargamos a nuestro Devkit el siguiente programa ([code](https://github.com/NXTIoT/Multiples_variables/blob/master/BME280_sigfox/bme280_sigfox.ino))
Abrimos el "Monitor Serie" de Arduino y nos aparecerá la información de las cuatro variables que está midiendo. Despues desplegara 
los comandos de "reset" del modulo y el comando de envio "AT$SF=xxxxxxxx"

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme2.png?raw=true)

En nuestro backend, necesitaremos decodificar el dato en crudo que llega al backend para corroborar que la informacion enviada corresponda 
con lo mostrado en el "Monitor Serie". 

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme3.png?raw=true)

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme4.png?raw=true)

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme5.png?raw=true)

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme6.png?raw=true)





Si revisamos el backend de Sigfox veremos que la informacion enviada en hexadecimal 

