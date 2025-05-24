## Procedimneto

# Parte B_1

- Niveles de Cuantización y Resolución: Cuanto mayor sean los niveles de cuantización, mejor es la resolución de la señal cuantizada.

- Ruido de Cuantización y Filtros Pasa Bajo (LPF): El ruido al estar presente durante la cuantización, este genera que la señal luego de la cuantización presente algunas anomalías en su comportamiento, este ruido se puede minimizar aplicando un LPF.

- Frecuencia de Muestreo y Cuantización: Lo ideal es que sea ligeramente mayor que la frecuencia máxima de la señal original antes de cuantización así se preserva la forma de onda original y se minimiza el ruido introducido por la cuantización.

- Efecto del Ruido Gaussiano en el Cuantizador: El ruido Gaussiano como tal no afecta el desempeño del cuantizador ya que este depende mas de la resolucion de nuestro cuantizador. al estar presente al momento de cuantizarla puede ocacionar que en algunos casos se tome una mayor amplitud a la que se deberia muestrear, como sucede en el caso de la modulacion (DPCM).

- Ventajas y Desventajas del Cuantizador No Uniforme: La desventaja del uso de un modelo de cuantizador no uniforme es que este puede aumentar la amplitud del ruido que posee baja amplitud, la principal ventaja es que este modelo de cuentizador no uniforme, puede tener una mejor resolucion frente a modelo Uniforme.

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

