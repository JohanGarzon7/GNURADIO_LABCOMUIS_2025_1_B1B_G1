# Laboratorio de Comunicaiones 

## Universidad Industrial de Santander

# Practica 1

### Integrantes

- Daniel Leonardo Gonzalez Gamba - 2215727
- Johan Esneider Garzon Espejo -2215588

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha de entrega

7 de Marzo de 2025

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asimismo, los autores asumen plena responsabilidad por la información contenida en este documento. 
---

---
# Palabras Clave 
`GNURADIO` ,`Osciloscopio`,`Analazidor de espectros`, `Frecuencia`,
`URRP 2920`.

# Resumen 
Reconocer y entender los conceptos basicos del los sitemas de comunicacion asi como los parametros y equipos que se utilizan en esta, haciendo uso de los conocimientos adquiridos previamente en la clase teorica impartido por el profesor.  
Se hace uso de equipos de laboratorio como el dispositivo de radio de URRP 2920 para amplificar señales, osciloscopio para medir amplitud y periodo, y por ultimo el analizador de espectro utilizado para medir la potencia de la señales.

# Objetivo General

Familiarizarse con el uso de herramientas de software definido por radio (SDR) como GNU Radio, junto con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. 

# Introduccion

Se pasaron desde implementaciones en GNURADio hasta el reconocimiento de los quipos y comprender su funcionamiento esto se hizo con el fin de evidenciar que le suceden a las señales en la comucnicaion de estas desde que pasa con un señal mak muestrada hasta que sucede cuando se sale del rango de fucnionamiento de los equipos.

Pasando a otro apartado es demasiado importante la teoria de muestreo de las señales, a lo que se quiere llegar es que romper el limite de nyquist hace que la señal no se muetre como se debe generando posibles problemas en esta lo cual provocaron grandes errores a la hora de procesar la señal.

El programa GNURADIO nos brinda de una manera de aprendizaje espectacular dotandonos de herramientas para la visualizacion de las señales asi como la pacapcidad para modificar la amplitud la frecuecia la frecuencia de muestro la amplitud la fase y demas parametros junto con la capacidad desde este programa para concetarse a el USRP 2920 para transimitir la señal tanto al osciloscopio como al analizador de espectros

Como fin se busca poder analizar las señales, conocer los aparatos y sus limitaciones y que cosas suceden con las señales en el area de las comucnicaciones.

# Procedimiento

## Reconocimiento de los equipos:

Para este paso la idea fue buscar los datasheets de los distintos aparatos asi como el rango de funcionamiento de estos por ejemplo saber cual es el rango de frecuencia el que pueden utilizar esto para no sobrepasar dichos limites y hacer mediciones incorrectaas, por ellos una vez analizados los parametros se saco esta lista el cual resume los datos hallados: 

### USRP-2920 
- Ancho de Banda: 20MHz 
- Rango de frecuencia: 50MHz a 2.2GHz 
- Paso de frecuencia: <1KHz 
- Rango de ganacia: 0 dB a 31 dB 
- Potenca tipica. 12W a 15W
### Analizador de Espectros R&S FPC1000 
- Numero de canales: 1 
- Ancho de banda: 1Hz 
- Impedancia de entrada: 50 ohm 
- Maximo samp_rate: 2.5Gsamples/s 
- Resolucion de frecuencia: 1 Hz
### Osciloscopio R&S RTB2004
- Impedancia de entreda: 1M ohm .
- Numero de canales: 4 
- Resolucion: 14 bit 
- Rango de frecuencia: 5Khz a 1Ghz 
- Canales digitales

Otros cosas relevantes son las configuraciones que se les deben a hacer a dichos aparatos, para configurar el osciloscopio para medir la amplitud y la frecuencia de una señal a este se le configura la escala de division osea los volts por divicion ademas del la posicion horizontal tambien es importante para un buena medicion, se puede agregar de igual manera cualquier medida que se necesite de la señal el periodo la frecuencia etc..

Entre medir una señal en el dominio del tiempo y en el dominio de la frecuecnia ay ciertas diferencias entre ellas que con el osciloscopio en el dominio de tiempo se puede calcular la amplitud de la señal y en el analizador de espectros la potencia y ancho de banda.  

Se mide con el analizador de espectros mas especificamente con el RBW aumentar o disminuir el span requiere de mas o menos costo computacional ya que puede llegra a ser medida la señal de una manera mas precisa.

## Simulacion de Señales en GNU Radio

En este aparto veremos como se comportavan la señales con diferentes tipos de forma de onda y como varian en tiempo y en frecuencia.  

