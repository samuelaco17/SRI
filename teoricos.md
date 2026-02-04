¿Por qué se utiliza mayoritariamente TCP en lugar de UDP en servicios como Netflix o Spotify?
Pregunta 1Resposta

a.
Porque TCP no utiliza buffer en el lado del cliente.

b.
Porque TCP ofrece una latencia mucho menor que UDP.

c.
Porque TCP garantiza que si un paquete se pierde, el servidor lo reenvía, asegurando la calidad.

d.
Porque UDP no permite el uso de firewalls o NAT.
La opción correcta es c. Porque TCP garantiza que si un paquete se pierde, el servidor lo reenvía, asegurando la calidad.

Explicación breve
Servicios como Netflix o Spotify priorizan que los datos lleguen completos y en orden, incluso si eso implica un poco más de latencia. Para streaming multimedia bajo demanda (no en directo), es más importante no perder paquetes que tener la mínima latencia posible. TCP ofrece:

Control de errores

Retransmisión de paquetes perdidos

Control de flujo y congestión

Entrega ordenada

UDP, en cambio, no garantiza nada de eso. Por eso se usa más en streaming en directo, juegos online o VoIP, donde la latencia importa más que la fiabilidad.

--------------------------------------------------------------------------------------------

¿Qué sucede en una reproducción de audio si el Jitter es superior al tamaño del buffer del cliente?
Pregunta 2Resposta

a.
El audio se corta, produciéndose lo que se conoce como Buffer Underrun.

b.
La calidad del audio aumenta automáticamente.

c.
El servidor activa la ráfaga de conexión (Burst-on-Connect).

d.
La latencia disminuye drásticamente.
La respuesta correcta es a. El audio se corta, produciéndose lo que se conoce como Buffer Underrun.

Por qué
Si el jitter (variación en el tiempo de llegada de los paquetes) supera la capacidad del buffer del cliente, este no puede compensar los retrasos. Resultado:

El reproductor se queda sin datos para reproducir.

Se produce un corte, salto o silencio en el audio.

Esto se denomina Buffer Underrun.

Las demás opciones no tienen relación con el comportamiento real del jitter en streaming.

--------------------------------------------------------------------------------------------

¿Qué proceso se está realizando al ejecutar el comando ffmpeg -i original.mp4 -c:v copy -c:a copy salida.mkv?
Pregunta 3Resposta

a.
Una inspección de los metadatos del archivo para localizar errores.

b.
Un "remuxing" o cambio de contenedor sin alterar los códecs ni la calidad original.

c.
Una transcodificación completa para reducir el bitrate a 2Mbps.

d.
La instalación del software necesario para emitir por streaming.
La respuesta correcta es b. Un "remuxing" o cambio de contenedor sin alterar los códecs ni la calidad original.

Por qué
El comando:

Código
ffmpeg -i original.mp4 -c:v copy -c:a copy salida.mkv
indica a FFmpeg que copie los flujos de vídeo y audio sin recodificarlos (-c:v copy y -c:a copy).
Lo único que cambia es el contenedor: de MP4 a MKV.
Esto se conoce como remuxing, y no afecta a la calidad ni al bitrate.

-----------------------------------------------------------------------------------------

¿Qué es un "contenedor" en el contexto de vídeo digital?
Pregunta 4Resposta

a.
Un algoritmo específico para comprimir píxeles.

b.
La resolución máxima que puede alcanzar un monitor (ej. 4K).

c.
El protocolo de red usado para enviar películas.

d.
Un formato de fichero que agrupa pistas de vídeo, audio, subtítulos y metadatos.
La respuesta correcta es d. Un formato de fichero que agrupa pistas de vídeo, audio, subtítulos y metadatos.

Por qué
Un contenedor (MP4, MKV, AVI, MOV…) no es un códec ni un método de compresión. Su función es empaquetar:

Pistas de vídeo

Pistas de audio

Subtítulos

Metadatos (capítulos, carátulas, idioma, bitrate…)

El contenedor define cómo se organizan y almacenan esos elementos dentro del archivo, pero no determina la calidad ni el tipo de compresión (eso lo hacen los códecs como H.264, H.265, AAC, Opus…).

-------------------------------------------------------------------------------------------

¿Cuál es la principal ventaja del streaming respecto al ancho de banda en comparación con la descarga directa?
Pregunta 5Resposta

a.
Solo se consume el ancho de banda que el cliente ha utilizado realmente.

b.
El servidor siempre entrega el fichero completo independientemente de lo que vea el usuario.

c.
No existe diferencia en el consumo de ancho de banda entre ambos métodos.

d.
El streaming permite el almacenamiento local permanente de los datos.
La respuesta correcta es a. Solo se consume el ancho de banda que el cliente ha utilizado realmente.

