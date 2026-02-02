# Práctica de Streaming y Transcodificación con FFmpeg  
## Guía completa paso a paso 

---

## 1. Instalación de FFmpeg en Ubuntu

```bash
sudo apt update
sudo apt install ffmpeg
```

Comprobación:

```bash
ffmpeg -version
ffprobe -version
```

---

## 2. Descarga del vídeo de prueba

Para la práctica se utiliza el archivo:

```
big-buck-bunny-1080p-30sec.mp4
```

Este vídeo se descarga desde la plataforma indicada por el profesor (Aules o enlace directo).

---

## 3. Análisis del vídeo con ffprobe

Comando:

```bash
ffprobe -v error -show_streams big-buck-bunny-1080p-30sec.mp4
```

### Información obtenida

#### Vídeo
- Codec: H.264 (High Profile)
- Resolución: 1920×1080
- Framerate: 24 fps
- Bitrate: ~5860 kbps
- PixFmt: yuv420p
- B‑frames: 2
- Duración: 30 s

#### Audio
- Codec: AAC LC
- Canales: 5.1
- Frecuencia: 48 kHz
- Bitrate: ~192 kbps
- Duración: 30 s

---

## 4. Remuxing: cambio de contenedor MP4 → MKV

Comando:

```bash
ffmpeg -i big-buck-bunny-1080p-30sec.mp4 -c:v copy -c:a copy salida.mkv
```

### Resultados

- Tamaño original: ~22.1 MB  
- Tamaño MKV: ~22.18 MB  
- Conclusión: No cambia de forma significativa.

### Rendimiento

El log muestra:

```
speed=41.4x
```

Esto indica:

- Carga de CPU muy baja  
- Proceso muy rápido  
- No hay recodificación, solo copia de streams  

---

## 5. Recodificación a H.264 y H.265 con bitrate fijo

### H.264 a 2 Mbps

```bash
ffmpeg -i big-buck-bunny-1080p-30sec.mp4 -c:v libx264 -b:v 2M -c:a copy h264_2mbps.mp4
```

Resultados:

- Tamaño final: 8496 KB (~8.3 MB)
- Bitrate real: ~2320 kbps
- Velocidad: 1.17x

---

### H.265 a 2 Mbps

```bash
ffmpeg -i big-buck-bunny-1080p-30sec.mp4 -c:v libx265 -b:v 2M -c:a copy h265_2mbps.mp4
```

Resultados:

- Tamaño final: 8622 KB (~8.4 MB)
- Bitrate real: ~2354 kbps
- Velocidad: 0.55x (mucho más lento)

---

## 6. Comparación visual entre H.264 y H.265

### ¿Cuál presenta más artefactos?

H.264 a 2 Mbps.

Motivos:

- H.265 es más eficiente  
- A igual bitrate, H.265 conserva más detalle  
- H.264 muestra más bloques en escenas con movimiento  

---

### ¿Pesan lo mismo los archivos finales?

Casi, pero no exactamente.

- H.264: 8496 KB  
- H.265: 8622 KB  

Diferencia: ~126 KB

Razones:

- El bitrate es un objetivo aproximado  
- Cada códec gestiona GOP, QP y compresión de forma distinta  
- El contenedor MP4 añade metadatos diferentes  

---

## Conclusiones finales

- El remuxing no altera el tamaño ni requiere CPU  
- H.265 ofrece mejor calidad que H.264 al mismo bitrate  
- Ambos archivos recodificados tienen tamaños muy similares  
- H.265 requiere más tiempo de procesamiento  