Para simular esto utilizamos el siguiente flujograma de GNURADIO [`simple_flowgraph.grc`](https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica1/Practica1C/simple_flowgraph.grc).  
Eh identificamos los bloques necesarios para el funcionamiento de nuestro programa:  

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica1/Practica1C/Evidencias/WhatsApp%20Image%202025-03-06%20at%209.39.11%20PM.jpeg">  
Una vez teniendo en cuenta cuales son nuetros bloques principales ejecutaremos nuestro flujograma para que nos quede algo asi:  

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica1/Practica1C/Evidencias/Captura%20desde%202025-03-06%2021-44-37.png">  
Ahora pasaremos ah analizar las señales para ello modificaremos el tipo de onda la forma de esta la frecuencia y faase de la señal.  
<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica1/Practica1C/Evidencias/Captura%20desde%202025-02-25%2015-58-10.png">  
Nos quedara algo similar a lo anterior si se desea ver mas imagenes con variaciones con distintos parametro debe acceder a lo siguiente

[Ir a las evidencias](/Practica1/Practica1C/Evidencias)

Ahora con esto podemos analizar y reponder cual es la diferencia entre una una fuente de tipo flotante y una de tipo complejo y esa es s que se genera una señal sinosoidal real mientras que en el tipo complejo se genera una señal real e imaginaria una desfada 90 grados de la otrra en banda base lo cual vendria siendo una señal exponecial compleja.

Como bien se vio la forma de onda afecta a la distribuccionde energia a que se debe esto esta genera mas ruido en el dominio de la frencuencia, en señales como la cuadrada o diente de cierra este ruido es mayor, mientras que en señales como sinusoidales este ruido es minimo.  

Ahora si se modifican distintos parametros como la amlitud, el offset,etc... de la señal, esta se visualizara en la grafica del dominio del tiempo mientras quye el el dominio de la frecuencia su ganancia se vera alterada.  

Al aumentar la amplitud en el dominio del tiempo, esta causa que se genere mas ganancia en el espectro de frecuencia.

## Transmisión y Medición de Señales con el USRP 2920

Para este apartado transmitiremos señales usando el USRP 2920 y medimos parámetros clave como potencia, ancho de banda, piso de ruido y relación señal a ruido (SNR).

### Conclusiones
## Analisis de resultados
### Actividad 3: Transmisión y Medición de Señales con el USRP 2920
Para la transmision de y medicion de Señales haciendo uso del USRP 2920, como primer paso se debe configurar el dispositivo, primero debemos crear un flujograma para que se pueda conectar mediante el reloj del computador, también debe conectar el lan y el cable tx/rx para transimitir la señal.  
El flujograma posee algunos parametro sque pueden afectr la potencia de la señale transmitida tales  como la amplitud, el ofset, el ruido de voltaje y el ancho de banda de resolucion. Es te ultimo se puede medir directamente desde el analizador de espectros, para esto se debe modificar como se ve la informacion en el analizador de espectros por lo que se debe varias la frecuencia central a una mas adecuada y poner un nivel de referencia con uno de los marcadores para luego poner otro marcador al otro punto de la señal.  
para calcular la SNR de la señal se hace uso de la ecuacion $SNR=\10 Log{potencia de la señal/Potencia de Ruido}$  
Al varias la ganancia del USRP se observan cambios en la potencia, una mayor amplitud, puede aumentar el ruido y mejorar el SNR.  
Respondiendo a la pregunta se "¿Es posible medir o estimar la potencia de la señal observada en el osciloscopio? ¿Por qué?" la respuesta es principalmente por que el osciloscopio es echo para medir volatajes sin potencia, sin embargo si se puede estimar con la relación:  
\[ P = \frac{V^2}{R} \] 
### Actividad 4
Las concluisones que se pueden observar sobre la relacion entre la potencia de la señal y la calidad de la comunicacion esque es importante encontrar un equilibrio entre la potencia y otras cosas a tener en cuenta (consumo,interferencia) entre este y más apartados. El piso de ruido afecta la capacidad de detectar sanales debiles dado que si el piso de ruido es demaciado "Abosrveria" la señal y no se podría analizar debidamente.  
Las limitaciones que presentan algunos equipos para realizar las mediciones de ancho de banda y precision en las mediciones es dependiendo del dispositivo al que mencionemos como ejemplo tenemos el Osciloscopio R&S RTB2004 el cual posee un rango de frecuencia: 5Khz a 1Ghz es en cuanto a limitaciones, con el analizador de espectros y una señal que se comporta en el rango de frecuencias permitido para este se pude medir la señal con una buena configuración de este.

<img src="">
Volver al [INICIO](#GNURADIO_LABCOMUIS_2025_1_B1B_G1)
