
# Laboratorio de Comunicaiones 

## Universidad Industrial de Santander

# Practica 1

### Integrantes

- Daniel Leonardo Gonzalez Gamba - 2215727
- Johan Esneider Garzon Espejo -2215588

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha de entrega

24 de Mayo de 2025

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asimismo, los autores asumen plena responsabilidad por la información contenida en este documento. 
---

---
# Palabras Clave 
`GNURADIO` ,`Osciloscopio`,`Analazidor de espectros`, `Frecuencia`,
`URRP 2920`.

# Resumen 
Se realizó el análisis de la modulación PAM (Pulse Amplitude Modulation) por muestreo natural en los dominios del tiempo y la frecuencia, utilizando diferentes formas de onda como señales moduladoras. Se ajustaron parámetros clave como la frecuencia de pulsos, frecuencia del mensaje, ancho de pulso y amplitud. Se observaron variaciones en la forma y el espectro de las señales moduladas al modificar dichos parámetros.

Cada señal ocupa un intervalo específico, evitando el solapamiento entre canales y asegurando la integridad de la información al multiplexar. Al incorporar un quinto canal, se recalcularon los retardos para mantener una separación del 20% entre señales (D1 = 0, D2 = 20, ..., D5 = 80), logrando una multiplexación eficiente sin interferencias.

Este estudio confirma la importancia de una adecuada relación entre la frecuencia de muestreo y la señal del mensaje (recomendada como 100:1) para garantizar una representación precisa de la señal original y una transmisión eficiente.

# Objetivo General

Analizar el proceso de modulación PAM por muestreo natural, evaluando el comportamiento de las señales moduladas en el dominio del tiempo y la frecuencia, y comprendiendo la influencia de parámetros como la frecuencia de muestreo, ancho de pulso y amplitud, con el fin de garantizar una multiplexación eficiente sin pérdida de información.

# Introduccion

La modulación por amplitud de pulsos (PAM) es una técnica fundamental en la transmisión digital de señales analógicas, como voz y video. En este informe se analiza el muestreo natural aplicado a diferentes formas de onda, evaluando cómo parámetros como la frecuencia de muestreo, el ancho de pulso y la separación entre canales afectan la representación y transmisión de la señal original. El estudio incluye tanto el análisis en el dominio del tiempo como en el de la frecuencia, asegurando una correcta multiplexación sin interferencia entre señales.

# Procedimiento

## PARTE A:  

Para analizar la modulación por amplitud de pulsos (PAM) mediante muestreo natural, se siguió un procedimiento estructurado en etapas, utilizando la herramienta GNU Radio para la generación, visualización y análisis de las señales.  


### Diseño del sistema en GNU Radio  

Se creó un bloque jerárquico denominado MODULADOR DE PULSOS, que permitió estructurar el sistema de muestreo y modulación. Este bloque integró una señal moduladora analógica (por ejemplo, una onda seno) y una portadora digital (trenes de pulsos).  


### Configuración de señales  

Se configuraron diferentes tipos de señales moduladoras (senoidal, triangular, diente de sierra) y se ajustaron parámetros como:  


-Frecuencia de muestreo  

-Ancho de los pulsos  

-Duración de la señal  

### Visualización en el dominio del tiempo y frecuencia  

Se observaron los efectos del muestreo natural sobre las formas de onda utilizando bloques de visualización en GNU Radio:  

-Diagramas temporales que mostraban cómo se ve la señal después del muestreo.  

-Espectros de frecuencia para identificar los componentes espectrales de la señal PAM.  


### Multiplexación de señales  

Se aplicó multiplexación por división de tiempo (TDM), asignando intervalos separados a cada canal. Se realizó el experimento con cuatro señales inicialmente, observando que no se producía solapamiento gracias a la separación de los intervalos.  

Posteriormente, se agregó un quinto canal, ajustando la separación al 20% para garantizar la no interferencia, como se muestra en los diagramas generados.  

### Imagenes de analisis  
Para el analisis de las señales moduladas, vamos a dar inicio a la primera señal la cual es una señal triangular:  

Se genera un tren de pulsos con una frecuencia de 1000 Hz y una señal de mensaje de 50 Hz con un ancho de pulso de 4 ms. La señal resultante presenta pulsos con amplitud que varía en forma triangular, esta forma de muestreo permite observar claramente cómo la amplitud de cada pulso corresponde a un valor instantáneo de la señal original.  

<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/TRIANGULAR.png?raw=true" width="400">
</p>  

Seguido de esto damos paso a visualizar la siguiente señal la cual es una señal sinosuidal:  

<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/sen.png?raw=true" width="400">
</p>  
### Análisis de resultados
Se comprobó que, con una correcta elección de los intervalos y del ancho de los pulsos, las señales pueden multiplexarse sin pérdida de información ni solapamiento. Esto se evidenció en los diagramas de muestreo y en la ausencia de interferencias entre señales.

## Simulacion de Señales en GNU Radio

En este aparto veremos como se modelaron las diferentes señales y como se muestrean dependiendiendo el tipo de modulacion que estamos trabajando:  


