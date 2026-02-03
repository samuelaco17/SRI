### Práctica de Streaming y Transcodificación con FFmpeg

### 1. Instalación de FFmpeg en Ubuntu
Para preparar el entorno se instala FFmpeg desde los repositorios oficiales:

```bash
sudo apt update
sudo apt install ffmpeg

ffmpeg -version
ffprobe -version
```
Comprobación de la instalación:
ffmpeg -version
ffprobe -version

```
ffmpeg -version
ffprobe -version
```
### 2. Descarga del vídeo de prueba
El archivo utilizado es:

big-buck-bunny-1080p-30sec.mp4

Descargado desde Aules para asegurar uniformidad en la práctica.

### 3. Análisis del vídeo con ffprobe
Antes de realizar conversiones se analiza el archivo:
```bash
ffprobe -v error -show_streams big-buck-bunny-1080p-30sec.mp4
```
### Datos del vídeo:

Codec: H.264 (High Profile)

Resolución: 1920×1080

Framerate: 24 fps

Bitrate: ~5860 kbps

PixFmt: yuv420p

B‑frames: 2

Duración: 30 s

### Datos del audio:

Codec: AAC LC

Canales: 5.1

Frecuencia: 48 kHz

Bitrate: ~192 kbps

Duración: 30 s

### 4. Remuxing: MP4 → MKV
Se cambia únicamente el contenedor sin recodificar:
```bash
ffmpeg -i big-buck-bunny-1080p-30sec.mp4 -c:v copy -c:a copy salida.mkv
```
### Resultados:

Tamaño MP4: ~22.1 MB

Tamaño MKV: ~22.18 MB

La diferencia es mínima porque solo se ha cambiado el contenedor.

Rendimiento:
El log muestra:
```bash
speed=41.4x
```
Esto confirma que el proceso es muy rápido y sin carga de CPU significativa.

### 5. Recodificación a H.264 y H.265 con bitrate fijo
H.264 a 2 Mbps
```bash
ffmpeg -i big-buck-bunny-1080p-30sec.mp4 -c:v libx264 -b:v 2M -c:a copy h264_2mbps.mp4
```
Resultados:

Tamaño final: 8496 KB (~8.3 MB)

Bitrate real: ~2320 kbps

Velocidad: 1.17x

H.265 a 2 Mbps
```bash
ffmpeg -i big-buck-bunny-1080p-30sec.mp4 -c:v libx265 -b:v 2M -c:a copy h265_2mbps.mp4
```
### Resultados:

Tamaño final: 8622 KB (~8.4 MB)

Bitrate real: ~2354 kbps

Velocidad: 0.55x (más lento debido a la mayor complejidad del códec)

### 6. Comparación visual entre H.264 y H.265
¿Cuál presenta más artefactos?  
El archivo H.264 muestra más artefactos a 2 Mbps.

### Motivos:

H.265 es más eficiente.

### Conserva más detalle al mismo bitrate.

H.264 pierde nitidez y muestra bloques en escenas con movimiento.

### ¿Pesan lo mismo?  
Son similares pero no idénticos:

H.264: 8496 KB

H.265: 8622 KB

Diferencia: ~126 KB

### Esto se debe a:

El bitrate es un objetivo aproximado.

Cada códec gestiona GOP, QP y compresión de forma distinta.

El contenedor añade metadatos propios.

Conclusiones finales
El remuxing no altera el tamaño ni requiere CPU.

H.265 ofrece mejor calidad que H.264 al mismo bitrate.

Los tamaños finales son muy parecidos.

H.265 necesita más tiempo de procesamiento.
