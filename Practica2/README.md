# Laboratorio de Comunicaciones

## Universidad Industrial de Santander

# Práctica 2A. Modelo de canal

### Integrantes

- Daniel Leonardo Gonzalez Gamba - 2215727
- Johan Esneider Garzon Espejo -2215588

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asimismo, los autores asumen plena responsabilidad por la información contenida en este documento. 
---


---
# Palabras Clave 
`GNURADIO` ,`Osciloscopio`,`Analazidor de espectros`, `Frecuencia`,
`URRP 2920`.

# Objetivo General
Durante la práctica, los estudiantes tendrán la oportunidad de observar cómo estos modelos afectan la calidad de la señal transmitida y como pueden mitigar sus efectos. Además, se evaluarán aspectos clave como la relación señal-ruido y la eficiencia en la transmisión de datos.
Este enfoque práctico nos permitirá no solo verificar las teorías aprendidas en clase, sino también desarrollar habilidades prácticas en el manejo de los equipos de laboratorio como con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000.

# Materiales y Equipos
USRP  2920:  Radio definido por software.
Osciloscopio 	R&S RTB2004:  Para visualización de señales en el dominio del tiempo y  frecuencia.
Analizador 	de Espectros R&S FPC1000: Para mediciones en el dominio de la frecuencia.
Computador 	con GNU Radio: Para simulación y generación de señales usando el USRP 2920.
Cables y conectores: Para interconexión de equipos.


## Actividad 1: Actividades de simulación de canal en GNU Radio
### Objetivo: Familiarizarse con los fenómenos de canal en un ambiente simulado.
### Procedimiento
- Revisar Manuales y Verificar Equipos:
- Cargue el flujograma Enlace Descarga
- Configure siempre la frecuencia de muestreo (samp_rate) en 25e6/2n  Hz. donde n es un número entero mayor a 2.
  
¿Cuál es el efecto de filtrar las frecuencias altas de una señal periódica?   

Al filtrar hacias las altas frecuecnias obtenenmos una mejor resolucion en la señal a mostrar obteniendi la señal por completo.

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Captura%20desde%202025-03-23%2019-37-23.png">

¿Qué sucede al filtrar muy cerca de la frecuencia fundamental de la señal?  

Al filtrar muy cerca a la señal fundamental perdemos la componente fundamental haciendo asi que se pierda la parte mas importante de la señal.

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Captura%20desde%202025-03-23%2019-25-19.png">

¿Cuál es el efecto de filtrar las frecuencias bajas de una señal periódica?  

Al filtrar las frecuencias bajas de la señal vamos perdiendo los armonicos que componen a esta 

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Captura%20desde%202025-03-23%2019-23-53.png">

¿Qué ocurre al eliminar los primeros armónicos de la señal?
Explique el fenómeno de la desviación de frecuencia en una señal. Puede hacerlo con al menos dos casos.  

Al eliminar los armonicos de una señal  podemos observar un cambio en la forma de onda, perdemos calidad en la señal y el efecto de la desviacion en la frecuencia es que esta cambia con respecto a su espectador.  
- Efecto Doppler

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Captura%20desde%202025-03-23%2019-53-36.png">

Observe cómo se degrada la señal al aumentar los niveles de ruido. Analice su comportamiento en el dominio del tiempo.

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Captura%20desde%202025-03-23%2019-56-42.png">
  
	
## Actividad 2: fenómenos de canal en el osciloscopio

### Objetivo Familiarizarse con los fenómenos de canal en un ambiente simulado.

### Procedimiento

- Configurar el USRP 2920:
- Configure el flujograma (Enlace Descarga) en GNU Radio para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presione E (enable) o D (disable), respectivamente.
- Configure siempre la frecuencia de muestreo (samp_rate) en 25e6/2n  Hz. donde n es un número entero mayor a 2. 
- Encienda, conecte y configure el osciloscopio con el USRP 2920 con los parámetros necesarios para evidenciar los fenómenos de canal.

¿Cuál es el efecto del ruido sobre la amplitud de las señales medidas en el osciloscopio? Conservan las mismas relaciones que se evidencian en la simulación.   

¿la relación señal a ruido creada intencionalmente en el computador se amplifica o se reduce en la señal observada en el osciloscopio?  

demuestre ¿Cómo se puede mejorar la relación señal a ruido en una señal?  

¿Cómo se evidencia el fenómeno de desviación de frecuencia en el osciloscopio? 

Este se evidencia con por asi decirlo variaciones en la forma de onda lo que siginifica que se ve inestable por asi decirlo y en el osciloscopio se ve dezplazada la señal como se ve en la siguiente figura.

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Captura%20desde%202025-03-23%2021-52-59.png">

¿Cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? 

Afecta en la por asi decirlo en la fomra en la que se muetra la señal

¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?
Evidencia

## Actividad 3: fenómenos de canal en el analizador de espectro

### Objetivo Familiarizarse con los fenómenos de canal en un ambiente simulado.
### Procedimiento

