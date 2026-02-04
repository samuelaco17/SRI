## Tabla de conversión para bitrates y tamaños

| Concepto | Fórmula | Ejemplo con 14.93 Gbps y 10 s |
|---------|---------|--------------------------------|
| **1. Bits totales** | bitrate × tiempo | `14.93 Gbps × 10 s = 149.3 Gb` |
| **2. Pasar de gigabits a gigabytes** | dividir entre 8 | `149.3 ÷ 8 = 18.6625 GB` |
| **3. Resultado final** | — | **18.66 GB** |

---

## Mini‑tabla de referencia rápida

| Unidad | Equivalencia |
|--------|--------------|
| 1 byte | 8 bits |
| 1 KB | 1024 bytes |
| 1 MB | 1024 KB |
| 1 GB | 1024 MB |
| 1 Gb (gigabit) | 1/8 GB (gigabyte) |
| Gb → GB | dividir entre 8 |
| GB → Gb | multiplicar por 8 |

---

## Plantilla para cualquier ejercicio

1. Multiplica el **bitrate** por los **segundos**.  
2. Convierte de **bits → bytes** dividiendo entre 8.  
3. Ajusta unidades si hace falta (MB, GB, TB).

.................................................................

### 1. Con un bitrate de 14.93 Gbps, ¿cuánto espacio de disco ocupará una toma de 10 segundos?
Pregunta 1Resposta

a.
186.6 MB

b.
149.3 GB

c.
18.66 GB

d.
1.86 GB
Para resolverlo solo necesitas convertir correctamente:

Bitrate: 14.93 Gbps

Duración: 10 s

14.93
 Gbps
×
10
=
149.3
 gigabits
Ahora pasamos de gigabits a gigabytes dividiendo entre 8:

149.3
÷
8
=
18.6625
 GB
La opción correcta es:

c. 18.66 GB

..................................................

### 2. Si 4 alumnos emiten a 6 Mbps cada uno en una línea de 20 Mbps de subida, ¿qué ocurrirá?
Pregunta 2Resposta

a.
La red se saturará (24 Mbps requeridos) provocando buffering.

b.
La red repartirá los 20 Mbps equitativamente sin cortes.

c.
El servidor Icecast aplicará automáticamente Burst-on-Connect.

d.
No ocurrirá nada, ya que la línea de subida es simétrica.
La suma total del tráfico es:

4
 alumnos
×
6
 Mbps
=
24
 Mbps
La línea solo ofrece 20 Mbps de subida, así que no puede soportar los 24 Mbps necesarios.

El resultado real es saturación y cortes.

La respuesta correcta es:

a. La red se saturará (24 Mbps requeridos) provocando buffering.

....................................................................

### 3. Si emites un streaming de audio a un bitrate constante (CBR) de 128 kbps y tienes 25 oyentes simultáneos en una red Unicast, ¿cuál es el ancho de banda total consumido?

Bitrate por oyente: 128 kbps

Número de oyentes: 25

128
 kbps
×
25
=
3200
 kbps
Convertimos a Mbps:

3200
÷
1000
=
3.2
 Mbps
Ancho de banda total consumido: 3.2 Mbps

Aquí la clave está en qué unidad quieres obtener al final.

🔹 Bitrate original
128 kbps = kilobits por segundo

Cuando multiplicas:

128
 kbps
×
25
=
3200
 kbps
El resultado sigue estando en kbps.

🔹 ¿Por qué dividir entre 1000?
Porque normalmente el ancho de banda total se expresa en Mbps (megabits por segundo), no en kbps.

Y:

1
 Mbps
=
1000
 kbps
Por eso:

3200
 kbps
÷
1000
=
3.2
 Mbps
🔹 ¿Y por qué 1000 y no 1024?
Porque en redes se usan múltiplos decimales (1000), no binarios (1024).
Los 1024 solo se usan en almacenamiento (KB, MB, GB…).

............................................................

### 4. Calcula el peso aproximado de un archivo de audio WAV de 5 minutos, con 44.1 kHz, 16 bits y estéreo.
Pregunta 4Resposta

a.
31.75 MB

b.
5.29 MB

c.
50.47 MB

d.
423.36 MB

Datos
Frecuencia de muestreo: 44,100 Hz

Profundidad: 16 bits

Canales: 2 (estéreo)

Duración: 5 minutos = 300 s

1. Cálculo del bitrate del WAV
44
,
100
 muestras/s
×
16
 bits
×
2
=
1
,
411
,
200
 bits/s
Eso son:

