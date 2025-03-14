# PRG1_SENSORES (CONTROL: Cuarto de pruebas - DI 10021)

## Descripción

Este programa transforma la lectura del sensor de entrada que mide la velocidad del aire en presión diferencial, calibra esta lectura (aplicando un multiplicador y un offset), y convierte la lectura de presión dinámica a caudal de aire (CFM).

## Autor

CARLOS JIMENEZ HIRASHI @cjhirashi

## Versión

1.5.0

## Fecha

2024-05-16

## Declaración de Variables del Sistema

El programa utiliza variables locales para cada VAV (Variable Air Volume) en cada Plenum para facilitar la gestión y comprensión del código.

### Variables por Plenum y VAV

A continuación, se describen las variables utilizadas para cada VAV:

*   `P#_VM_CV`: Coeficiente de Velocidad de VAV Mediana (Plenum #)
*   `P#_VM_IN`: Lectura del sensor de velocidad de VAV Mediana (Plenum #)
*   `P#_VM_DP`: Lectura del sensor de velocidad calibrado de VAV Mediana (Plenum #)
*   `P#_VM_Q`: Conversión de lectura de sensor a Caudales de VAV Mediana (Plenum #)
*   `P#_VM_M`: Factor Multiplicador de VAV Mediana (Plenum #)
*   `P#_VM_O`: Factor Offset de VAV Mediana (Plenum #)

*   `P#_VG_CV`: Coeficiente de Velocidad de VAV Grande (Plenum #)
*   `P#_VG_IN`: Lectura del sensor de velocidad de VAV Grande (Plenum #)
*   `P#_VG_DP`: Lectura del sensor de velocidad calibrado de VAV Grande (Plenum #)
*   `P#_VG_Q`: Conversión de lectura de sensor a Caudales de VAV Grande (Plenum #)
*   `P#_VG_M`: Factor Multiplicador de VAV Grande (Plenum #)
*   `P#_VG_O`: Factor Offset de VAV Grande (Plenum #)

*   `P#_VC_CV`: Coeficiente de Velocidad de VAV Chica (Plenum #)
*   `P#_VC_IN`: Lectura del sensor de velocidad de VAV Chica (Plenum #)
*   `P#_VC_DP`: Lectura del sensor de velocidad calibrado de VAV Chica (Plenum #)
*   `P#_VC_Q`: Conversión de lectura de sensor a Caudales de VAV Chica (Plenum #)
*   `P#_VC_M`: Factor Multiplicador de VAV Chica (Plenum #)
*   `P#_VC_O`: Factor Offset de VAV Chica (Plenum #)

Donde `#` es el número del Plenum (1, 2, 3, 4, 5, 6, R7).

### Variables para Caudales Totales

*   `P#_Q`: Caudal total del Plenum #, calculado como la suma de los caudales de cada VAV en el plenum.

### Puntos de Entrada/Salida

*   `AI#`: Puntos de entrada analógicos (sensores de velocidad).
*   `AV#`: Puntos analógicos variables (valores calibrados, caudales, etc.).
*   `10022.AV###`: Puntos analógicos del controlador 10022 donde se leen los coeficientes de velocidad.

### Lectura de Coeficientes de Velocidad (CV)

Los Coeficientes de Velocidad (CV) se leen desde los puntos analógicos del controlador `10022.AV###` cada minuto, utilizando la función `INTERVAL(00:01:00)`. Esto permite actualizar los valores de CV dinámicamente.

## Lógica de Control

La lógica de control se divide en las siguientes secciones:

1.  **Calibración del Sensor de Entrada:** Se aplica un factor multiplicador y un offset a la lectura del sensor de velocidad para calibrar la lectura:

    ```
    P#_XX_DP = MAX(0, ((P#_XX_IN * P#_XX_M) + P#_XX_O))
    ```

2.  **Conversión a Caudal:** Se utiliza el Coeficiente de Velocidad (CV) para convertir la lectura calibrada a caudal:

    ```
    P#_XX_Q = MAX(0, (P#_XX_CV * ((P#_XX_DP)^0.5)))
    ```

    Donde `XX` es el tipo de VAV (VM, VG, VC).

## Cálculos de Caudales Totales

Los caudales totales de cada plenum se calculan sumando los caudales de cada VAV en el plenum y se asignan a las variables AV correspondientes:

*   `AV9 = P1_VM_Q + P1_VG_Q + P1_VC_Q` (Plenum 1)
*   `AV18 = P2_VM_Q + P2_VG_Q` (Plenum 2)
*   `AV31 = P4_VM_Q + P4_VG_Q + P4_VC_Q` (Plenum 4)
*   `AV40 = P5_VC_Q + P5_VG_Q` (Plenum 5)
*   `AV49 = P6_VG_Q + P6_VM_Q` (Plenum 6)
*   `AV58 = PR7_VC_Q + PR7_VG_Q` (Plenum R7)

## Notas Adicionales

*   La función `MAX(0, valor)` se utiliza para asegurar que los valores de presión diferencial y caudal no sean negativos.
*   El programa está diseñado para ser modular y fácil de mantener, con variables locales claramente definidas para cada VAV y plenum.