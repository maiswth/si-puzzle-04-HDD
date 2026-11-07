# Teoría · Pieza 04: HDD

**Grupo:** Maisara Aldana · Morena Macias

## Conceptos clave

### 1. ¿Qué es un HDD? vigencia y evolución

- **Definición:** un disco duro (*Hard Disk Drive*, HDD) es un dispositivo de almacenamiento secundario **no volátil** que graba datos magnéticamente en **platos giratorios**, un brazo con cabezales lee y escribe la información.

#### ¿Por qué sigue vigente?
Los SSD siguen ganando en latencia e IOPS, pero el HDD gana en **capacidad y coste por TB**, por lo que son adecuados para guardar grandes cantidades de información.

#### Evolución de los HDD: como consiguieron almacenar cada vez más información
El principal objetivo de su evolución ha sido **aumentar la densidad de almacenamiento**, es decir almacenar más información en la misma superficie física.

#### Jerarquía de memoria y E/S
- **Definición:** es la forma en que se organizan los diferentes tipos de memoria de un ordenador según su velocidad, capacidad y coste. Las memorias más rapidas utilizan tecnologías más costosas y necesitan estar muy cerca del procesador. **Cada nivel es caché del inferior**.

#### ¿Cómo se organiza?
| Nivel | Tipo de memoria | Función |
|---|---|---|
| 1 | Registros | Guardan datos que utiliza directamente la CPU |
| 2 | Caché L1 | Almacena datos de acceso muy frecuente |
| 3 | Caché L2 | Almacena más datos que L1 pero es algo más lenta |
| 4 | Caché L3 | Caché de mayor capacidad, compartida normalmente entre núcleos |
| 5 | RAM | Guarda programas y datos que se están utilizando |
| 6 | SSD | Almacenamiento permanente rápido |
| 7 | HDD | Almacenamiento permanente de gran capacidad |

---

### 2. Componentes su funcionamiento y RPM

- **Los platos:** Son los discos circulares que encontramos dentro del HDD. Se encargan de almacenar los datos mediante magnetismo. Pueden utilizarse ambas caras.
- **Cabezales de lectura y escritura:** Son unos componentes diminutos que se encargan de leer y escribir los datos en los platos.
* *Escritura:* el cabezal modifica la orientación magnética de pequeñas regiones del plato para representar los datos.
* *Lectura:* detecta las variaciones magnéticas de esas regiones. Se utilizan tecnologías como:
+ **GMR:** permite detectar campos magnéticos mediante cambios en la resistencia eléctrica.
- **Brazo actuador:** Desplaza los cabezales hasta la pista donde se encuentran los datos.
- **Motor del eje (spindle):** Hace girar los platos a una velocidad constante.

#### RPM (Revolutions Per Minute)
Indica cuantas vueltas completas realizan los platos de un disco duro en un minuto, las velocidades habituales son 5400 y 7200RPM. A mayor RPM, menor latencia rotacional, quiere decir que cuanto más rápido giran los platos, menos tiempo tenemos que esperar a que el sector deseado pase por debajo del cabezal. 

- **Ventajas:** Al reducirse el tiempo de espera, generalmente se mejora el rendimiento (+ operaciones - tiempo). 
- **Desventajas:** Mayor RPM también significa que el motor tiene que girar los platos a mayor velocidad y eso produce ruido, calor y un mayor consumo de energía.

---

### 3. Rendimiento y tiempo de acceso

El tiempo de acceso es el tiempo necesario para localizar y leer datos.

$$T_{\text{acceso}} = T_{\text{seek}} + T_{\text{rotacional}} + T_{\text{transferencia}}$$

- *Seek:* tiempo que tarda el cabezal en desplazarse hasta la pista correspondiente.
- *Latencia rotacional:* tiempo que espera hasta que el sector deseado pasa por debajo del cabezal.
- *Transferencia:* tiempo necesario para transmitir los datos.

#### 3.1. Latencia
Es el tiempo que transcurre desde que se solicita un dato hasta que comienza a estar disponible.

#### 3.2. Acceso por bloques
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

### 5. CMR frente a SMR

Son dos formas distintas de organizar físicamente la información en los platos de un HDD. Y esa diferencia afecta a como se comporta el disco cuando escribimos datos.
Los platos de un HDD son discos circulares recubiertos de material magnético. En su superficie se organizan los datos en circunferencias concéntricas llamadas pistas (*tracks*). La diferencia entre CMR y SMR radica en como se distribuyen las pistas.

#### 5.1. CMR (Conventional Magnetic Recording)
En CMR, las pistas se escriben **una al lado de la otra, sin solaparse**. Si quieres modificar los datos de la pista B, puedes hacerlo sin tener que modificar las pistas A y C.
- **Ventaja:** Escrituras constantes y predecibles.

#### 5.2. SMR (Shingled Magnetic Recording)
En SMR, las pistas se escriben **solapándose parcialmente**. De esta manera aprovechan mejor la superficie del plato y almacenan más información en el mismo espacio.

- **Inconveniente:** Modificar los datos puede requerir trabajo adicional porque unas pistas se solapan con otras. Si queremos modificar los datos de B, podríamos sobreescribir parte de C, pero no queremos perder los datos de C así que el disco tiene que guardar temporalmente los datos que necesita conservar, reescribir la información modificada, reorganizar y volver a escribir los datos afectados.

Aquí entran las escrituras *secuenciales* o *aleatorias*.
* *Secuenciales:* los datos se escriben siguiendo un orden. Esto facilita que SMR vaya colocando la información de forma consecutiva, evitando muchas reorganizaciones.
* *Aleatorias:* escribimos o modificamos datos en distintas posiciones. Esto puede obligar a SMR a reorganizar información de varias zonas, haciendo que tarde más.

---

### 6. Fiabilidad: MTBF y SMART

Existen dos herramientas principales que sirven para valorar la capacidad de un disco para almacenar, leer y escribir datos correctamente sin sufrir averías.

#### 6.1. MTBF (Mean Time Between Failures)
- **Definición:** Estimación estadística de la fiabilidad de un dispositivo, que indica el tiempo medio entre averías y se expresa normalmente en horas. **No permite predecir cuando va a fallar un disco concreto**.

*Ejemplo:* un HDD tiene un MTBF de 1.000.000 de horas, no significa que cada disco vaya a durar ese tiempo, es una estimación estadística calculada para un conjunto de dispositivos. Algunos pueden fallar antes y otros funcionar durante mucho más tiempo.

#### 6.2. SMART (Self-Monitoring, Analysis and Reporting Technology)
- **Definición:** Tecnología que permite al propio disco duro supervisar determinados aspectos de su funcionamiento y registrar indicadores que pueden ayudar a detectar posibles fallos. **No garantiza que el disco avise antes de averiarse**.

SMART registra diferentes indicadores como, la temperatura, los sectores reasignados (sectores dañados que se sustituyen por otros de reserva) y los errores de lectura y escritura. Estos datos ayudan a detectar posibles problemas y señales de deterioro del disco.


## Tabla resumen

| Tipo | Dato clave | Cuándo se usa |
|---|---|---|

## Datos que hay que saberse

## Preguntas tipo test (8)

1. Pregunta
   - a) …
   - b) …  ← correcta
   - c) …
   - d) …
   - Explicación: …
