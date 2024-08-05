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

> `ACTIV` 

> `DEMANDA` | Se asigna la variable de demanda correspondiente a la caja monitoreada

### ACTIVACION DE CAJA

***ACTIVACION*** El control de la compuerta se activa cuando la `DEMANDA` de la compuerta sea mayor a lo establecido en la variable `P_APER`

***DESACTIVACION*** El control de la compuerta se desactiva cuando la `DEMANDA` sea menor que 1%

```bash
    IF `DEMANDA` > `P_APER` THEN `ACTIV` = 1
    IF `DEMANDA` < 1 THEN `ACTIV` = 0
```

### ASIGNACION DE DEMANDA A COMPUETAS POR ESTADO DE ACTIVACIÓN

Cuando el estado de `ACTIV` sea *On*, se asignará el porcentaje de `DEMANDA` actual a la compuerta `VAV ` y el estado de apertura de la compueta de bloqueo `CM_BL`

Cuando el estado de `ACTIV` sea *Off*, se asignará a control de compuerta `VAV` 0% y a control de compuerta de bloqueo `CM_BL` Off

```bash
    IF `ACTIV1` = 1 THEN `CM_BL` = 1, `VAV` = `DEMANDA` ELSE `CM_BL` = 1, `VAV` = 0
```

