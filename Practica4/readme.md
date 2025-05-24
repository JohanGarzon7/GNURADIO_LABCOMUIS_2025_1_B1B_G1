# Laboratorio de Comunicaiones 

## Universidad Industrial de Santander

# Practica 4

### Integrantes

- Daniel Leonardo Gonzalez Gamba - 2215727
- Johan Esneider Garzon Espejo -2215588

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asi mismo, los autores asumen plena responsabilidad por la información contenida en este documento. 
---

---
# Palabras Clave 
`Modulacion Angular ` ,`Banda Estrecha`,`Banda Ancha`, `Frecuencia`,
`BESSEl`,`Modulacion PM`.

# Resumen 
Se conectó una señal coseno como entrada y se observó en el dominio del tiempo y frecuencia. Para modulación angular de banda estrecha y banda ancha se analizaron dos casos en el osciloscopio: la señal se mantuvo parecida a una portadora con pequeña variación de fase. Se calculó la potencia de la envolvente compleja, y se notó que las características de la señal mensaje (como su frecuencia) se reflejan en esas pequeñas variaciones..

# Objetivo General

Entender y comprender las modulaciones angulares de tanto tipo de banda estrecha como el tipo de banda ancha junto con el uso de GNU Radio. 

# Introduccion

Se genero un montaje en la aplicacion de GNU Radio para poder facilitar las respecttivas modificaciones para variar nuestra señal para asi poder comprender las Modulaciones tanto de banda estrecha como las de banda ancha sin embargi esto no quedo aqui si no que junto con el USRP mandamos
las señales a nuestro Osicloscopio y Analizador de espectros para realizar un mejor analisis desde estos y comparar los de inmediato los datos 
preacticos junto con los datos teoricos.

# Procedimiento

## Diseño en GNU para practica 

Para este apartado lo que se debio de hacer fue algo sencillo ya que simplemente basto con descargar la base del archivo .grc ya dado para simplemente guardarlo y emepezar
la practica lo que debemedo de visualizar en GNU fue lo siguiente

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica4/Images/WhatsApp%20Image%202025-05-17%20at%208.17.41%20AM%20(6).jpeg">

## Modulacion de Banda Estrecha y Banda Ancha

La señal mostrada en el osciloscopio bueno la señal mostrada en dicho aparato en una senañl modulada
y en esta foto podemos obeservar una portadora ane alta frecuencia cuya amplitud varia en dicha imagen podemos visualizar una envolvente compleja y ahora podemos variar en alguno de los 2 casos posibles y es cuando nuestro kp*Am<0.1 o cuando nuestro kp*Am>5 dando nos asi dos señales distintas en nuestro oscilocopio y como ya mencionamos la señal se ve mas o menos como un seno de mejor manera por asi decirlo en cuanto sea mayor que 5 mientra que cuanto es menor a penas se ven los picos es como si mi 
señal fuese un poco mas constante.


<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica4/Images/WhatsApp%20Image%202025-05-17%20at%208.17.41%20AM%20(6).jpegg">

Y en caunto al analizador de espectro segun las modulacion de los 2 tipos posible que se realizansen salio distintos tipos de picos en nuestro analizador y para hallar el ancho de banda utilizamos nuestro nivel de referecnia que se igual a 20dbm 

<img src="https://github.com/JohanGarzon7/GNURADIO_LABCOMUIS_2025_1_B1B_G1/blob/main/Practica4/Images/WhatsApp%20Image%202025-05-17%20at%208.17.40%20AM%20(1).jpeg">
  
## Calcule los coeficientes de Bessel

Y para este ultimo apartado de la practica solo se tomo los valores de potencia de cada uno de los picos visto en nuestro analizador de espectro para asi poder llenar nuestra tabla de beesel y hallar 
dichos coeficientes directamnete en esta practica se pudo ver cuanto deberia de ser el valor teorico
como el valor real obtenido de la tabla el cual calcula en base a la potencia de cada uno de los picos

# Conclusiones:
## 1.)
El cálculo del índice de modulación indica que la variación de amplitud es considerable, lo que resulta en una señal modulada fácilmente discernible visualmente y con una distribución de potencia notable entre la portadora y las bandas laterales.
## 2.)
Se pueden extraer parámetros clave de la señal mensaje directamente del osciloscopio: A pesar de ser una señal modulada compleja, el osciloscopio permite determinar características esenciales de la señal moduladora.

Volver al [INICIO](#GNURADIO_LABCOMUIS_2025_1_B1B_G1)
