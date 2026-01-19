# SERVICIOS DE REDES

## Servicios de streaming
### Icecast y Mixxx


1. Requisitos previos
En el servidor (Icecast)

    Icecast2 instalado y funcionando.

    Puerto 8000/TCP abierto en UFW.

    Archivo de configuración /etc/icecast2/icecast.xml con la contraseña del usuario source.

En la máquina DJ

    Mixxx instalado.

    Sonido funcionando correctamente.

    Conectividad con el servidor Icecast (ping a la IP).

2. Configuración del servidor Icecast

El archivo principal es:


/etc/icecast2/icecast.xml

Los parámetros importantes son:


<authentication>
    <source-password>sourcepassword</source-password>
    <relay-password>relaypassword</relay-password>
    <admin-password>adminpassword</admin-password>
</authentication>

Reiniciar Icecast tras cualquier cambio:


sudo systemctl restart icecast2

Comprobar que está activo:


systemctl status icecast2

Acceso web:


http://172.30.16.133:8000

3. Configuración de Mixxx para emitir

Abrir Mixxx → Preferencias → Emisión en vivo.

Seleccionar una fuente de emisión y configurar:
3.1 Conexión al servidor
Campo	Valor
Tipo	Icecast2
Servidor	IP del servidor Icecast
Puerto	8000
Montar	/eug
Usuario	source
Contraseña	la definida en Icecast

Ejemplo de mountpoint:

/eug

3.2 Codificación

Recomendado:

    Formato: MP3

    Tasa de bits: 128 kbps

    Canales: Estéreo

3.3 Opciones adicionales

    Activar Reconexión automática

    Activar Emitir al aplicar cambios

    (Opcional) Marcar Transmisión pública para que aparezca en la página principal de Icecast

Aplicar los cambios.
4. Iniciar la emisión

    Cargar una pista en Mixxx.

    Subir el volumen del canal y del máster.

    Activar la emisión (si no se activa automáticamente).

Si la conexión es correcta, Mixxx muestra el estado como Conectado.
5. Comprobación desde el navegador o VLC
Navegador (máquina anfitrión o cualquier equipo de la red)


http://172.30.16.133:8000/eug

Ejemplo:


http://172.30.16.133:8000/eug

VLC

    Abrir VLC → Medio → Abrir ubicación de red

    Introducir la URL del mountpoint

6. Verificación en la interfaz web de Icecast

Acceder a:

http://IP_DEL_SERVIDOR:8000

En la sección Mountpoints debe aparecer tu radio:
Código

/eugcasdes

Al hacer clic, se debe reproducir el audio emitido desde Mixxx.
