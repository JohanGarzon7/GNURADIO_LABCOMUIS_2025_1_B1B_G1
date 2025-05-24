
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

Se redujo la frecuencia del mensaje a 10 Hz y se incrementa el ancho del pulso a 10 ms. La señal modulada presenta una forma envolvente suave y continua, más similar a la señal analógica original. El aumento del ancho de pulso incrementa la duración de cada muestra, lo que afecta la reconstrucción de la señal.  

<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/sen.png?raw=true" width="400">
</p>  
Ahora con una señal Diente de sierra:  

En este caso, se eleva la frecuencia del mensaje a 80 Hz con un ancho de pulso de 20 ms. La forma de la señal modulada tiende a parecerse a una señal de rampa, modulada por pulsos de mayor duración. Esto implica una menor resolución temporal, pero permite ver con claridad el seguimiento de la señal original.  
<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/Cierra.png?raw=true" width="400">
</p> 


### Analisis de resultados primer punto  

Se comprobó que, con una correcta elección de los intervalos y del ancho de los pulsos, las señales pueden multiplexarse sin pérdida de información ni solapamiento. Esto se evidenció en los diagramas de muestreo y en la ausencia de interferencias entre señales.

### Segundo punto  
Para el desarrollo de este punto partimos ddel concepto de multiplezacion de diferentes señales, el cual se debe realizar primero la modificacion de la frecuencia del mensaje y la frecuencia de pulsos, esto con el fin de generar un espacio en el cual nuestras señales en este caso cuatro con unretardo de una respecto a la otra.  
A continuacion se presenta un ejemplo con las cuatro señales multiplexadas:  
<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/multiplexacion.png?raw=true" width="400">
</p>  
Como podemos ver que cada señal tiene su propio intervalo ya antes dichos, y efectivamente podemos notar que ninguna de las señales se solapan entre sí, y esto nos ayuda que ninguna de estas señales pierda información cuando se se multiplexan.  
Agregando una nueva señal, en este caso una señal de audio, como ya sabemos es una señal aleatoria pero que aun asi se puede modular, para esto debemo disminuir la feecuencia del mensaje y aumentando la frecuencia de pulsos.  
<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/multiplezacionx2.png?raw=true" width="400">
</p>  

### Analisis de resultados 2do punto


Volver al [INICIO](#GNURADIO_LABCOMUIS_2025_1_B1B_G1)
