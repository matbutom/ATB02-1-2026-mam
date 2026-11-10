# Clase — lunes 02 de noviembre de 2026

**Profesor:** Bruno Perelli

Materiales, apuntes y ejercicios de esta clase.

## Apuntes

### Sonic Pi

Entorno de programación musical en vivo basado en Ruby. Permite generar y secuenciar sonido mediante código, usando ciclos, muestras, sintetizadores y parámetros temporales. Su reloj lógico y las funciones de sincronización coordinan eventos musicales; los cambios en el código pueden ejecutarse durante la reproducción.

### Protocolos de comunicación

- **RX (recepción) y TX (transmisión):** abreviaturas habituales para indicar la dirección de los datos en una interfaz o dispositivo. RX recibe datos; TX los envía. No definen por sí solas el formato ni el transporte: estos dependen de la conexión y del protocolo utilizado.

- **MIDI (Musical Instrument Digital Interface):** protocolo de mensajes para controlar instrumentos y equipos musicales. Transmite eventos y controles —por ejemplo, nota, altura, velocidad, canal y cambios de control—, no audio digital. Puede transportarse por conexiones MIDI físicas o por MIDI sobre USB.

- **OSC (Open Sound Control):** protocolo de mensajes para intercambiar control y datos entre aplicaciones o dispositivos, comúnmente sobre UDP/IP. Los mensajes usan direcciones jerárquicas (por ejemplo, `/synth/frequency`) y pueden incluir valores tipados; es flexible para instalaciones y sistemas interactivos en red.
