# Puzzle UT2 · Pieza NN: Nombre de la pieza
Grupo: Maisara Aldana (@maiswth) · Morena Macias (@M0ren42)

### 1. ¿Qué es un HDD? vigencia y evolución

- **Definición:** Un disco duro (HDD) es un dispositivo de almacenamiento no volátil que conserva los datos aunque el ordenador está apagado. Utiliza platos magnéticos giratorios y cabezales para leer y escribir información.

Aunque los SSD ofrecen menor latencia y más operaciones de entrada y salida por segundo (IOPS), los HDD siguen siendo útiles para almacenar grandes cantidades de datos por su menor coste por terabyte. Su evolución busca aumentar la densidad de almacenamiento: guardar más información en el mismo espacio.

#### Jerarquía de memoria y E/S
- **Definición:** es la forma en que se organizan los diferentes tipos de memoria de un ordenador según su velocidad, capacidad y coste. Las memorias más rápidas utilizan tecnologías más costosas y necesitan estar muy cerca del procesador. **Cada nivel es caché del inferior**.

#### ¿Cómo se organiza?
| Nivel | Tipo de memoria | Función |
|---|---|---|
| 1 | Registros | Guardan datos que utiliza directamente la CPU |
| 2 | Caché L1 | Almacena datos de acceso muy frecuente |
| 3 | Caché L2 | Almacena más datos que L1 pero es algo más lenta |
| 4 | Caché L3 | Caché de mayor capacidad, compartida normalmente entre núcleos |
| 5 | RAM | Guarda programas y datos que se estan utilizando |
| 6 | SSD | Almacenamiento permanente rápido |
| 7 | HDD | Almacenamiento permanente de gran capacidad |

---

### 2. Componentes su funcionamiento y RPM

- **Los platos:** son los discos circulares, guardan los datos mediante magentisimo cubiertos de material magnético que encontramos dentro del HDD. En su superficie se organizan los datos en circunferencias concentricas llamas pistas (*traks*). Pueden utilizarse ambas caras.
- **Cabezales de lectura y escritura:** son unos componentes diminutos que se encargan de leer y escribir los datos en los platos.
    - *Escritura:* el cabezal modifica la orientación magnética de pequeñas regiones del plato para representar los datos.
    - *Lectura:* detecta las variaciones magnéticas de esas regiones.
- **Brazo actuador:** desplaza los cabezales hasta la pista donde se encuentran los datos.
- **Motor del eje (spindle):** hace girar los platos a una velocidad constante.

#### RPM (Revolutions Per Minute)
Indica cuantas vueltas completas realizan los platos de un disco duro en un minuto, las velocidades habituales son 5400 y 7200RPM. A mayor RPM, menor latencia rotacional, quiere decir que cuanto más rápido giran los platos, menos tiempo tenemos que esperar a que el sector deseado pase por debajo del cabezal. 

- **Ventajas:** al reducirse el tiempo de espera, generalmente se mejora el rendimiento (+ operaciones - tiempo). 
- **Desventajas:** mayor RPM también significa que el motor tiene que girar los platos a mayor velocidad y eso produce ruido, calor y un mayor consumo de energía.

---

### 3. Rendimiento y tiempo de acceso

El tiempo de acceso es el tiempo necesario para localizar y leer datos.

$$T_{\text{acceso}} = T_{\text{seek}} + T_{\text{rotacional}} + T_{\text{transferencia}}$$

- *Seek:* tiempo que tarda el cabezal en desplazarse hasta la pista correspondiente.
- *Latencia rotacional:* tiempo que espera hasta que el sector deseado pasa por debajo del cabezal.
- *Transferencia:* tiempo necesario para transmitir los datos.

#### Tabla resumen de características y unidades
| Característica | Unidad | Valores típicos hoy | Qué significa |
|---|---|---|---|
| Velocidad de giro | RPM (revoluciones por minuto) | 5.400 y 7200 RPM | Número de vueltas completas que realizan los platos del disco por minuto. |   
| Tiempo de busqueda (*Seek*) | Milisegundos (ms) | 8 a 12 ms | El tiempo que tarda el brazo actuador en desplazar el cabezal hasta la pista correspondiente. |
| Latencia rotacional | milisegundos (ms) | 4,17 ms (s 7.200 RPM) | El tiempo que espera el cabezal hasta que el sector deseado para por debajo debido al giro. |
| Tasa de transferencia | MB/s (Megabytes por segundo) | 150 a 250MB/s | La velocidad a la que se transmiten los datos una vez que el cabezal empieza a leerlos o escribirlos | 

#### 3.1. Acceso por bloques
La RAM permite acceder directamente a posiciones individuales de memoria direccionables por bytes. Sin embargo los dispositivos de almacenamiento, suelen trabajar mediante bloques de datos.

---

### 4. Memoria caché

- **Definición:** es una pequeña memoria temporal que está integrada en el disco duro, su función es almacenar datos durante un tiempo para facilitar y acelerar determinadas operaciones de lectura y escritura.

#### ¿Como ayuda a mejorar el rendimiento?

