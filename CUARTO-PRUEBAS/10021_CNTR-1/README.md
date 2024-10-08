# CONTROL DE CUARTO DE PRUEBAS - CONTROLADOR 1

Sistema de control para la operación de las cajas VAV del *CUARTO DE PRUEBAS*

## TARJETAS DE CONTROL

> Controlador KMC [**BAC-5901C**](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/ "Documentación de equipo")
>
> - 8 Entradas Universales, 8 Salidas Universales
> - Puerto *RS-485* **BACnet MS/TP**
> - Alimentación a ***24 VAC/DC***

> Módulo de expansión KMC [**CAN-5901**](https://www.kmccontrols.com/product/expansion-io-module-8-ui-8-uo/ "Documentación de equipo")
>
> - 8 Entradas Universales, 8 Salidas Universales
> - Alimentación a ***24 VAC/DC***

## PROGRAMAS

### PRG1_SENSORES

Control de medición de caudales del sistema, a través de la señal medida por los transmisores de presión diferencial de las cajas Dwayer **MS-311**, rango de medición *0-2"WC*

### PRG2_VAVS

Control de apertura de compuerta de ***VAV*** por demanda de control de suministro de aire por CFMs y control de apertura de compuerta de bloqueo de aire.

### PRG3_PLENUMS

Control de caudal de aire por plenums, este programa asigna las variables para operación del plenum, a las cajas VAV del Plenum activo

### PRG4_DEMANDA

### PRG5_UMA

### PRG6_CALIBRACION

## PUNTOS DE CONTROL

_____

### ENTRADAS

> ***AI3*** | `P1_VM_DP` [ *"WC* ] | PLENUM 1, VAV 01 - MEDIANA, PRES DIF
>
> ***AI4*** | `P1_VG_DP` [ *"WC* ] | PLENUM 1, VAV 02 - GRANDE, PRES DIF
>
> ***AI5*** | `P2_VM_DP` [ *"WC* ] | PLENUM 2, VAV 01 - MEDIANA, PRES DIF
>
> ***AI6*** | `P2_VG_DP` [ *"WC* ] | PLENUM 2, VAV 02 - GRANDE, PRES DIF
>
> ***AI7*** | `P4_VM_DP` [ *"WC* ] | PLENUM 4, VAV 01 - MEDIANA, PRES DIF
>
> ***AI8*** | `P4_VG_DP` [ *"WC* ] | PLENUM 4, VAV 02 - GRANDE, PRES DIF
>
> ***AI9*** | `P4_VC_DP` [ *"WC* ] | PLENUM 4, VAV 03 - CHICA, PRES DIF
>
> ***AI10*** | `P5_VC_DP` [ *"WC* ] | PLENUM 5, VAV 01 - CHICA, PRES DIF
>
> ***AI11*** | `P5_VG_DP` [ *"WC* ] | PLENUM 5, VAV 02 - GRANDE, PRES DIF
>
> ***AI12*** | `P6_VG_DP` [ *"WC* ] | PLENUM 6, VAV 01 - GRANDE, PRES DIF
>
> ***AI13*** | `P6_VM_DP` [ *"WC* ] | PLENUM 6, VAV 02 - MEDIANA, PRES DIF
>
> ***AI14*** | `PR7_VC_DP` [ *"WC* ] | PLENUM R7, VAV 01 - CHICA, PRES DIF
>
> ***AI15*** | `PR7_VG_DP` [ *"WC* ] | PLENUM R7, VAV 02 - GRANDE, PRES DIF
>
> ***AI16*** | `P1_DP-1` [ *"WC* ] | PLENUM 1, CAIDA DE PRESION 1
>
> ***AI17*** | `P1_DP-2` [ *"WC* ] | PLENUM 1, CAIDA DE PRESION 2
>
> ***AI18*** | `P2_DP` [ *"WC* ] | PLENUM 2, CAIDA DE PRESION

### SALIDAS