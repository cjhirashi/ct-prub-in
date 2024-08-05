# CONTROL DE CUARTO DE PRUEBA (CONTROLADOR 1)

Programas para operación de cajas VAV del sistema del Cuarto de Pruebas.

## PROGRAMAS

### PRG1_SENSORES

Lectura de caudales del sistema


### PRG2_VAVS

Control de de apertura de compuertas por flujo de aire en cajas VAV

#### PLENUM 1

- VAV-01

- VAV-02

#### PLENUM 2

- VAV-01

- VAV-02

#### PLENUM 4

- VAV-01

- VAV-02

#### PLENUM 5

- VAV-01

- VAV-02

#### PLENUM 6

- VAV-01

- VAV-02

#### PLENUM 7R

- VAV-01

- VAV-02


## PUNTOS DE CONTROL

### ENTRADAS

> `AI3` **P1_VM_DP**    PLENUM 1, VAV 01 - MEDIANA, PRES DIF
>
> `AI4` **P1_VG_DP**    PLENUM 1, VAV 02 - GRANDE, PRES DIF
>
> `AI5` **P2_VM_DP**    PLENUM 2, VAV 01 - MEDIANA, PRES DIF
>
> `AI6` **P2_VG_DP**    PLENUM 2, VAV 02 - GRANDE, PRES DIF
>
> `AI7` **P4_VM_DP**    PLENUM 4, VAV 01 - MEDIANA, PRES DIF
>
> `AI8` **P4_VG_DP**    PLENUM 4, VAV 02 - GRANDE, PRES DIF
>
> `AI9` **P4_VC_DP**    PLENUM 4, VAV 03 - CHICA, PRES DIF
>
> `AI10` **P5_VC_DP**    PLENUM 5, VAV 01 - CHICA, PRES DIF
>
> `AI11` **P5_VG_DP**    PLENUM 5, VAV 02 - GRANDE, PRES DIF
>
> `AI12` **P6_VG_DP**    PLENUM 6, VAV 01 - GRANDE, PRES DIF
>
> `AI13` **P6_VM_DP**    PLENUM 6, VAV 02 - MEDIANA, PRES DIF
>
> `AI14` **PR7_VC_DP**    PLENUM R7, VAV 01 - CHICA, PRES DIF
>
> `AI15` **PR7_VG_DP**    PLENUM R7, VAV 02 - GRANDE, PRES DIF
>
> `AI16` **P1_DP-1**    PLENUM 1, CAIDA DE PRESION 1
>
> `AI17` **P1_DP-2**    PLENUM 1, CAIDA DE PRESION 2
>
> `AI18` **P2_DP**    PLENUM 2, CAIDA DE PRESION

### SALIDAS