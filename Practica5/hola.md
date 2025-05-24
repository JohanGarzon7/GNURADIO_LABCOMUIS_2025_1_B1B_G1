## Procedimneto

### 1. Niveles de Cuantización y Resolución

Cuanto mayor sean los niveles de cuantización, mejor es la resolución de la señal cuantizada.

### 2. Ruido de Cuantización y Filtros Pasa Bajo (LPF)

El ruido al estar presente durante la cuantización, este genera que la señal luego de la cuantización presente algunas anomalías en su comportamiento, este ruido se puede minimizar aplicando un LPF.

### 3. Frecuencia de Muestreo y Cuantización

Lo ideal es que sea ligeramente mayor que la frecuencia máxima de la señal original antes de cuantización así se preserva la forma de onda original y se minimiza el ruido introducido por la cuantización.

### 4. Efecto del Ruido Gaussiano en el Cuantizador

El ruido Gaussiano como tal no afecta el desempeño del cuantizador ya que este depende mas de la resolucion de nuestro cuantizador. al estar presente al momento de cuantizarla puede ocacionar que en algunos casos se tome una mayor amplitud a la que se deberia muestrear, como sucede en el caso de la modulacion (DPCM).

### 5. Ventajas y Desventajas del Cuantizador No Uniforme

La desventaja del uso de un modelo de cuantizador no uniforme es que este puede aumentar la amplitud del ruido que posee baja amplitud, la principal ventaja es que este modelo de cuentizador no uniforme, puede tener una mejor resolucion frente a modelo Uniforme.