- **Operaciones de lectura:** el HDD almacena una copia temporal de los datos en su caché para entregarlos directamente si se vuelven a solicitar, lo que ahorra tiempo y reduce accesos físicos. Como su capacidad es limitada, estos datos no se conservan indefinidamente.
- **Operaciones de escritura:** el HDD almacena los datos temporalmente en su caché para que el firmware los organice y agrupe antes de guardarlos en los platos, lo que mejora el rendimiento y reduce los tiempos de espera.

#### ¿Por qué no es almacenamiento permanente?
La caché del disco duro no es permanente porque es memoria volátil (normalmente DRAM). A diferencia de los platos magnéticos, que guardan la información de forma definitiva incluso tras apagar el equipo, la caché solo mantiene los datos temporalmente mientras el disco funciona.

---

### 5. Tecnologías de grabación: CMR y SMR

Son dos formas de organizar las pistas donde se almacenan los datos en los platos de un HDD. La diferencia está en su distribución y afecta al rendimiento de escritura.

#### CMR (Conventional Magnetic Recording)
Las pistas se escriben **una al lado de la otra, sin solaparse**. Esto permite modificar una pista sin afectar a las vecinas y ofrece un rendimiento de escritura constante y predecible.

#### SMR (Shingled Magnetic Recording)
Las pistas se **solapan parcialmente** para almacenar más información en el mismo espacio. Sin embargo, modificar una pista puede obligar a guardar y reescribir datos de las pistas vecinas, ralentizando la escritura.

Su rendimiento depende del tipo de escritura:
    - **Secuencial:** los datos se escriben en orden, lo que reduce las reorganizaciones.
    - **Aleatoria:** los datos se modifican en distintas posiciones, lo que puede exigir más reorganizaciones y aumentar el tiempo de escritura.

---

### 6. Factores de forma y estándares de conexión

Los discos duros también se clasifican según su tamaño físico (factor de forma) y según el tipo de conexión que utilizan para comunicarse con el ordenador.

#### 6.1. Factor de forma
El **factor de forma** indica el tamaño físico de la unidad de almacenamiento.
- **Disco de 3,5 pulgadas:** se utilizan principalmente en sobremesas y NAS. Son más grandes y necesitan alimentación de 5V y 12V.
- **Disco de 2,5 pulgadas:** son más compactos y habituales en portátiles y discos externos. Funcionan normalmente con 5V, por lo que los externos suelen alimentarse mediante USB.

#### 6.2. Interfaces de conexión
La interfaz permite que el HDD se comunique con el equipo. Las principales son SATA, habitual en ordenadores domésticos y NAS por su bajo coste, y SAS, utilizada en servidores y entornos empresariales por sus funciones de fiabilidad y alta disponibilidad.

#### 6.3 Compatibilidad
El tamaño y la conexión son características independientes: un HDD de 3,5 o 2,5 pulgadas puede utilizar SATA o SAS. Un disco SATA normalmente funciona con una controladora SAS, pero un disco SAS no funciona con un puerto SATA convencional.


---
### 7. Un modelo real: ficha técnica interpretada

**Modelo:** Marca Modelo (enlace a la ficha del fabricante)

| Dato de la ficha | Qué significa | ¿Es bueno? ¿Para qué uso? |
|---|---|---|

---

### 8. Averías típicas y errores al instalarla



### 9. Fiabilidad: MTBF y SMART

Existen dos herramientas principales que sirven para valorar la capacidad de un disco para almacenar, leer y escribir datos correctamente sin sufrir averías.

#### 9.1. MTBF (Mean Time Between Failures)
- **Definición:** estimación estadística de la fiabilidad de un dispositivo, que indica el tiempo medio entre averías y se expresa normalmente en horas. **No permite predecir cuando va a fallar un disco concreto**.

*Ejemplo:* un HDD tiene un MTBF de 1.000.000 de horas, no significa que cada disco vaya a durar ese tiempo, es una estimación estadística calculada para un conjunto de dispositivos. Algunos pueden fallar antes y otros funcionar durante mucho más tiempo.

#### 9.2. SMART (Self-Monitoring, Analysis and Reporting Technology)
- **Definición:** tecnología que permite al propio disco duro supervisar determinados aspectos de su funcionamiento y registrar indicadores que pueden ayudar a detectar posibles fallos. **No garantiza que el disco avise antes de averiarse**.

SMART registra diferentes indicadores como, la temperatura, los sectores reasignados (sectores dañados que se sustituyen por otros de reserva) y los errores de lectura y escritura. Estos datos ayudan a detectar posibles problemas y señales de deterioro del disco.



![Esquema de funcionamiento](img/ejemplo-esquema.svg)

<!-- Guardad vuestras imágenes en img/ y cambiad el nombre del archivo en la línea de arriba. -->

## Fuentes

1.
2.
3.

## Uso de IA

Qué preguntamos a Jarvis u otra IA y cómo comprobamos sus respuestas.

## 7. Fuentes

1.
2.
3.

## Uso de IA
Qué preguntamos a Jarvis u otra IA y cómo comprobamos sus respuestas.
