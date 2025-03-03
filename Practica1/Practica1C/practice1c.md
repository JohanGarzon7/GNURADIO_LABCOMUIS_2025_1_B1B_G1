
# Práctica 1C. Mediciones de potencia y frecuencia

## **Objetivo General**
Familiarizarse con el uso de herramientas de software definido por radio (SDR) como GNU Radio, junto con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. Los estudiantes aprenderán a medir y analizar parámetros clave en comunicaciones, como potencia, ancho de banda, relación señal a ruido (SNR) y piso de ruido.

---

## **Materiales y Equipos**
- **USRP 2920**: Radio definido por software.
- **Osciloscopio R&S RTB2004**: Para visualización de señales en el dominio del tiempo y frecuencia.
- **Analizador de Espectros R&S FPC1000**: Para mediciones en el dominio de la frecuencia.
- **Computador con GNU Radio**: Para simulación y generación de señales usando el USRP 2920.
- **Cables y conectores**: Para interconexión de equipos.

---

## **Actividad 1: Revisión de Especificaciones de los Equipos**

### **Objetivo**
Familiarizarse con las especificaciones técnicas de los equipos de laboratorio y entender cómo configurarlos para realizar mediciones.

### **Procedimiento**
1. **Revisar Manuales y Verificar Equipos**:
   - Revisar las especificaciones de los equipos de laboratorio (USRP 2920, Osciloscopio R&S RTB2004 y Analizador de Espectros R&S FPC1000).
   - Identificar las principales funciones y controles de los equipos.

2. **Seleccionar Especificaciones Relevantes**:
   - Seleccionar las **5 especificaciones** que consideren **más relevantes** de cada equipo. 

3. **Configuración de los Equipos**:
   - **USRP 2920**: Identificar el rango de frecuencia y ganancia configurable del radio. Para esto, conecte la alimentación y el cable de red al radio, y desde un terminal (Ctrl + Alt + T) ejecute el comando `uhd_usrp_probe`.
   - **Osciloscopio R&S RTB2004**: Identificar el ancho de banda máximo, resolución vertical y tipos de mediciones soportadas.
   - **Analizador de Espectros R&S FPC1000**: Identificar el rango de frecuencia, resolución y figura de ruido.

### **Preguntas Orientadoras**
1. ¿Cuál es el rango de frecuencia del USRP 2920 y cómo se compara con el del analizador de espectros?

   El rango de frecuencias es de 50MHz a 2.2GHz.
2. ¿Qué parámetros del USRP 2920 se deben configurar para transmitir una señal en una frecuencia específica?

   Primero se debe conectar con el reloj del PC,Frecuecia central, Amplitud, Anch de banda.
3. ¿Cómo se configura el osciloscopio para medir la amplitud y la frecuencia de una señal?
   Se configura la escala de division osea los volts por divicion ademas del la
   posicion horizontal tambien es importante para un buena medicion, se puede agregar de igual manera cualquier medida que se necesite de la señal el periodo la frecuencia etc..   
4. ¿Qué diferencia hay entre medir una señal en el dominio del tiempo (osciloscopio) y en el dominio de la frecuencia (analizador de espectros)?
   Que con el osciloscopio en el dominio de tiempo se puede calcular la amplitud de la señal y en el analizador de espectros la potencia y ancho de banda.   
5. ¿Cómo se mide el piso de ruido en el analizador de espectros? ¿Cómo afecta la frecuencia central, SPAN y RBW la medida de piso de ruido? ¿Por qué?
   Se mide con el analizador de espectros mas especificamente con el RBW aumentar o disminuir el span requiere de mas o menos costo computacional ya que puede llegra a ser medida la señal de una manera mas precisa.

### **Evidencia**
- Lista con las 5 especificaciones más relevantes de cada equipo.
- USRP-2920
  . Ancho de Banda: 20MHz
  . Rango de frecuencia: 50MHz a 2.2GHz
  . Paso de frecuencia: <1KHz
  . Rango de ganacia: 0 dB a 31 dB
  . Potenca tipica. 12W a 15W
- Analizador de Espectros R&S FPC1000
  . Numero de canales: 1
  . Ancho de banda: 1Hz
  . Impedancia de entrada: 50 ohm
  . Maximo samp_rate: 2.5Gsamples/s
  . Resolucion de frecuencia: 1 Hz
