# Clase — lunes 5 de octubre de 2026

**Profesor:** Bruno Perelli

repo del curso https://github.com/Hackspawn/MAM_ATB2026/

## Herramientas vistas en clases

- [Fritzing](https://fritzing.org/): herramienta para diseñar y documentar circuitos electrónicos.

## Arduino UNO R3

- **Voltaje de operación:** 5 V. Las entradas analógicas A0–A5 miden por defecto entre 0 V y 5 V, usando esa referencia. La entrada `VIN`/conector de alimentación es para alimentar la placa; no debe confundirse con el voltaje de operación de sus pines.

- **Resolución analógica:** el convertidor ADC es de 10 bits, por lo que representa `2^10 = 1024` niveles: valores enteros de `0` a `1023` (`0000000000₂` a `1111111111₂`).

- **Lectura en el UNO R3:** `analogRead()` siempre entrega una lectura analógica de 10 bits (un valor entre `0` y `1023`). Las entradas digitales, en cambio, se leen como un solo bit: `LOW` o `HIGH`.

- **Lectura digital:** `digitalRead(pin)` lee el nivel lógico presente en un pin digital y devuelve `LOW` (0) o `HIGH` (1). Si el pin está configurado como `OUTPUT`, devuelve el último estado que se escribió con `digitalWrite()`; para leer una señal externa, configura el pin como `INPUT`.

- **Salidas digitales:** se configuran con `pinMode(pin, OUTPUT)` y se escriben con `digitalWrite(pin, LOW)` o `digitalWrite(pin, HIGH)`. En el UNO R3, esos estados corresponden aproximadamente a 0 V y 5 V, respectivamente.
- Con la referencia predeterminada de 5 V, `analogRead(pin)` entrega aproximadamente `voltaje × 1023 / 5`. Cada paso equivale a unos `5 / 1024 ≈ 0,00488 V` (4,88 mV). Por ejemplo, 0 V da 0 y 5 V da 1023.

- **Fórmula del sistema binario:** cada dígito (bit) vale 0 o 1 y su posición determina una potencia de 2. De derecha a izquierda, las posiciones valen `2⁰, 2¹, 2², ...`. El número se calcula como `valor = bₙ·2ⁿ + ... + b₂·2² + b₁·2¹ + b₀·2⁰`. Ejemplo: `1011₂ = 1·2³ + 0·2² + 1·2¹ + 1·2⁰ = 11₁₀`.

- **Qué representan 0 y 1:** en binario son los dos estados posibles de un bit. En una entrada digital del Arduino, `LOW` (0) representa un nivel de voltaje bajo, cercano a 0 V, y `HIGH` (1) un nivel alto, cercano a 5 V en el UNO R3. En lógica, suelen interpretarse como falso/apagado y verdadero/encendido, respectivamente.

- **Corriente y LED:** la corriente es el flujo de carga eléctrica y se mide en amperios (A), normalmente en miliamperios (mA). Un LED tiene polaridad: pata larga al positivo (ánodo) y pata corta a GND (cátodo). Conéctalo con una resistencia en serie para limitar la corriente y proteger tanto el LED como el pin.

- **Cálculo de la resistencia:** ley de Ohm: `R = (Vfuente − VLED) / I`. Ejemplo: con 5 V, un LED rojo con caída aproximada de 2 V y una resistencia de `220 Ω`, la corriente es `(5 − 2) / 220 ≈ 0,0136 A = 13,6 mA`. El UNO R3 recomienda un máximo de 20 mA por pin; la caída de voltaje del LED varía según el tipo y el color.

## RGB, HSB y Lab

- **RGB (Red, Green, Blue):** describe el color mezclando luz roja, verde y azul. Es un modelo aditivo usado en pantallas: con los tres canales al máximo se obtiene blanco; con todos en cero, negro. En la notación común de 8 bits, cada canal va de 0 a 255; por ejemplo, `rgb(255, 0, 0)` es rojo.
- **HSB (Hue, Saturation, Brightness):** expresa el color mediante tono, saturación y brillo. El tono suele medirse como un ángulo de 0° a 360°; saturación y brillo, como porcentajes. Es una forma intuitiva de elegir y ajustar colores, representando los mismos colores RGB con parámetros distintos.
- **Lab (CIELAB):** usa `L*` para claridad (negro a blanco), `a*` para el eje verde–rojo y `b*` para el eje azul–amarillo. Está diseñado para describir colores según la percepción humana y no depende de un dispositivo específico como una pantalla concreta.

## C++: `void`

- `void` indica que una función no devuelve ningún valor. Se usa como tipo de retorno cuando la función realiza una acción, pero no entrega un resultado para guardar o usar en una expresión.
- En Arduino, `void setup()` se ejecuta una vez al iniciar la placa y `void loop()` se repite continuamente. Ambas funciones son `void` porque no devuelven un valor.
- Ejemplo:

  ```cpp
  void encenderLed() {
    digitalWrite(LED_BUILTIN, HIGH);
  }
  ```

  `encenderLed()` realiza una acción y no devuelve un dato.

Referencias: 

[Documentación del UNO R3](https://docs.arduino.cc/hardware/uno-rev3)

[Tutorial de lectura analógica](https://docs.arduino.cc/tutorials/uno-rev3-smd/AnalogReadSerial/)

[Ejemplo Blink y conexión del LED](https://docs.arduino.cc/built-in-examples/basics/Blink/)

[Modelos RGB, HSB y Lab (Adobe)](https://helpx.adobe.com/uk/creative-cloud/apps/colors/understand-color-modes.html)

[Especificación de color Lab y RGB (W3C)](https://www.w3.org/TR/2026/CRD-css-color-4-20260901/)