- Configurar el USRP 2920:
- Configure el flujograma en GNU Radio (Enlace Descarga) para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presione E (enable) o D (disable), respectivamente.
- Configure siempre la frecuencia de muestreo (samp_rate) en 25e6/2n  Hz. donde n es un número entero mayor a 2. 
- Encienda, conecte y configure el analizador de espectro con el USRP 2920 con los parámetros necesarios para evidenciar los fenómenos de canal.

## Preguntas Orientadoras

¿Cuál es el efecto del ruido sobre la respuesta en frecuencia de las señales medidas en el analizador de espectro? Conservan las mismas relaciones que se evidencian en la simulación.   

¿La relación señal a ruido creada intencionalmente desde el computador se amplifica o se reduce en la señal observada en el analizador de espectro? 
adjunte la evidencia de la medición de la relación señal a ruido de dos formas de onda distintas.    

¿Cómo se evidencia el fenómeno de desviación de frecuencia en el analizador de espectro? evidencie al menos con dos formas de onda.    

Este se evidencia dado a que la señal se corre.


<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Captura%20desde%202025-03-23%2021-52-59.png">

¿Cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida?

Afecta principlamente en la disminucion de la potencia entregada en el receptor dado que la atenuacion va por distancia recorrida por lo que al tener una mayor distancia que recorrer se recibe menos potencia. 

¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?  

El modelo de canal que mejor representa las mediciones es el canal con ruido aditivo blanco gaussiano (AWGN).
## Actividad 4: Efectos de los fenómenos de canal en la conversión de frecuencia  

Familiarizarse con los efectos de los fenómenos de un canal alámbrico e inalámbrico real en la conversión de frecuencia.

### Procedimiento

**Configurar el USRP 2920:**
   - Configurar el flujograma [filters_flowgraph.grc](filters_flowgraph.grc) en GNU Radio para **transmitir y recibir ** una señal a través del USRP.
   - Habilitar o deshabilitar los bloques correspondientes (`Channel Model`, `Throttle`, `UHD: USRP Sink`, `UHD: USRP Source`, `Virtual Sink`). Para esto, seleccione el bloque deseado y presione **E** (enable) o **D** (disable), respectivamente.
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2. Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.
   - Compare los resultados al recibir la señal usando diferentes medios (aire o cable coaxial).

### Preguntas Orientadoras

- ¿Cómo se evidencian los diferentes fenómenos de canal en la señal recibida?  
Los diferentes fenómenos del canal se evidencian en la señal recibida a través de variaciones en su amplitud, frecuencia y calidad. La atenuación se observa como una reducción en la amplitud respecto a la señal transmitida. El ruido afecta la claridad de la señal y puede detectarse como un aumento en el nivel de fondo en el analizador de espectros. La desviación de frecuencia se percibe como un desplazamiento en la frecuencia central, mientras que la distorsión e interferencias pueden manifestarse como alteraciones en la forma de la señal debido a reflexiones o multitrayectoria.  
- ¿Cómo se pueden mitigar los efectos del canal en la señal recibida?  
Para mitigar estos efectos, se pueden aplicar diversas estrategias. El uso de filtros digitales ayuda a reducir el ruido y mejorar la calidad de la señal. Incrementar la potencia de transmisión mejora la relación señal/ruido, permitiendo una mejor recepción. La elección del medio adecuado, como cables coaxiales en lugar de transmisión en aire, minimiza interferencias y pérdidas.
### Evidencia

A continuacion se evidencian algunas imagenes donde se puede observar diferentes señales transmitidas mediante antenas, recibidas y proyectadas tanto en osciloscopio y analizador de espectros donde se configuro previamente para un analisis optimo.  
-Señal cuadrada:  
<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Imagen de WhatsApp 2025-03-24 a las 12.07.18_8a996374.jpg">  
Una vez seleccionada y configurara la señal a transmitir se procede a proyectarla tanto en el analizador de espectro como en el osciloscopio, esto se puede lograr usando un conector adecuado que me permite conectar el cable coaxial de la antena receptora a los dos dispositivos de analisis.  
<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/WhatsApp%20Image%202025-03-23%20at%206.50.11%20PM.jpeg">
Se puede evidenciar la atenuacion ocacionada por el medio transmitido(aire) junto con otros factores a fectan la señal como el ruido externo.  

-Señal Sinusolidal modulada en cuadratura:  
Para transmitir esta señal se deben realizar unos ajustes en el softwaare para modularla, ajustanto valores como la forma de la onda, fecuencia de la señal base, amplitud de la señal base, frecuencia de la portadora, ganancia de la trasnmicion,ruido del canal...  
<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica2/Imagenes/Imagen%20de%20WhatsApp%202025-03-24%20a%20las%2012.07.17_82caf0c2.jpg" width= '650'>  
</p>
Una vez generada la señal y confugurada adecuadamente se procede a visualizar en los dispositivos:
<p align="center">
  <img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/eefaca5856543cc553d29ae2e7121ba8546588ff/Practica2/Imagenes/Imagen%20de%20WhatsApp%202025-03-24%20a%20las%2012.07.17_21e82e8c.jpg" width="650">
</p>


Igualmente se vuelve a visualizar una atenuacion y precencia de ruido en la señal recibida.
