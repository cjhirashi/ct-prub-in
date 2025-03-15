## PRG2 - CONTROL DE COMPUERTAS DE VAVS

Este programa Control Basic, implementado en el controlador con Device Instance 10021, tiene como objetivo activar y desactivar el control de las compuertas (VAV y de bloqueo) en 15 VAVs distribuidas en 7 Plenums, basándose en la demanda de operación de cada compuerta.

---
### INFORMACION DEL SISTEMA

*   **AUTOR**: CARLOS JIMENEZ HIRASHI @cjhirashi
*   **DI**: 10021
*   **VERSION**: 1.5.0
*   **FECHA**: 14/MAR/2025

---
### LISTA DE PUNTOS

| VARIABLE DE CONTROL | NOMBRE DE PUNTO | DESCRIPCION | TIPO | VALOR/PUNTO DE CONTROL |
|---|---|---|---|---|
| PORC_ACTIV |  | Porcentaje de activación del control de compuertas | CONSTANTE | 5 |
| P1_VM_DM | `P1_VM_DM` | PLENUM 1 - VAV MEDIANA - DEMANDA | AV | AV85 |
| P1_VM_A | `P1_VM_A` | PLENUM 1, VAV 01 - MEDIANA, COMPUERTA VAV | AO | AO1 |
| P1_VM_AB | `P1_VM_AB` | PLENUM 1, VAV 01 - MEDIANA, COMPUERTA BLOQUEO | BO | BO14 |
| P1_VG_DM | `P1_VG_DM` | PLENUM 1 - VAV GRANDE - DEMANDA | AV | AV86 |
| P1_VG_A | `P1_VG_A` | PLENUM 1, VAV 02 - GRANDE, COMPUERTA VAV | AO | AO2 |
| P1_VG_AB | `P1_VG_AB` | PLENUM 1, VAV 02 - GRANDE, COMPUERTA BLOQUEO | BO | BO15 |
| P1_VC_DM | `P1_VC_DM` | PLENUM 1, VAV03 - CHICA, DEMANDA | AV | AV67 |
| P1_VC_A | `P1_VC_A` | PLENUM 1, VAV 03 - CHICA, COMPUERTA VAV | AO | AO21 |
| P1_VC_AB | `P1_VC_AB` | PLENUM 1, VAV 03 - CHICA, COMPUERTA BLOQUEO | BO | BO22 |
| P2_VM_DM | `P2_VM_DM` | PLENUM 2 - VAV MEDIANA - DEMANDA | AV | AV87 |
| P2_VM_A | `P2_VM_A` | PLENUM 2, VAV 01 - MEDIANA, COMPUERTA VAV | AO | AO3 |
| P2_VM_AB | `P2_VM_AB` | PLENUM 2, VAV 01 - MEDIANA, COMPUERTA BLOQUEO | BO | BO16 |
| P2_VG_DM | `P2_VG_DM` | PLENUM 2 - VAV GRANDE - DEMANDA | AV | AV88 |
| P2_VG_A | `P2_VG_A` | PLENUM 2, VAV 02 - GRANDE, COMPUERTA VAV | AO | AO4 |
| P2_VG_AB | `P2_VG_AB` | PLENUM 2, VAV 02 - GRANDE, COMPUERTA BLOQUEO | BO | BO1 |
| P3_VG_DM | `P3_VG_DM` | PLENUM 3, VAV01 - GRANDE, DEMANDA | AV | AV68 |
| P3_VG_A | `P3_VG_A` | PLENUM 3, VAV 01 - GRANDE, COMPUERTA VAV | AO | AO23 |
| P3_VG_AB | `P3_VG_AB` | PLENUM 3, VAV 01 - GRANDE, COMPUERTA BLOQUEO | BO | BO24 |
| P4_VM_DM | `P4_VM_DM` | PLENUM 4 - VAV MEDIANA - DEMANDA | AV | AV89 |
| P4_VM_A | `P4_VM_A` | PLENUM 4, VAV 01 - MEDIANA, COMPUERTA VAV | AO | AO5 |
| P4_VM_AB | `P4_VM_AB` | PLENUM 4, VAV 01 - MEDIANA, COMPUERTA BLOQUEO | BO | BO2 |
| P4_VG_DM | `P4_VG_DM` | PLENUM 4 - VAV GRANDE - DEMANDA | AV | AV90 |
| P4_VG_A | `P4_VG_A` | PLENUM 4, VAV 02 - GRANDE, COMPUERTA VAV | AO | AO6 |
| P4_VG_AB | `P4_VG_AB` | PLENUM 4, VAV 02 - GRANDE, COMPUERTA BLOQUEO | BO | BO3 |
| P4_VC_DM | `P4_VC_DM` | PLENUM 4 - VAV CHICA - DEMANDA | AV | AV91 |
| P4_VC_A | `P4_VC_A` | PLENUM 4, VAV 03 - CHICA, COMPUERTA VAV | AO | AO7 |
| P4_VC_AB | `P4_VC_AB` | PLENUM 4, VAV 03 - CHICA, COMPUERTA BLOQUEO | BO | BO4 |
| P5_VC_DM | `P5_VC_DM` | PLENUM 5 - VAV CHICA - DEMANDA | AV | AV92 |
| P5_VC_A | `P5_VC_A` | PLENUM 5, VAV 01 - CHICA, COMPUERTA VAV | AO | AO8 |
| P5_VC_AB | `P5_VC_AB` | PLENUM 5, VAV 01 - CHICA, COMPUERTA BLOQUEO | BO | BO5 |
| P5_VG_DM | `P5_VG_DM` | PLENUM 5 - VAV GRANDE - DEMANDA | AV | AV93 |
| P5_VG_A | `P5_VG_A` | PLENUM 5, VAV 02 - GRANDE, COMPUERTA VAV | AO | AO9 |
| P5_VG_AB | `P5_VG_AB` | PLENUM 5, VAV 02 - GRANDE, COMPUERTA BLOQUEO | BO | BO6 |
| P6_VG_DM | `P6_VG_DM` | PLENUM 6 - VAV GRANDE - DEMANDA | AV | AV94 |
| P6_VG_A | `P6_VG_A` | PLENUM 6, VAV 01 - GRANDE, COMPUERTA VAV | AO | AO10 |
| P6_VG_AB | `P6_VG_AB` | PLENUM 6, VAV 01 - GRANDE, COMPUERTA BLOQUEO | BO | BO7 |
| P6_VM_DM | `P6_VM_DM` | PLENUM 6 - VAV MEDIANA - DEMANDA | AV | AV95 |
| P6_VM_A | `P6_VM_A` | PLENUM 6, VAV 02 - MEDIANA, COMPUERTA VAV | AO | AO11 |
| P6_VM_AB | `P6_VM_AB` | PLENUM 6, VAV 02 - MEDIANA, COMPUERTA BLOQUEO | BO | BO8 |
| PR7_VC_DM | `PR7_VC_DM` | PLENUM R7 - VAV CHICA - DEMANDA | AV | AV96 |
| PR7_VC_A | `PR7_VC_A` | PLENUM R7, VAV 01 - CHICA, COMPUERTA VAV | AO | AO12 |
| PR7_VC_AB | `PR7_VC_AB` | PLENUM R7, VAV 01 - CHICA, COMPUERTA BLOQUEO | BO | BO17 |
| PR7_VG_DM | `PR7_VG_DM` | PLENUM R7 - VAV GRANDE - DEMANDA | AV | AV97 |
| PR7_VG_A | `PR7_VG_A` | PLENUM R7, VAV 02 - GRANDE, COMPUERTA VAV | AO | AO13 |
| PR7_VG_AB | `PR7_VG_AB` | PLENUM R7, VAV 02 - GRANDE, COMPUERTA BLOQUEO | BO | BO18 |

