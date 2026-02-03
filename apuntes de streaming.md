Apuntes de Streaming — Versión Optimizada
1. Descarga directa vs Streaming
Descarga directa
El usuario descarga el archivo completo.

Aunque solo vea 2 minutos, el servidor envía todo.

Se almacena en disco.

Ejemplos: Mega, Google Drive.

Problema: desperdicio de ancho de banda.

Streaming
El servidor envía datos en tiempo real.

No se guarda el archivo completo, solo un buffer temporal.

Solo se consume el ancho de banda equivalente al tiempo reproducido.

Ejemplos: Spotify, YouTube Live, radios online.

Ventaja: optimiza el ancho de banda.

2. Topologías de red aplicadas al streaming
Unicast
Conexión 1 a 1.

Si hay 100 oyentes → 100 conexiones.

Fórmula: BW_total = BW_stream × Nº_usuarios

Poco escalable.

Multicast
El servidor envía a una dirección multicast (224.0.0.0–239.255.255.255).

Los routers replican solo si hay suscriptores.

Útil solo en redes internas (Internet lo bloquea).

Broadcast
Envío a toda la red local.

No se usa para streaming profesional.

3. Capa de transporte: TCP vs UDP
TCP
Fiable: retransmite paquetes perdidos.

Usa ACK/NACK.

Pasa firewalls y NAT.

Desventaja: mayor latencia.

Ideal para: radio online, Netflix, Spotify, Twitch (receptor).

UDP
No retransmite paquetes.

Baja latencia.

Puede haber pérdidas.

Ideal para: videollamadas, juegos, WebRTC, RTSP.

4. QoS: Jitter y Buffer
Jitter
Variación en el tiempo de llegada de los paquetes.
Si el jitter supera el buffer → cortes.

Buffer
Memoria temporal para absorber jitter.
Más buffer = más estabilidad, pero más latencia.

Burst-on-Connect (Icecast)
El servidor envía una ráfaga inicial a máxima velocidad.

El buffer se llena rápido.

Reduce el tiempo hasta que empieza a sonar el audio.

5. Protocolos de Streaming
Modelos de capa de aplicación
HTTP Legacy (ICY / Icecast2)

HTTP Adaptativo (HLS / DASH)

Real-Time (RTMP, RTSP, WebRTC)

HTTP Legacy (ICY / Icecast2)
Flujo continuo por TCP.

Formatos: MP3, OGG, AAC.

No hay adaptación de calidad.

Puertos: 80, 443, 8000.

HTTP Adaptativo (HLS / DASH)
El vídeo se divide en chunks de 2–10 s.

Permite calidad adaptativa.

Formatos: .ts, .m4s.

Usado por Netflix, YouTube, Disney+.

Real-Time
RTMP: ingesta (OBS → YouTube/Twitch).

RTSP: cámaras IP (UDP para datos, TCP para control).

WebRTC: videollamadas, ultra baja latencia (<0.5 s).

6. Cuadro resumen
Protocolo | Base | Latencia | Uso | Firewall | CDN
Icecast (ICY) | TCP/HTTP | 10–30 s | Radio | Fácil | Difícil
HLS/DASH | TCP/HTTP | 15–45 s | VOD | Fácil | Excelente
RTMP | TCP | 2–5 s | Ingesta | Medio | No
WebRTC | UDP/TCP | <0.5 s | Videollamadas | Difícil | No
RTSP | UDP+TCP | <1 s | Cámaras | Problemas NAT | No

7. Códecs
Con pérdida
Eliminan información irrelevante.

Muy comprimidos.

Ejemplos: MP3, AAC, Vorbis.

Sin pérdida
No eliminan información.

Pesan más.

Ejemplos: FLAC, WAV.

8. Audio digital
Frecuencia de muestreo
Muestras por segundo.

Estándar: 44.1 kHz.

Profundidad de bits
Bits por muestra.

Estándar: 16 bits.

Canales
Mono (1), Estéreo (2), 5.1, 7.1…

9. Cálculo de peso (Audio)
Fórmula RAW
Peso = Frecuencia × Bits × Canales × Segundos

Ejemplo WAV
44100 × 16 × 2 × 180 = 31.75 MB

Con compresión
Peso = Bitrate × Tiempo

10. Vídeo
Contenedor
Incluye vídeo, audio, subtítulos y metadatos.
Ejemplos: MP4, MKV, MOV.

Cálculo RAW
Peso = (Ancho × Alto) × Profundidad × FPS × Tiempo

Bitrates recomendados (Vídeo)
Resolución	Calidad	Mínimo	Recomendado
4K	Ultra HD	15 Mbps	25–45 Mbps
1080p	Alta	4 Mbps	6–9 Mbps
720p	Media	1.5 Mbps	3–4 Mbps
480p	Estándar	500 kbps	1 Mbps
360p	Baja	400 kbps	700 kbps
12. Ejercicios típicos (muy probables en examen)
Audio
Peso WAV

Bitrate = frecuencia × bits × canales

Máximo de oyentes según ancho de banda

Ancho de banda total = bitrate × oyentes

Vídeo
Bitrate RAW

Espacio ocupado

Porcentaje de uso de red

Soluciones: bajar bitrate, usar H.265, usar CDN

Con códec
Peso = Bitrate × Tiempo
