# Teoría · Pieza 04: HDD

**Grupo:** Maisara Aldana · Morena Macias

## Conceptos clave

### 1. Qué es un HDD
- **Definición:** un disco duro (*Hard Disc Drive*, HDD) es un dispositivo de almacenamiento secundario **no volátil** que graba datos magnéticamente en **platos giratorios**, un brazo con cabezales lee y escribe la información.
#### ¿Por qué sigue vigente?
Los SSD siguen ganando en latencia e IOPS, pero el HDD gana en **capacidad y coste por TB**.
#### Evolución de los HDD: como consiguieron almacenar cada vez más información
El principal objetivo de su evolución ha sido **aumentar la densidad de almacenamiento**, es decir almacenar más información en la misma superficie física.

### 2. Componentes y funcionamiento
- **Los platos:**
Son los discos circulares que encontramos dentro del HDD. Se encargan de almacenar los datos mediante magnetismo. Pueden utilizarse ambas caras.
- **Cabezales de lectura y escritura**
Son unos componentes diminutos que se encargan de leer y escribir los datos en los platos.
*Escritura:* el cabezal modifica la orientación magnética de pequeñas regiones del plato para representar los datos.
*Lectura:* detecta las variaciones magnéticas de esas regiones
- **Brazo actuador**
Desplaza los cabezales hasta la pista donde se encuentran los datos.
- **Motor del eje (spindle)**
Hace girar los platos a una velocidad constante.

#### RPM (Revolutions Per Minute)

### 3. Rendimiento y tiempo de acceso
El tiempo de acceso es el tiempo necesario para localizar y leer datos.

$$T_{\text{acceso}} = T_{\text{seek}} + T_{\text{rotacional}} + T_{\text{transferencia}}$$
- *Seek:* tiempo que tarda el cabezal en desplazarse hasta la pista correspondiente.
- *Latencia rotacional:* tiempo que espera hasta que el sector deseado pasa por debajo del cabezal.
- *Transferencia:* tiempo necesario para transmitir los datos.

### 2. Jerarquía de memoria y E/S
- **Definición:** la jerarquía de memoria es la forma en que se organizan los diferentes tipos de memoria de un ordenador según su velocidad, capacidad y coste. Las memorias más rápidas utilizan tecnologías más costosas y necesitan estar muy cerca del procesador. **Cada nivel es caché del inferior**.

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

#### 2.1. Latencias 
**Latencia:** es el tiempo que transcurre desde que se solicita un dato hasta que comienza a estar disponible.
#### 2.2. Acceso por bloques
La RAM permite acceder directamente a posiciones individuales de memoria direccionables por bytes. Sin embargo los dispositivos de almacenamiento, suelen trabajar mediante **bloques de datos**.

### 3. Anatomía interna y física
- A. Los platos: donde se almacena la información
- B. El helio
- **Ventajas:** Algunos HDD sustituyen el aire por el helio (más ligero), se reduce la fricción aerodinámica, las turbulencias y el calor, lo que disminuye el consumo de energía y permite incluir más platos en el mismo espacio.
- **Requisito:** Requieren un sellado hermético para evitar fugas de helio y entradas de aire.
Para la lectura se utilizan tecnologías como:
**GRM:** permite detectar campos magnéticos mediante cambios en la resistencia eléctrica.
**TMR:** utiliza un efecto cuántico para detectar variaciones magnéticas con una gran sensibilidad.
#### D. El actuador
SMART

### 4. Rendimiento y fórmulas de un HDD
#### Tiempo de acceso

### 5. CMR frente a SMR
### 6. SMART

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
