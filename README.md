# Consola 1602 · v2

![build](https://github.com/zoraizmahmood/Consola-1602-v2/actions/workflows/build.yml/badge.svg)

> La segunda versión de la [Consola 1602](https://github.com/zoraizmahmood/Consola-1602): el mismo firmware, pero ahora sobre una **PCB propia** diseñada en KiCad y fabricada por **PCBWay**. Adiós a la protoboard y a los cables sueltos.

<p align="center">
  <img src="assets/pcb-3d.png" alt="Render 3D de la PCB de la Consola 1602 v2" width="720">
</p>

La v1 era un Arduino Uno, un LCD de 16x2, cinco botones y un zumbador unidos con cables dupont. Funcionaba, pero cualquier golpe soltaba un cable y no había forma de meterla en una caja decente. La v2 convierte todo ese cableado en un **shield** que se enchufa directamente encima del Arduino Uno: un único bloque compacto que entra en una carcasa a medida.

---

## Qué cambia respecto a la v1

| | v1 | v2 |
|---|---|---|
| Montaje | Protoboard y cables dupont | Shield PCB de dos capas que se enchufa al Uno |
| Contraste del LCD | Potenciómetro de 10 kΩ | Sin potenciómetro: V0 conectado a D8 |
| Zumbador | D8 | A2 |
| Resistencia de la retro | 220 Ω de inserción | R1 SMD 0805 |
| Carcasa | Pensada para el Uno suelto | Nueva, a medida de la PCB |
| Firmware | v1.1 | v2.0 (mismas aplicaciones, pines adaptados) |

Todas las aplicaciones de la v1 siguen ahí: reloj con dígitos grandes, Snake, Dino, Simon, test de reflejos, Pomodoro, notas, diagnóstico del sistema y ajustes en EEPROM. La documentación completa del firmware y su arquitectura está en el [repositorio de la v1](https://github.com/zoraizmahmood/Consola-1602#arquitectura).

---

## La placa

<p align="center">
  <img src="assets/pcb-top.png" alt="Cara superior de la PCB" width="420">
  <img src="assets/pcb-bottom.png" alt="Cara inferior de la PCB" width="420">
</p>

| Característica      | Valor                          |
|---------------------|--------------------------------|
| Tamaño              | 85,9 × 61,9 mm                 |
| Capas               | 2                              |
| Grosor              | 1,6 mm                         |
| Pista mínima        | 0,25 mm                        |
| Separación mínima   | 0,2 mm                         |
| Vías                | 9                              |
| Herramienta         | KiCad 10                       |
| Fabricante          | [PCBWay](https://www.pcbway.com) |

Los cinco botones forman una cruceta a la izquierda (`◄` `▲` `▼` `►`) y el `OK` queda solo a la derecha, como en un mando. El LCD ocupa toda la mitad superior y los conectores del Arduino quedan debajo, de modo que la placa se monta directamente encima del Uno.

### Archivos

| Ruta | Qué es |
|------|--------|
| [`hardware/pcb/placa.kicad_pro`](hardware/pcb/placa.kicad_pro) | Proyecto de KiCad |
| [`hardware/pcb/placa.kicad_sch`](hardware/pcb/placa.kicad_sch) | Esquema |
| [`hardware/pcb/placa.kicad_pcb`](hardware/pcb/placa.kicad_pcb) | Diseño de la placa |
| [`hardware/pcb/gerbers/`](hardware/pcb/gerbers/) | Gerber y taladros sueltos |
| [`hardware/pcb/gerbers-pcbway.zip`](hardware/pcb/gerbers-pcbway.zip) | El ZIP exacto que se subió a PCBWay |
| [`assets/esquema.pdf`](assets/esquema.pdf) | Esquema en PDF, para verlo sin KiCad |

### Pedir tu propia placa

1. Descarga [`gerbers-pcbway.zip`](hardware/pcb/gerbers-pcbway.zip).
2. Súbelo en el presupuesto rápido de PCBWay (o de cualquier otro fabricante: son Gerber estándar).
3. Las opciones por defecto valen: 2 capas, 1,6 mm, FR-4. El color de la máscara es a tu gusto.

---

## Mi experiencia con PCBWay

Esta versión existe gracias a que **PCBWay patrocinó la fabricación de las placas**. Lo dejo claro desde el principio: no he pagado las PCB. Lo que cuento aquí es mi experiencia real, incluidos los fallos (que fueron míos, no de ellos).

**Diseñar la primera PCB.** Hasta ahora todo lo había montado en protoboard, así que pasar a KiCad fue empezar de cero: esquema, asignar huellas, colocar componentes y rutar pistas. Lo más difícil no fue el rutado, sino decidir dónde iba cada cosa para que la placa encajara sobre el Arduino Uno y a la vez quedara cómoda en la mano. [COMPLETAR: cuánto tardaste en diseñarla, qué te costó más, si seguiste algún tutorial]

**El pedido.** Subir los Gerber fue rápido: la web los procesa al momento y enseña una vista previa de cada capa, lo que sirve para comprobar que no falta nada antes de pagar. [COMPLETAR: si hubo revisión manual del diseño, si te contactaron por algo, color de máscara y acabado elegidos]

**El tiempo.** [COMPLETAR: días de fabricación, días de envío y a qué país, si hubo aduanas]

**La calidad.** [COMPLETAR: cómo llegaron (embalaje, cantidad), nitidez de la serigrafía, alineación de la máscara, si todos los taladros eran del tamaño correcto]

**El montaje.** [COMPLETAR: cómo fue soldar, si todo encajó a la primera, si el LCD y los botones quedaron bien alineados]

**Lo que haría distinto.** [COMPLETAR: errores de diseño que encontraste al montar, qué cambiarías en una v3]

**En resumen:** pasar de la protoboard a una PCB fabricada ha sido el salto más grande del proyecto. Ver tu propio diseño convertido en una placa real, con tu nombre en la serigrafía, es otra cosa. Si estás pensando en hacer tu primera PCB, hazla.

<!-- Añade aquí fotos reales:
<p align="center">
  <img src="assets/foto-placas.jpg" alt="Las placas recién llegadas de PCBWay" width="420">
  <img src="assets/foto-montada.jpg" alt="La consola montada" width="420">
</p>
-->

---

## Materiales

| Componente                              | Ref.      | Cantidad |
|-----------------------------------------|-----------|----------|
| PCB Consola 1602 v2                     | —         | 1        |
| Arduino Uno R3                          | —         | 1        |
| LCD 16x2 con HD44780 (WC1602A o similar)| LCD1      | 1        |
| Pulsador táctil 6×6 mm de inserción     | SW1–SW5   | 5        |
| Zumbador activo de 5 V, 12 mm           | BZ1       | 1        |
| Resistencia 220 Ω, SMD 0805             | R1        | 1        |
| Tira de pines de 2,54 mm 1x8            | J1, J4    | 2        |
| Tira de pines de 2,54 mm 1x10           | J2        | 1        |
| Tira de pines de 2,54 mm 1x6            | J3        | 1        |

Ya no hace falta el potenciómetro de 10 kΩ ni la protoboard.

---

## Conexiones

En la v2 el cableado lo fija la placa, pero conviene tenerlo a mano para depurar:

| Señal                | Pin del Uno | En la PCB |
|----------------------|-------------|-----------|
| LCD `RS`             | D12         | LCD1-4    |
| LCD `E`              | D11         | LCD1-6    |
| LCD `D4–D7`          | D5, D4, D3, D2 | LCD1-11…14 |
| LCD `V0` (contraste) | D8          | LCD1-3    |
| LCD `A` (retro)      | D9 a través de R1 | LCD1-15 |
| `▲`                  | D6          | SW2       |
| `▼`                  | D7          | SW4       |
| `◄`                  | D10         | SW1       |
| `►`                  | A0          | SW3       |
| `OK`                 | A1          | SW5       |
| Zumbador             | A2          | BZ1       |

**Sobre el contraste:** la v1 usaba un potenciómetro en `V0`. En la placa ese pin va a D8 y el firmware lo pone a `LOW`, que equivale a contraste máximo y en los LCD de 5 V se lee bien. Así la placa se queda sin una pieza y sin un ajuste que hacer a mano.

Los pines **A4** y **A5** siguen libres para añadir un RTC DS3231.

---

## Carcasa

La carcasa de la v2 está rediseñada para la PCB. Los archivos irán en [`hardware/carcasa/`](hardware/carcasa/).

<!-- Añade aquí un render de la carcasa:
<p align="center">
  <img src="assets/carcasa-v2.png" alt="Render de la carcasa v2" width="480">
</p>
-->

| Parámetro          | Valor        |
|--------------------|--------------|
| Material           | PLA          |
| Altura de capa     | 0,2 mm       |
| Relleno            | 20 %         |
| Soportes           | No           |
| Perímetros         | 3            |

---

## Cargar el firmware

Solo hace falta la librería `LiquidCrystal`, que viene incluida en el IDE de Arduino.

```bash
git clone https://github.com/zoraizmahmood/Consola-1602-v2.git
cd Consola-1602-v2

arduino-cli compile --fqbn arduino:avr:uno .
arduino-cli upload  --fqbn arduino:avr:uno -p /dev/ttyACM0 .
```

También puedes abrir `Consola-1602-v2.ino` en el IDE de Arduino y subirlo con `Ctrl+U`.

| Recurso                  | Uso      | Máximo del Uno | Ocupación |
|--------------------------|----------|----------------|-----------|
| Memoria de programa      | 15 238 B | 32 256 B       | 47 %      |
| RAM (variables globales) | 622 B    | 2 048 B        | 30 %      |

El [`diagram.json`](diagram.json) de [Wokwi](https://wokwi.com) está actualizado al cableado de la v2, así que puedes probar el firmware en el navegador antes de soldar nada.

---

## Estructura del proyecto

```
Consola-1602-v2/
├── Consola-1602-v2.ino      # Firmware adaptado a la PCB
├── diagram.json             # Cableado para el simulador de Wokwi
├── wokwi.toml
├── hardware/
│   ├── pcb/
│   │   ├── placa.kicad_pro  # Proyecto de KiCad
│   │   ├── placa.kicad_sch  # Esquema
│   │   ├── placa.kicad_pcb  # Diseño de la placa
│   │   ├── gerbers/         # Gerber y taladros
│   │   └── gerbers-pcbway.zip
│   └── carcasa/             # Carcasa v2 (Fusion 360 + STL)
├── assets/                  # Renders, esquema en PDF y fotos
└── .github/workflows/
    └── build.yml            # Compilación automática para arduino:avr:uno
```

---

## Agradecimientos

A [PCBWay](https://www.pcbway.com) por patrocinar la fabricación de las placas de esta versión.

## Autor

Creado por [zoraizmahmood](https://github.com/zoraizmahmood).

## Licencia

El firmware, bajo licencia [MIT](LICENSE). El hardware de `hardware/` (PCB y carcasa), bajo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.es).