1
,
411
,
200
÷
8
=
176
,
400
 bytes/s
2. Tamaño total del archivo
176
,
400
 bytes/s
×
300
 s
=
52
,
920
,
000
 bytes
Convertimos a MB (en audio se usa 1 MB = 1,000,000 bytes):

52
,
920
,
000
÷
1
,
000
,
000
=
52.92
 MB
La opción más cercana es:

c. 50.47 MB
(Es la que más se aproxima al valor real ≈ 52.9 MB.)

🧠 Objetivo
Calcular el tamaño aproximado de un archivo WAV con estas características:

44.1 kHz

16 bits

Estéreo (2 canales)

5 minutos (300 segundos)

1. ¿Qué es lo primero que se calcula?
👉 El bitrate real del audio WAV
Un archivo WAV no está comprimido, así que su bitrate depende directamente de:

Frecuencia de muestreo
×
profundidad
×
nº de canales
Sustituimos:
44,100 muestras por segundo

16 bits por muestra

2 canales (estéreo)

44
,
100
×
16
×
2
=
1
,
411
,
200
 bits/s
¿Por qué se hace esto?
Porque un WAV almacena cada muestra tal cual, sin compresión.
Cada muestra tiene 16 bits, y hay 44,100 muestras por segundo por canal.

2. Convertir bits/s a bytes/s
Los tamaños de archivo se miden en bytes, no en bits.

Sabemos que:

1
 byte
=
8
 bits
Así que:

1
,
411
,
200
÷
8
=
176
,
400
 bytes/s
¿Por qué dividir entre 8?
Porque queremos pasar de bits (unidad de transmisión) a bytes (unidad de almacenamiento).

3. Calcular el tamaño total del archivo
Duración: 5 minutos = 300 segundos

Multiplicamos:

176
,
400
 bytes/s
×
300
 s
=
52
,
920
,
000
 bytes
¿Por qué multiplicar por los segundos?
Porque queremos saber cuántos bytes se generan en total durante toda la duración del audio.

4. Convertir bytes a MB
En audio y redes se usa la conversión decimal:

1
 MB
=
1
,
000
,
000
 bytes
Así que:

52
,
920
,
000
÷
1
,
000
,
000
=
52.92
 MB
5. Comparar con las opciones
La opción más cercana es:

✅ c. 50.47 MB

--------------------------------------------------

### 5. Un estudio graba en RAW a 3840x2160, a 60 fps y 30 bits de color. ¿Cuál es el bitrate resultante en Gbps?
Pregunta 5Resposta

a.
14.93 Gbps

b.
14.93 Mbps

c.
1.49 Gbps

d.
447.8 Gbps
Vamos a calcularlo paso a paso, Samalin, con números claros.

1. Resolución por fotograma
3840
×
2160
=
8
,
294
,
400
 p
ı
ˊ
xeles
2. Píxeles por segundo (a 60 fps)
8
,
294
,
400
×
60
=
497
,
664
,
000
 p
ı
ˊ
xeles/s
3. Bits por segundo (30 bits por píxel)
497
,
664
,
000
×
30
=
14
,
929
,
920
,
000
 bits/s
4. Pasar a Gbps
14
,
929
,
920
,
000
÷
1
,
000
,
000
,
000
=
14.93
 Gbps
✔ Respuesta correcta: a. 14.93 Gbps
Si quieres, te preparo una tabla en Markdown con todas las fórmulas de vídeo RAW para tu repo.

🎥 Datos del ejercicio
Resolución: 3840 × 2160

Fotogramas por segundo: 60 fps

Profundidad de color: 30 bits por píxel

Formato: RAW (sin compresión)

En RAW no hay compresión, así que el bitrate depende directamente de cuántos bits genera cada fotograma y cuántos fotogramas hay por segundo.

1. Cálculo de píxeles por fotograma
3840
×
2160
=
8
,
294
,
400
 p
ı
ˊ
xeles
¿Por qué?
Porque cada fotograma es una imagen completa, y necesitamos saber cuántos píxeles contiene para saber cuántos bits se generan por fotograma.

2. Píxeles por segundo
8
,
294
,
400
×
60
=
497
,
664
,
000
 p
ı
ˊ
xeles/s
¿Por qué?
Porque el bitrate se mide por segundo, así que multiplicamos los píxeles de un fotograma por los fotogramas por segundo.

3. Bits por segundo
Cada píxel tiene 30 bits de información (10 bits por canal RGB, por ejemplo).

497
,
664
,
000
×
30
=
14
,
929
,
920
,
000
 bits/s