Por qué
En streaming, el servidor envía solo la parte del contenido que el usuario está viendo.
Si alguien abandona un vídeo a los 2 minutos, solo se transmiten esos 2 minutos.

En una descarga directa, en cambio, el fichero completo se transfiere aunque el usuario no lo llegue a consumir entero, lo que implica un uso mayor e innecesario de ancho de banda.

------------------------------------------------------------------------------------------

¿En qué consiste la mecánica del protocolo HLS (HTTP Live Streaming)?
Pregunta 6Resposta

a.
Es un protocolo P2P que no requiere servidor centralizado.

b.
Se utiliza exclusivamente para cámaras de seguridad mediante UDP.

c.
El servidor trocea el fichero en pequeños fragmentos o chunks de 2 a 10 segundos.

d.
Se abre una conexión TCP y el servidor envía un flujo continuo de bytes sin parar.
La respuesta correcta es c. El servidor trocea el fichero en pequeños fragmentos o chunks de 2 a 10 segundos.

Por qué
HLS funciona dividiendo el contenido en pequeños segmentos HTTP (normalmente entre 2 y 10 segundos).
El cliente descarga estos fragmentos uno tras otro siguiendo una playlist M3U8, lo que permite:

Adaptar la calidad según el ancho de banda (ABR).

Reanudar fácilmente si hay cortes.

Usar servidores HTTP estándar y CDNs.

Las otras opciones no describen el funcionamiento real de HLS.

------------------------------------------------------------------------------------------

¿Cuál es el estándar de frecuencia de muestreo y profundidad de bits para una calidad de CD?
Pregunta 7Resposta

a.
22 kHz y 8 bits.

b.
44,1 kHz y 16 bits.

c.
96 kHz y 32 bits.

d.
48 kHz y 24 bits.
La respuesta correcta es b. 44,1 kHz y 16 bits.

Por qué
El estándar del CD de audio (Red Book) utiliza:

Frecuencia de muestreo: 44,1 kHz

Profundidad de bits: 16 bits por muestra

Esto permite una calidad suficiente para cubrir el rango audible humano y una buena relación señal‑ruido.

------------------------------------------------------------------------------------------

En una topología de red Unicast, si hay 100 oyentes conectados, ¿cómo gestiona el servidor el envío de información?
Pregunta 8Resposta

a.
El servidor abre 100 sockets TCP y envía la información 100 veces.

b.
La información se envía una sola vez a toda la red local.

c.
El ancho de banda total es igual al ancho de banda del stream dividido por el número de usuarios.

d.
El servidor envía la información a una dirección única y los routers la replican.
La respuesta correcta es a. El servidor abre 100 sockets TCP y envía la información 100 veces.

Por qué
En Unicast, cada cliente recibe su propia conexión individual.
Eso implica:

100 oyentes → 100 conexiones independientes.

El servidor duplica el envío tantas veces como clientes haya.

El consumo total de ancho de banda crece linealmente con el número de usuarios.

Las otras opciones describen comportamientos propios de Multicast o son incorrectas.

---------------------------------------------------------------------------------------------------
¿Qué define a un códec con pérdida como el MP3?
Pregunta 9Resposta

a.
Comprime el fichero de forma idéntica a un .zip sin eliminar información.

b.
Elimina información que puede ser imperceptible para reducir el peso, siendo esta irrecuperable.

c.
Mantiene la misma calidad y peso que un archivo WAV original.

d.
Solo se puede utilizar en conexiones UDP.
La respuesta correcta es b. Elimina información que puede ser imperceptible para reducir el peso, siendo esta irrecuperable.

Por qué
Un códec con pérdida (lossy) como MP3, AAC u Opus aplica técnicas psicoacústicas para descartar partes del audio que el oído humano percibe poco o nada.
Esto reduce drásticamente el tamaño del archivo, pero la información eliminada no puede recuperarse.

Las otras opciones no describen el funcionamiento real de un códec con pérdida.

---------------------------------------------------------------------------------------------------------

¿Cuál es la función principal de Icecast2 en una arquitectura de radio online?
Pregunta 10Resposta

a.
Generar el contenido de audio de forma autónoma.

b.
Comprimir los archivos de audio originales de 32MB a 3MB.

c.
Sustituir al software de mezclas como Mixxx.

d.
Actuar como una antena virtual que recibe el audio de una fuente y lo distribuye a los oyentes.
La respuesta correcta es d. Actuar como una antena virtual que recibe el audio de una fuente y lo distribuye a los oyentes.

Por qué
Icecast2 no genera contenido ni mezcla audio. Su papel es:

Recibir un stream de audio desde una fuente (por ejemplo, Mixxx, Butt, Liquidsoap…).

Servir ese stream a todos los oyentes conectados.

Gestionar conexiones, puntos de montaje, estadísticas y ancho de banda.

Es, en esencia, el servidor de streaming que hace de “antena” en una radio online.
