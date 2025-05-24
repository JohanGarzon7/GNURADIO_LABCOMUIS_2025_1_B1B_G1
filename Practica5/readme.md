
# Laboratorio de Comunicaiones 

## Universidad Industrial de Santander

# Practica 5

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

Para analizar la modulación por amplitud de pulsos (PAM) mediante muestreo natural, se siguió un procedimiento estructurado en etapas, utilizando la herramienta GNU Radio para la generación, visualización y análisis de las## Procedimneto

# Parte B_1

- Niveles de Cuantización y Resolución: Cuanto mayor sean los niveles de cuantización, mejor es la resolución de la señal cuantizada.

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/Snapshot_2025-05-23_23-55-02.png">

- Ruido de Cuantización y Filtros Pasa Bajo (LPF): El ruido al estar presente durante la cuantización, este genera que la señal luego de la cuantización presente algunas anomalías en su comportamiento, este ruido se puede minimizar aplicando un LPF.

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/Snapshot_2025-05-23_23-57-53.png">

- Frecuencia de Muestreo y Cuantización: Lo ideal es que sea ligeramente mayor que la frecuencia máxima de la señal original antes de cuantización así se preserva la forma de onda original y se minimiza el ruido introducido por la cuantización.

- Efecto del Ruido Gaussiano en el Cuantizador: El ruido Gaussiano como tal no afecta el desempeño del cuantizador ya que este depende mas de la resolucion de nuestro cuantizador. al estar presente al momento de cuantizarla puede ocacionar que en algunos casos se tome una mayor amplitud a la que se deberia muestrear, como sucede en el caso de la modulacion (DPCM).
  
<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/Snapshot_2025-05-24_00-00-31.png">

- Ventajas y Desventajas del Cuantizador No Uniforme: La desventaja del uso de un modelo de cuantizador no uniforme es que este puede aumentar la amplitud del ruido que posee baja amplitud, la principal ventaja es que este modelo de cuentizador no uniforme, puede tener una mejor resolucion frente a modelo Uniforme.
  
<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/Snapshot_2025-05-24_00-01-01.png">

# Parte B_2

- Aumenta o disminuye el ruido de la señal filtrada segun sea su valor determinado.

-  La posibilidad de obtener una mejor resolucion en la señal cantificada.

-  En un cuantizador no uniforme como el mostrado, el ancho de banda del canal afecta directamente la calidad de la señal cuantizada. Si el canal tiene un ancho de banda amplio, permite que pasen tanto las componentes útiles de la señal como el ruido de cuantización, lo que puede degradar la relación señal-ruido (SNR). En cambio, un ancho de banda moderado actúa como un filtro que atenúa las componentes de alta frecuencia introducidas por la cuantización, mejorando la calidad al reducir el ruido sin distorsionar significativamente la señal.

-  Tiene un impacto significativo en la calidad de la señal cuantificada y en la percepcion de ruido, aunque la ley A reduce el error de cuantización en señales de baja amplitud, el ruido gaussiano puede sumarse a la señal antes de la compresión.

-  Para optimizar la cuantización Ley A y mejorar la relación señal-ruido (SNR), se deben tener algunos aspectos en cuenta, tales como: El valor de la constante A,  el filtrado de la señal (LPF) y aumentar el numero de bits.

-  . Amplitudes= 70.8mV
- . Delta de amplitud=5..273 mV
- . Delta de tiempos= 8.7ms

- ..Ancho de banda= 62kHz
- ..Delta de frecuencia= 2.411 kHz
- ..Potencia = -25dB

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica5/Images/Snapshot_2025-05-24_00-03-44.png"> señales.  


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

### Primer punto
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


#### Analisis de resultados

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

#### Analisis de resultados  
Cada señal ocupa su propio intervalo previamente definido, y se puede observar que no hay superposición entre ellas. Esto garantiza que, al multiplexarlas, no haya pérdida de información en ninguna de las señales.
En el segundo punto se solicita añadir un nuevo canal, lo cual modifica la fórmula utilizada para calcular los intervalos. En lugar de 4 canales, ahora se consideran 5, lo que implica que la separación entre los intervalos de cada señal es del 20%. Como se muestra en la imagen, los retardos quedan distribuidos como: D1 = 0, D2 = 20, D3 = 40, D4 = 60 y D5 = 80. Esta separación asegura que no haya superposición entre señales.  


Volver al [INICIO](#GNURADIO_LABCOMUIS_2025_1_B1B_G1)