¿Por qué?
Porque el bitrate RAW es literalmente:

p
ı
ˊ
xeles por segundo
×
bits por p
ı
ˊ
xel
4. Convertir a Gbps
14
,
929
,
920
,
000
÷
1
,
000
,
000
,
000
=
14.93
 Gbps
¿Por qué dividir entre 1.000.000.000?
Porque:

1 Gbps = 1.000.000.000 bits/s

En vídeo y redes se usan múltiplos decimales, no binarios.

✔ Resultado final
14.93 Gbps

................................................................................

### 6. Tienes un disco de 500 GB. ¿Cuántas horas de vídeo HD a 2 Mbps podrías alojar aproximadamente?
Pregunta 6Resposta

a.
250 horas

b.
555 horas

c.
277 horas

d.
1000 horas
Vamos a resolverlo con calma, Samalin, porque este es de los clásicos de cálculo de almacenamiento en ASIR.

1. Convertir el tamaño del disco a megabits
El vídeo está en Mbps, así que el disco debe convertirse también a megabits.

1 byte = 8 bits

1 GB = 1.000 MB (en almacenamiento se usa decimal)

1 MB = 8.000.000 bits → 8 Mb

Primero pasamos 500 GB a megabits:

500
 
GB
×
1000
 
MB
=
500
 
000
 
MB
500
 
000
 
MB
×
8
=
4
 
000
 
000
 
Mb
2. Dividir entre el bitrate del vídeo
El vídeo consume 2 Mbps, así que:

4
 
000
 
000
÷
2
=
2
 
000
 
000
 
segundos
3. Convertir segundos a horas
2
 
000
 
000
÷
3600
≈
555.55
 
horas
✔ Respuesta correcta
b. 555 horas

...................................................................

### 7. Si tienes una conexión de 20 Mbps de subida y emites vídeo a 6 Mbps, ¿qué porcentaje de tu línea estás utilizando?
Pregunta 7Resposta

a.
60%

b.
12%

c.
30%

d.
6%
Vamos a calcularlo de forma directa, Samalin.

Ancho de banda disponible: 20 Mbps

Consumo del streaming: 6 Mbps

El porcentaje usado es:

6
20
×
100
=
30
%
La opción correcta es:

c. 30%

...................................................................

### 8. ¿Cuál es el bitrate de un flujo de audio que utiliza una frecuencia de muestreo de 48 kHz, una profundidad de 24 bits y un solo canal (mono)?
Pregunta 8Resposta

a.
0.576 Mbps

b.
576 kbps

c.
2.304 Mbps

d.
1.152 Mbps
Vamos a calcularlo paso a paso, Samalin, como harías tú mismo en clase.

1. Fórmula del bitrate en audio sin comprimir (PCM/WAV)
Bitrate
=
Frecuencia de muestreo
×
Profundidad
×
Canales
2. Sustituimos los valores
Frecuencia: 48.000 Hz

Profundidad: 24 bits

Canales: 1 (mono)

48
,
000
×
24
×
1
=
1
,
152
,
000
 bits/s
3. Convertimos a kbps y Mbps
En kbps:
1
,
152
,
000
÷
1000
=
1152
 kbps
En Mbps:
1
,
152
,
000
÷
1
,
000
,
000
=
1.152
 Mbps
✔ Respuesta correcta
d. 1.152 Mbps

............................................................

### 9. En una línea de 100 Mbps simétricos, ¿cuántos usuarios podrían ver un streaming de vídeo de 2 Mbps?
Pregunta 9Resposta

a.
200 usuarios

b.
20 usuarios

c.
50 usuarios

d.
100 usuarios
Vamos a resolverlo rápido, Samalin.

Ancho de banda disponible: 100 Mbps

Consumo por usuario: 2 Mbps

Número de usuarios posibles:

100
2
=
50
La respuesta correcta es:

c. 50 usuarios

.............................................................

### 10. Un servidor tiene un límite de subida de 10 Mbps. ¿Cuántos oyentes simultáneos puede soportar si cada uno consume 192 kbps?
Pregunta 10Resposta

a.
520 oyentes

b.
19 oyentes

c.
100 oyentes

d.
52 oyentes
Vamos directo al cálculo, Samalin.

Límite de subida del servidor: 10 Mbps = 10.000 kbps

Consumo por oyente: 192 kbps

Número de oyentes simultáneos:

10
 
000
192
≈
52.08
El servidor puede soportar 52 oyentes antes de saturarse.

La respuesta correcta es:

d. 52 oyentes
