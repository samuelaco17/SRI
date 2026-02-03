### Apuntes de Streaming — Versión Mejorada para Examen

### 1. Descarga directa vs Streaming

**Descarga directa**  
- El usuario descarga el archivo completo.  
- Aunque solo vea 2 minutos, el servidor envía todo.  
- Se almacena en disco (buffer + fichero).  
- Ejemplos: Mega, Google Drive.  
- Problema: desperdicio de ancho de banda.

**Streaming**  
- El servidor envía datos en tiempo real (flujo continuo).  
- No se guarda el archivo completo, solo un buffer temporal.  
- Solo se consume el ancho de banda equivalente al tiempo reproducido.  
- Ejemplos: Spotify, YouTube Live, radios online.  
- Ventaja: optimiza el ancho de banda.

---

### 2. Topologías de red aplicadas al Streaming

**Unicast**  
- Conexión 1 a 1 entre servidor y cliente.  
- Si hay 100 oyentes → 100 conexiones.  
- Fórmula: BW_total = BW_stream × Nº_usuarios  
- Poco escalable.

**Multicast**  
- Dirección: 224.0.0.0–239.255.255.255.  
- Los routers replican el tráfico solo si hay suscriptores.  
- Útil solo en redes internas (Internet lo bloquea).

**Broadcast**  
- Envío a toda la red local.  
- No se usa en streaming profesional.

---

### 3. Capa de transporte: TCP vs UDP

**TCP**  
- Fiable: retransmite paquetes perdidos.  
- Usa ACK/NACK.  
- Pasa firewalls, NAT y proxys.  
- Desventaja: mayor latencia.  
- Ideal para: radio online, Netflix, Spotify, Twitch (receptor), descargas, HTTP.

**UDP**  
- No retransmite paquetes.  
- Baja latencia.  
- Puede haber pérdidas (artefactos, cortes).  
- Ideal para: videollamadas, juegos, WebRTC, RTSP.

---

### 4. QoS: Jitter y Buffer

**Jitter**  
- Variación en el tiempo de llegada de los paquetes.  
- Si el jitter supera el buffer → cortes.

**Buffer**  
- Memoria temporal para absorber jitter.  
- Más buffer = más estabilidad.  
- Más buffer = más latencia.

**Burst-on-Connect (Icecast)**  
- Al conectarse un oyente, el servidor envía una ráfaga inicial (ej. 64 KB) a máxima velocidad.  
- Llena el buffer del cliente casi instantáneamente.  
- Reduce el time-to-first-byte.

---

### 5. Protocolos de Streaming

**Modelos de capa de aplicación**  
- HTTP Legacy (ICY / Icecast2)  
- HTTP Adaptativo (HLS / DASH)  
- Real-Time (RTMP, RTSP, WebRTC)

**HTTP Legacy (ICY / Icecast2)**  
- Flujo continuo por TCP.  
- Formatos: MP3, OGG, AAC.  
- Puertos: 80, 443, 8000.  
- No hay adaptación de calidad.  
- Usado en radios online.

**HTTP Adaptativo (HLS / DASH)**  
- El vídeo se divide en chunks de 2–10 s.  
- Calidad adaptativa según ancho de banda.  
- Formatos: .ts, .m4s.  
- Usado por: Netflix, YouTube, Disney+, HBO.

**Real-Time**  
- RTMP: TCP. Ingesta (OBS → YouTube/Twitch). Obsoleto para usuarios finales.  
- RTSP: Cámaras IP. UDP para datos, TCP para control. Problemas con NAT.  
- WebRTC: Videollamadas. P2P, cifrado, ultra baja latencia (<0.5 s).

---

### 6. Cuadro resumen

