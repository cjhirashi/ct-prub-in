# PRG1 SENSORES

Lectura de caudales del sistema desde sensores Dwyer MS, rango de medición de señal de entrada de *0-2"WC*

**PLENUM 1**

- VAV-01

- VAV-02

**PLENUM 2**

- VAV-01

- VAV-02

**PLENUM 4**

- VAV-01

- VAV-02

**PLENUM 5**

- VAV-01

- VAV-02

**PLENUM 6**

- VAV-01

- VAV-02

**PLENUM 7R**

- VAV-01

- VAV-02

## VARIABLES GLOBALES

> `P_APER` =  5 (%) | Porcentaje para activación de control de compuertas.

> `SINC` = 10 (seg.) | Tiempo de sincronización de datos

> `DEMANDA` (%) | Demanda de enfriamiento para apertura de compuerta por porcentaje

> `VAV` (%) | Porcentaje de apertura de compuerta

> `CM_BL` (On/Off) | Comando de apertura de compuerta de bloqueo

## MEDICION POR CAJA VAV

### VARIABLES LOCALES

> `ACTIV#` 

> `DEMANDA` | Se asigna la variable de demanda correspondiente a la caja monitoreada

### ACTIVACION DE CAJA

**ACTIVACION** El control de la compuerta se activa cuando la demanda de la compuerta se mayor a lo establecido en la variable `P_APER`

**DESACTIVACION** El control de la compuerta se desactiva cuando la demanda sea menor que 1%

```bash
    IF `DEMANDA` > `P_APER` THEN `ACTIV#` = 1
    IF DEMANDA < 1 THEN ACTIV1 = 0
```