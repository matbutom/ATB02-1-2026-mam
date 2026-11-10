# Clase — lunes 9 de noviembre de 2026

**Profesor:** Bruno Perelli

Materiales, apuntes y ejercicios de esta clase.

## Apuntes

### Comunicación entre circuitos: I²C y SPI

I²C y SPI son protocolos seriales síncronos usados para comunicar microcontroladores con periféricos, como sensores, pantallas y memorias. En ambos, una señal de reloj coordina el intercambio de bits; cada dispositivo debe ser compatible con el protocolo y sus niveles eléctricos.

#### I²C (Inter-Integrated Circuit)

- Usa dos líneas compartidas: **SDA** lleva los datos y **SCL** el reloj. Los dispositivos se conectan al mismo bus.
- Cada dispositivo tiene una **dirección**; el controlador inicia la comunicación y selecciona a qué dispositivo enviar o del que recibir datos. En un bus pueden coexistir varios dispositivos, siempre que no tengan direcciones en conflicto.
- Las líneas suelen ser de tipo *open-drain/open-collector* y requieren resistencias **pull-up**. No se deben conectar directamente dispositivos con tensiones incompatibles.
- La transferencia incluye condiciones de inicio y parada, dirección, bits de datos y confirmaciones (**ACK/NACK**). Puede haber más de un controlador, aunque la configuración y el arbitraje añaden complejidad.
- **Ventaja:** requiere pocos cables y facilita compartir el bus. **Costo:** suele ser más lento que SPI y los dispositivos comparten el mismo medio, por lo que no transmiten simultáneamente.

#### SPI (Serial Peripheral Interface)

- En su forma habitual usa **SCLK** (reloj), **MOSI** (datos del controlador al periférico), **MISO** (datos del periférico al controlador) y una línea **CS/SS** para seleccionar cada periférico.
- Los periféricos comparten reloj y líneas de datos, pero normalmente cada uno necesita su propia línea CS. Al activar la selección, el controlador inicia la transferencia.
- Es **dúplex completo**: se pueden enviar y recibir bits al mismo tiempo. No define una dirección ni un mecanismo de confirmación universal; el formato de los mensajes depende del dispositivo.
- El modo de reloj se configura con **CPOL** y **CPHA** (polaridad y fase); controlador y periférico deben coincidir. También deben respetarse la frecuencia máxima y los tiempos indicados en la hoja de datos.
- **Ventaja:** suele ofrecer mayor velocidad y una transferencia sencilla. **Costo:** usa más líneas, especialmente al añadir periféricos, y requiere gestionar la selección de cada uno.

#### Comparación práctica

| Aspecto | I²C | SPI |
|---|---|---|
| Líneas principales | 2 compartidas (SDA, SCL) | 3 compartidas (SCLK, MOSI, MISO) más CS por periférico |
| Selección del periférico | Dirección enviada por el bus | Línea CS dedicada, generalmente |
| Confirmación | ACK/NACK | No hay confirmación universal en el protocolo |
| Transferencia simultánea en ambos sentidos | No, normalmente alterna lectura y escritura | Sí, dúplex completo |
| Uso habitual | Varios periféricos con pocos pines y velocidad moderada | Transferencias rápidas y periféricos con selección dedicada |

La elección depende de los periféricos disponibles, la cantidad de pines, la velocidad necesaria y las distancias de cableado. Antes de conectar, revisar en las hojas de datos la tensión lógica, la frecuencia, el modo de reloj (SPI) y las resistencias pull-up requeridas (I²C).
