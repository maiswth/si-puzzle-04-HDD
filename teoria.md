# Teoría · Pieza 04: HDD

**Grupo:** Maisara Aldana · Morena Macias

## Conceptos clave

- **HDD (Hard Disk Drive):** almacenamiento secundario **no volátil** que graba datos magnéticamente en **platos giratorios**; un brazo con cabezales lee y escribe.
- **Vigencia:** el SSD gana en latencia e IOPS, pero el HDD gana en **capacidad y coste por TB** → ideal para grandes volúmenes. Su evolución ha buscado **aumentar la densidad** (más información en la misma superficie).
- **Jerarquía de memoria:** organiza la memoria por velocidad, capacidad y coste; las más rápidas son más caras y están más cerca del procesador. **Cada nivel es caché del inferior.** Orden: Registros (datos de la CPU) → L1 (acceso muy frecuente) → L2 (más capacidad, algo más lenta) → L3 (mayor, compartida entre núcleos) → RAM (programas y datos en uso) → SSD (permanente rápido) → HDD (permanente de gran capacidad).
- **Componentes:**
  - **Platos:** discos con material magnético; se usan ambas caras.
  - **Cabezales:** *escriben* cambiando la orientación magnética de regiones diminutas; *leen* detectando sus variaciones (p. ej. **GMR**: detecta campos magnéticos por cambios de resistencia eléctrica).
  - **Brazo actuador:** mueve los cabezales a la pista.
  - **Motor del eje (spindle):** gira los platos a velocidad constante.
- **RPM:** vueltas completas por minuto; habituales **5400 y 7200**. Más RPM → **menor latencia rotacional** y mejor rendimiento (más operaciones en menos tiempo), pero más **ruido, calor y consumo**.
- **Tiempo de acceso:** tiempo para localizar y leer datos.
  $$T_{\text{acceso}} = T_{\text{seek}} + T_{\text{rotacional}} + T_{\text{transferencia}}$$
  *Seek:* el cabezal llega a la pista. *Rotacional:* espera a que el sector pase bajo el cabezal. *Transferencia:* transmitir los datos.
- **Latencia:** tiempo desde que se solicita un dato hasta que empieza a estar disponible.
- **Acceso por bloques:** la RAM accede a posiciones individuales direccionables por bytes; el almacenamiento trabaja con **bloques**.
- **Caché del disco:** pequeña memoria temporal integrada. *Lectura:* guarda copia para servirla si se repite (menos accesos físicos; capacidad limitada, no es indefinida). *Escritura:* guarda datos para que el firmware los **organice y agrupe** antes de grabarlos en los platos. **No es permanente:** es memoria **volátil** (normalmente DRAM); los platos sí conservan datos sin energía.
- **Pistas (tracks):** circunferencias concéntricas donde se organizan los datos del plato.
- **CMR (Conventional Magnetic Recording):** pistas **una al lado de otra, sin solaparse**; se puede modificar la pista B sin tocar A ni C → escrituras constantes y predecibles.
- **SMR (Shingled Magnetic Recording):** pistas **parcialmente solapadas** → más densidad en el mismo espacio. Inconveniente: modificar B puede sobrescribir parte de C, así que el disco guarda temporalmente lo que debe conservar, reescribe lo modificado, reorganiza y vuelve a escribir lo afectado. *Escrituras secuenciales* (en orden): evitan reorganizaciones. *Aleatorias* (posiciones distintas): obligan a reorganizar varias zonas → más lento.
- **MTBF (Mean Time Between Failures):** estimación estadística del tiempo medio entre averías (en horas). **No predice cuándo fallará un disco concreto.** Ej.: 1.000.000 h no implica que cada disco dure eso; es un dato de un conjunto.
- **SMART (Self-Monitoring, Analysis and Reporting Technology):** el disco supervisa su funcionamiento y registra indicadores: temperatura, **sectores reasignados** (dañados, sustituidos por reserva) y errores de lectura/escritura. **No garantiza avisar antes de una avería.**