| Protocolo     | Base      | Latencia | Uso              | Firewall     | CDN        |
|---------------|-----------|----------|------------------|--------------|------------|
| Icecast (ICY) | TCP/HTTP  | 10–30 s  | Radio            | Muy fácil    | Difícil    |
| HLS/DASH      | TCP/HTTP  | 15–45 s  | Vídeo bajo demanda | Muy fácil | Excelente  |
| RTMP          | TCP       | 2–5 s    | Ingesta          | Medio        | No         |
| WebRTC        | UDP/TCP   | <0.5 s   | Videollamadas    | Complejo     | No         |
| RTSP          | UDP+TCP   | <1 s     | Cámaras IP       | Problemas NAT| No         |

---

### 7. Códecs de Audio

**Con pérdida**  
- Eliminan información irrelevante.  
- No recuperable.  
- Ejemplos: MP3, AAC, Vorbis.

**Sin pérdida**  
- No eliminan información.  
- Pesan más.  
- Ejemplos: FLAC, WAV.

---

### 8. Audio digital

**Frecuencia de muestreo**  
- Muestras por segundo.  
- Estándar: 44.1 kHz (calidad CD).

**Profundidad de bits**  
- Bits por muestra.  
- Estándar: 16 bits.  
- Más bits = más rango dinámico.

**Canales**  
- Mono (1), Estéreo (2), 5.1, 7.1…

---

### 9. Cálculo de peso (Audio)

**Fórmula RAW**  
- Peso = Frecuencia × Bits × Canales × Segundos

**Ejemplo WAV**  
- 44100 × 16 × 2 × 180 = 31.75 MB

**Con compresión**  
- Peso = Bitrate × Tiempo

---

### 10. Vídeo

**Contenedor**  
Incluye:  
- Pistas de vídeo  
- Pistas de audio  
- Subtítulos  
- Metadatos  
Ejemplos: MP4, MKV, MOV.

**Cálculo RAW**  
- Peso = (Ancho × Alto) × Profundidad × FPS × Tiempo

**Bitrate (con códec)**  
- Peso = Bitrate × Tiempo

**Bitrates recomendados**

| Resolución | Calidad   | Mínimo   | Recomendado     |
|------------|-----------|----------|-----------------|
| 4K         | Ultra HD  | 15 Mbps  | 25–45 Mbps      |
| 1080p      | Alta      | 4 Mbps   | 6–9 Mbps        |
| 720p       | Media     | 1.5 Mbps | 3–4 Mbps        |
| 480p       | Estándar  | 500 kbps | 1 Mbps          |
| 360p       | Baja      | 400 kbps | 700 kbps        |

---

### 11. Icecast2 (Servidor)

**Características**  
- Servidor de streaming de audio.  
- Necesita un source client (Mixxx, Butt).  
- Formatos: MP3, OGG.  
- Puntos de montaje.  
- Gestión de oyentes.  
- Web admin.

**Instalación**
```bash
apt update
apt install icecast2
```
Configurar:

source-password

admin-password

puerto 8000

### 12. Mixxx (Emisor)
Instalación
```bash
add-apt-repository ppa:mixxx/mixxx
apt update
apt install mixxx
```
### Configuración

Tipo: Icecast2

Montaje: /hectorsri

Servidor: 172.30.16.101

Puerto: 8000

Usuario: source

Contraseña: la configurada en Icecast

### 13. FFmpeg
Remuxing (cambiar contenedor sin recodificar)
```bash
ffmpeg -i original.mp4 -c:v copy -c:a copy salida.mkv
```
Cambio de códec
```bash
ffmpeg -i video.mp4 -c:v libx264 -b:v 2M -c:a copy h264.mp4
ffmpeg -i video.mp4 -c:v libx265 -b:v 2M -c:a copy h265.mp4
```
### 14. Conversión de unidades
1 byte = 8 bits

1 kbps = 1000 bps

1 Mbps = 1000 kbps

1 MB = 1024 KB

### 15. Ejercicios típicos de examen
Audio

bitrate_raw = frecuencia × bits × canales

BW_total = bitrate × oyentes

Vídeo

Bitrate RAW

Espacio ocupado

Porcentaje de uso de red

Soluciones típicas

Bajar bitrate

Usar H.265

Usar CDN

Reducir resolución o FPS
