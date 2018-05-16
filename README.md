Multiples_variables
=============

-	[Introducción](#introducción)

-	[Conexión](#conexión)

Introducción
------------

La finalidad de este repositorio es mostrar una manera de enviar multiples variables con el DEVKIT en un solo mensaje a través de Sigfox. 
Se utilizará el sensor BME280 el cual nos proporciona cuatro variables diferentes: temperatura, presión, 
altura y humedad (Se puede utilizar otro tipo de sensores). Estas cuatro variables las introduciremos 
en nuestro payload, que posteriormente será enviado hacia el backend de Sigfox. Ya en el backend decodificaremos la informacion 
enviada, creando variables que podremos utilizar en los callbacks.

El programa del sensor BM280 y las librerías fueron tomadas del Github de Adafruit (https://github.com/adafruit/Adafruit_BME280_Library)

Conexión
--------

El sensor se conecta de acuerdo a la imagen de abajo utilizando la comunicación I2C

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme1.png?raw=true)

Una vez conectado, cargamos a nuestro Devkit el siguiente programa ([code](https://github.com/NXTIoT/Multiples_variables/blob/master/BME280_sigfox/bme280_sigfox.ino))
Abrimos el "Monitor Serie" de Arduino y presionamos el boton azul para enviar un mensaje. Enseguida nos aparecerá la información de las cuatro variables que está midiendo. Despues desplegara 
los comandos de "reset" del modulo y el comando de envio "AT$SF=xxxxxxxx"

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme2.png?raw=true)

En nuestro backend, necesitaremos decodificar el dato en crudo que llega al backend para corroborar que la informacion enviada corresponda 
con lo mostrado en el "Monitor Serie". Damos click en el "Device Type" de nuestro dispositivo

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme4.png?raw=true)

nos aparecerá la informacion de nuestro "Device Type". En la esquina superior derecha, hacemos click en "Edit" 

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme5.png?raw=true)

nos dirigimos a la parte inferior en "Payload display". Seleccionamos "Payload parsing -> Custom grammar" y escribimos lo siguiente

-	temp::uint:8 presion::float:32:little-endian alt::float:32:little-endian hum::uint:8

damos click en "OK"

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme6.png?raw=true)

ahora nos vamos a los mensajes del dispositivo. Al ver el mensaje enviado, debajo del payload en hexadecimal, veremos las
4 variables que declaramos en el "Device Type"

![dev1](https://github.com/NXTIoT/Multiples_variables/blob/master/imagenes/bme3.png?raw=true)