## Tabla resumen

| Tipo | Dato clave | Cuándo se usa |
|---|---|---|
| HDD | Magnético, platos; mejor capacidad y €/TB | Almacenar grandes cantidades de datos |
| SSD | Mejor latencia e IOPS | Almacenamiento permanente rápido |
| 5400 RPM | Menos ruido, calor y consumo | Si prima eficiencia y silencio |
| 7200 RPM | Menor latencia rotacional | Si prima el rendimiento |
| CMR | Pistas sin solape; escritura predecible | Escrituras aleatorias o constantes |
| SMR | Pistas solapadas; mayor densidad | Escrituras sobre todo secuenciales |
| MTBF | Estadística de un conjunto, en horas | Comparar fiabilidad general |
| SMART | Indicadores del propio disco | Vigilar el estado de un disco |

## Datos que hay que saberse

- Jerarquía: Registros > L1 > L2 > L3 > RAM > SSD > HDD (cada nivel es caché del inferior).
- Plato = datos; cabezal = leer/escribir; brazo = posiciona; spindle = gira.
- T acceso = seek + rotacional + transferencia.
- Más RPM = menos latencia rotacional, pero más ruido, calor y consumo.
- La caché del HDD es volátil (DRAM); los platos no.
- SMR solapa pistas: más densidad, peor con escrituras aleatorias.
- MTBF y SMART no predicen ni garantizan: son orientativos.

## Preguntas tipo test (8)

1. ¿Qué ventaja mantiene el HDD frente al SSD?
   - a) Menor latencia
   - b) Mayor capacidad y menor coste por TB  ← correcta
   - c) Más IOPS
   - d) Es memoria volátil
   - Explicación: el SSD gana en latencia e IOPS; el HDD, en capacidad y coste por TB.

2. En la jerarquía de memoria, ¿qué se sitúa justo entre la RAM y el HDD?
   - a) Caché L3
   - b) Registros
   - c) SSD  ← correcta
   - d) Caché L2
   - Explicación: orden: registros, L1, L2, L3, RAM, SSD, HDD.

3. ¿Qué componente desplaza los cabezales hasta la pista?
   - a) Spindle
   - b) Brazo actuador  ← correcta
   - c) Plato
   - d) Caché
   - Explicación: el spindle gira los platos; el brazo posiciona los cabezales.

4. ¿Qué efecto tiene aumentar las RPM?
   - a) Mayor latencia rotacional
   - b) Menor consumo
   - c) Menor latencia rotacional, pero más ruido, calor y consumo  ← correcta
   - d) Menor tiempo de seek siempre
   - Explicación: los platos giran más rápido y el sector llega antes al cabezal.

5. ¿Qué incluye el tiempo de acceso de un HDD?
   - a) Seek + rotacional + transferencia  ← correcta
   - b) Solo seek
   - c) Seek + caché
   - d) Rotacional + RPM
   - Explicación: es la suma de los tres tiempos.

6. ¿Por qué la caché del HDD no es almacenamiento permanente?
   - a) Porque es magnética
   - b) Porque es memoria volátil (DRAM)  ← correcta
   - c) Porque está en los platos
   - d) Porque la gestiona el brazo
   - Explicación: pierde los datos al apagar; los platos los conservan.

7. ¿Qué caracteriza a SMR?
   - a) Pistas sin solape
   - b) Pistas parcialmente solapadas, con más densidad  ← correcta
   - c) Escrituras siempre predecibles
   - d) Usa SSD interno
   - Explicación: el solape aprovecha mejor la superficie, pero complica modificar datos.

8. Un HDD tiene un MTBF de 1.000.000 de horas. ¿Qué significa?
   - a) Que ese disco durará exactamente ese tiempo
   - b) Que SMART avisará antes de fallar
   - c) Que es una estimación estadística de un conjunto de discos  ← correcta
   - d) Que no puede fallar antes
   - Explicación: el MTBF no predice el fallo de un disco concreto.