- Osciloscopio R&S RTB2004
  . Impedancia de entreda: 1M ohm
  . Numero de canales: 4
  . Resolucion: 14 bit
  . Rango de frecuencia: 5Khz a 1Ghz
  . Canales digitales
- Realice una medición de piso de ruido normalizado.

---

## **Actividad 2: Simulación de Señales en GNU Radio**

### **Objetivo**
Generar y analizar señales en GNU Radio para entender cómo se comportan diferentes formas de onda en tiempo y frecuencia.

### **Procedimiento**
1. **Iniciar GNU Radio**:
   - Ejecute GNU Radio Companion (GRC) (`gnuradio-companion`).
   - Cargue el flujograma [`simple_flowgraph.grc`](https://github.com/omreyes/LabComUIS/blob/develop/guides/practice1/simple_flowgraph.grc).
   - Identifique los bloques principales: `Signal Source`, `Throttle`, `QT GUI Time Sink` y `QT GUI Frequency Sink`.
   - Configure la frecuencia de muestreo (samp_rate) en 20 kHz.

2. **Ejecutar el Flujograma**:
   - Ejecute el flujograma y observe los diferentes controles (Source Controls, Channel Controls, USRP Controls), así como las señales generadas en las ventanas de tiempo (`Time Sink`) y frecuencia (`Frequency Sink`).
   - Identifique y relacione los bloques presentes en el flujograma con lo observado en la ventana de ejecución.
  
3. **Análisis de Señales** 
   - Analice y valide los resultados en el dominio del tiempo y de frecuencia si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
   - Modifique el nivel de ruido del modelo de canal y analice el efecto en tiempo y frecuencia.

### **Preguntas Orientadoras**
1. ¿Cómo se puede explicar matemáticamente la diferencia entre una fuente de tipo flotante y una de tipo complejo?
   La diferencia entre tipo flotante es que se genera una señal sinosoidal real mientras que en el
   tipo complejo se genera una señal real  e imaginaria una desfada 90 grados de la otrra en banda base lo cual vendria siendo una señal exponecial compleja. 
2. ¿Cómo afecta la forma de onda a la distribución de energía (potencia) en el dominio de la frecuencia?
   La distribuccion de potenca si cambiamos la forma de la onda, esta genera mas fuido en el dominio de la frencuencia, en señales como la cuadrada o diente de cierra este ruido es mayor, mientras que en señales como sinusoidales este ruido es minimo.
   
3. ¿Qué sucede con la señal en el dominio del tiempo y la frecuencia si se modifican los diferentes parámetros de la fuente? ¿Lo observado corresponde a lo esperado teóricamente?
Si modificamos la amlitud, el offset,etc... de la señal, esta se visualizara en la grafica del dominio del tiempo mientras quye el el dominio de la frecuencia su ganancia se vera alterada.
4. ¿Cómo se relaciona la amplitud de la señal con la potencia observada en el dominio de la frecuencia?
Al aumentar la amplitud  en el dominio del tiempo, esta causa que se genere mas ganancia en el espectro de frecuencia.
5. ¿Qué diferencias se observan entre una señal senoidal y una señal cuadrada en el dominio de la frecuencia?
La cantidad de ruido que se genera en el espectro de frecuencia, esto debido a cambios  en su amplitud de mantera casi instantanea.
### **Evidencias**
- Capturas de pantalla de señales generadas en el dominio del tiempo y la frecuencia que evidencien cada una de las comparaciones realizadas.

---

## **Actividad 3: Transmisión y Medición de Señales con el USRP 2920**

### **Objetivo**
Transmitir señales usando el USRP 2920 y medir parámetros clave como potencia, ancho de banda, piso de ruido y relación señal a ruido (SNR).

### **Procedimiento**
1. **Configurar el USRP 2920**:
   - Configure el flujograma en GNU Radio para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presionando `E` (enable) o `D` (disable), respectivamente.
   - Identifique el bloque de frecuencia de muestreo (samp_rate) y observe el efecto de cambiar su valor (e.g. 10 kHz).
   - Configure la frecuencia de muestreo (samp_rate) en 1 MHz.
   - Verifique el efecto de modificar la frecuencia y ganancia del USRP. 

2. **Medición con el Analizador de Espectros**:
   - Conecte la salida del USRP al analizador de espectros.
   - Mida el piso de ruido normalizado a la frecuencia de portadora que va a utilizar.
   - Compare el espectro de la señal observada en el analizador de espectros con la observada en la pantalla de simulación. Tenga en cuenta que el radio (USRP) equivale al diagrama de bloques mostrado en la figura.

<img src="qam_modulator.png" alt="QAM Modulator" width="400">
     
   - Analice y valide los resultados en el dominio de la frecuencia si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
   - Mida potencia de la señal transmitida y ancho de banda de diferentes señales generadas.
   - Conecte una antena apropiada a la entrada del analizador de espectros y observe el espectro de una señal FM (las estaciones FM se sitúan entre los 88 MHz y 108 MHz). Mida su ancho de banda y relación señal a ruido. 
   - Determinar la máxima potencia de transmisión.
   - Evalúe la respuesta en frecuencia del canal midiendo los cambios de ganancia del sistema cuando varía la frecuencia de portadora.
   - Compare los resultados de transmitir usando un cable y usando antenas.

4. **Medición con el Osciloscopio**:
   - Analice y valide los resultados en el dominio del tiempo si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
  - Contraste estos resultados con los obtenidos con el analizador de espectros.

5. **Cálculo de la Relación Señal a Ruido (SNR)**:
   - Usar las mediciones de potencia y piso de ruido para calcular la SNR de algunas de las señales generadas.
   - Anotar el valor de la SNR en dB.

### **Preguntas Orientadoras**
1. ¿Cómo se configura el USRP 2920 para transmitir una señal en una frecuencia específica?
   Para poder transimitir las señales con el USRP 2920 primero debemos crear un flujograma para que se pueda conectar mediante el reloj del computador tambien debe conectrase el lan y el cable tx/rx para transimitir la señal 
2. ¿Qué parámetros del flujograma afectan la potencia de la señal transmitida?
   La amplitud el offset el ruido de voltaje y el anco de banda de resolucion.
3. ¿Cómo se mide el ancho de banda de la señal transmitida en el analizador de espectros?
   
4. ¿Cómo se calcula la relación señal a ruido (SNR) a partir de las mediciones de potencia y piso de ruido?
7. ¿Qué diferencias se observan en las mediciones de potencia cuando se varía la ganancia del USRP?
8. ¿Es posible medir o estimar la potencia de la señal observada en el osciloscopio? ¿Por qué?

### **Evidencia**
- Capturas de pantalla de señales generadas en el dominio del tiempo y la frecuencia que evidencien las principales comparaciones realizadas.
- Captura de la señal FM usada para medición de ancho de banda.

---

## **Actividad 4: Análisis de Resultados y Conclusiones**

### **Objetivo**
Analizar los resultados obtenidos y sacar conclusiones sobre el comportamiento de las señales en diferentes condiciones para elaborar el informe.

### **Para la Elaboración del Informe**
1. **Comparar Resultados**:
   - Compare los resultados obtenidos en las simulaciones y las transmisiones reales.
   - Discuta las diferencias entre las mediciones realizadas con el osciloscopio y el analizador de espectros.

2. **Reflexionar sobre la SNR**:
   - Analice la importancia de la relación señal a ruido (SNR) en las comunicaciones inalámbricas.
   - Discuta cómo el piso de ruido afecta la capacidad de detectar señales débiles.

3. **Conclusiones Finales**:
   - Escriba conclusiones basadas en los resultados obtenidos.
   - Reflexe sobre las limitaciones de los equipos y cómo se podrían mejorar las mediciones.

### **Preguntas Orientadoras**
1. ¿Qué conclusiones se pueden obtener sobre la relación entre la potencia de la señal y la calidad de la comunicación?
2. ¿Cómo afecta el piso de ruido a la capacidad de detectar señales débiles?
3. ¿Qué limitaciones tienen los equipos utilizados en términos de ancho de banda y precisión en las mediciones?
4. ¿Cómo se pueden mejorar las mediciones de señal en un entorno con alto nivel de ruido?
5. ¿Qué aplicaciones prácticas tienen las mediciones de potencia y ancho de banda en sistemas de comunicaciones reales?
6. ¿Cómo se puede medir la respuesta en frecuencia de un canal alámbrico?
7. ¿Cómo se puede obtener un modelo sencillo de las pérdidas (_pathloss_) en un canal inalámbrico?