Para simular esto utilizamos el siguiente flujograma de GNURADIO [`simple_flowgraph.grc`](https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica1/Practica1C/simple_flowgraph.grc).  
Eh identificamos los bloques necesarios para el funcionamiento de nuestro programa:  



Ahora con esto podemos analizar y reponder cual es la diferencia entre una una fuente de tipo flotante y una de tipo complejo y esa es s que se genera una señal sinosoidal real mientras que en el tipo complejo se genera una señal real e imaginaria una desfada 90 grados de la otrra en banda base lo cual vendria siendo una señal exponecial compleja.

Como bien se vio la forma de onda afecta a la distribuccionde energia a que se debe esto esta genera mas ruido en el dominio de la frencuencia, en señales como la cuadrada o diente de cierra este ruido es mayor, mientras que en señales como sinusoidales este ruido es minimo.  

Ahora si se modifican distintos parametros como la amlitud, el offset,etc... de la señal, esta se visualizara en la grafica del dominio del tiempo mientras quye el el dominio de la frecuencia su ganancia se vera alterada.  

Al aumentar la amplitud en el dominio del tiempo, esta causa que se genere mas ganancia en el espectro de frecuencia.

## Transmisión y Medición de Señales con el USRP 2920

Para este apartado transmitiremos señales usando el USRP 2920 y medimos parámetros clave como potencia, ancho de banda, piso de ruido y relación señal a ruido (SNR).

## Analisis de resultados
### Actividad 3: Transmisión y Medición de Señales con el USRP 2920
Para la transmision de y medicion de Señales haciendo uso del USRP 2920, como primer paso se debe configurar el dispositivo, primero debemos crear un flujograma para que se pueda conectar mediante el reloj del computador, también debe conectar el lan y el cable tx/rx para transimitir la señal.  
El flujograma posee algunos parametro sque pueden afectr la potencia de la señale transmitida tales  como la amplitud, el ofset, el ruido de voltaje y el ancho de banda de resolucion. Es te ultimo se puede medir directamente desde el analizador de espectros, para esto se debe modificar como se ve la informacion en el analizador de espectros por lo que se debe varias la frecuencia central a una mas adecuada y poner un nivel de referencia con uno de los marcadores para luego poner otro marcador al otro punto de la señal.  
para calcular la SNR de la señal se hace uso de la ecuacion:  
    SNR = 10 log10 (Potencia de la señal / Potencia de ruido)


Al varias la ganancia del USRP se observan cambios en la potencia, una mayor amplitud, puede aumentar el ruido y mejorar el SNR.  
Respondiendo a la pregunta se "¿Es posible medir o estimar la potencia de la señal observada en el osciloscopio? ¿Por qué?" la respuesta es principalmente por que el osciloscopio es echo para medir volatajes sin potencia, sin embargo si se puede estimar con la relación:  
$\ P = \frac{V^2}{R} \$ 
### Actividad 4
Las concluisones que se pueden observar sobre la relacion entre la potencia de la señal y la calidad de la comunicacion esque es importante encontrar un equilibrio entre la potencia y otras cosas a tener en cuenta (consumo,interferencia) entre este y más apartados. El piso de ruido afecta la capacidad de detectar sanales debiles dado que si el piso de ruido es demaciado "Abosrveria" la señal y no se podría analizar debidamente.  
Las limitaciones que presentan algunos equipos para realizar las mediciones de ancho de banda y precision en las mediciones es dependiendo del dispositivo al que mencionemos como ejemplo tenemos el Osciloscopio R&S RTB2004 el cual posee un rango de frecuencia: 5Khz a 1Ghz es en cuanto a limitaciones, con el analizador de espectros y una señal que se comporta en el rango de frecuencias permitido para este se pude medir la señal con una buena configuración de este.
Para mejorar las mediciones de la señal en un entorno con alto nivel de ruido se puede optar por estrategias como relizar filtros pasabajas, pasa altas que pueden ayudar a eliminar e ruido no deseado, aumentar la potencia de transmicion de la señal ya que generaria una mayor diferencia entre la señal que se desea trasnmitir y el nivel de ruido.  
Algunas de las aplicaciones practicas del uso de mediciones de potencia y ancho de banda es el diseño de sistemas de radio y televicion ya que estos permiten asegurar que la transmision cumpla con los requisitos para una buena calidad.  
# Conclusiones:
## 1.)
Se logró obtener un mejor manejo y uso de los equipos de laboratorio adaptandoce a los nuevos equipos con mucha mas facilidad a lo largo de las practicas que se requerian en cada una de las diferentes actividades.
## 2.)
A lo largo de la práctica, se observaron diversos fenómenos estudiados previamente en el curso teórico, lo que facilitó su comprensión y permitió identificar factores que influyen en la transmisión de señales de información. Además, mediante el uso del programa GNU Radio, se generaron distintos tipos de señales, ajustando diversos parámetros para modificar sus características.
## 3.)
El uso de las comunicaciones en el mundo moderno parten de los conocimientos que se obtienen a lo largo del curso de comunicaciones, esto se debe a que se profundiza y se pone en practica lo aprendido en el curso teorio facilitando mas aun el analisis de diferentes sistemas de comunicacion.  

Volver al [INICIO](#GNURADIO_LABCOMUIS_2025_1_B1B_G1)