---
### LOGICA DE OPERACION

El programa itera a través de cada VAV en cada Plenum y aplica la siguiente lógica:

1.  **Activación/Desactivación:**

    *   Si el valor de la demanda (`DM`) es mayor que el porcentaje de activación definido por la constante `PORC_ACTIV` (actualmente 5), se activa el control de la compuerta (`ACTIV` = 1).
    *   Si el valor de la demanda (`DM`) es menor que 1, se desactiva el control de la compuerta (`ACTIV` = 0).

    ```
    IF P1_VM_DM > PORC_ACTIV THEN P1_VM_ACTIV = 1
    IF P1_VM_DM < 1 THEN P1_VM_ACTIV = 0
    ```
2.  **Control de Compuertas:**

    *   Si el control de la compuerta está activo (`ACTIV` = 1):

        *   El valor de la compuerta VAV (`A`) se establece igual al valor de la demanda (`DM`).
        *   La compuerta de bloqueo (`AB`) se abre (valor 1).
        
    *   Si el control de la compuerta está inactivo (`ACTIV` = 0):

        *   El valor de la compuerta VAV (`A`) se establece en 0.
        *   La compuerta de bloqueo (`AB`) se cierra (valor 0).

    ```
    IF P1_VM_ACTIV THEN 
        P1_VM_A = P1_VM_DM
        P1_VM_AB = 1 
    ELSE 
        P1_VM_A = 0
        P1_VM_AB = 0
    ENDIF
    ```

Esta lógica se repite para cada VAV en cada Plenum, asegurando que el sistema responda adecuadamente a las condiciones de demanda en cada zona.