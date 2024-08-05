# PRG2 VAVS

Control de apertura de compuerta de VAV por demanda de control de suministro de aire por *CFMs* y control de apertura de compuerta de bloqueo de aire.

## VARIABLES GLOBALES

> `P_APER` =  5 (%) | Porcentaje para activación de control de compuertas.

> `SINC` = 10 (seg.) | Tiempo de sincronización de datos

> `DEMANDA` (%) | Demanda de enfriamiento para apertura de compuerta por porcentaje

> `VAV` (%) | Porcentaje de apertura de compuerta

> `CM_BL` (On/Off) | Comando de apertura de compuerta de bloqueo

## MEDICION POR CAJA VAV

### VARIABLES LOCALES

> `ACTIV` 

> `DEMANDA` [AV] | Se asigna la variable de demanda correspondiente a la caja monitoreada

### ACTIVACION DE CAJA

***ACTIVACION*** El control de la compuerta se activa cuando la `DEMANDA` de la compuerta sea mayor a lo establecido en la variable `P_APER`

***DESACTIVACION*** El control de la compuerta se desactiva cuando la `DEMANDA` sea menor que 1%

```bash
			REM ***ACTIVACION DE CAJA
				IF DEMANDA > P_APER THEN ACTIV = 1
				IF DEMANDA < 1 THEN ACTIV = 0
```

### ASIGNACION DE DEMANDA A COMPUETAS POR ESTADO DE ACTIVACIÓN

Cuando el estado de `ACTIV` sea *On*, se asignará al control de compuerta `VAV` el valor de `DEMANDA` y a la compueta de bloqueo `CM_BL` el valor de *On*

Cuando el estado de `ACTIV` sea *Off*, se asignará al control de compuerta `VAV` el valor de 0% y a la compueta de bloqueo `CM_BL` el valor de *Off*

```bash
			REM ***CONTROL DE COMPUERTAS
				IF ACTIV THEN VAV = DEMANDA , CM_BL = 1 ELSE VAV = 0 , CM_BL = 0

```

### ASIGNACIÓN DE CONTROL DE COMPUERTAS A SALIDAS 

Asignación de de estados de apertura del control de compuerta `VAV` y control de compuerta de bloqueo `CM_BL` a puertos de salida del controlador.

```bash
			REM ***ASIGNACION DE PUNTOS DE CONTROL COMPUERTAS
				[AO] = VAV			: REM COMPUERTA DE VAV
				[BO] = CM_BL		: REM COMPUERTA DE BLOQUEO
```

## PARAMETROS POR CAJA

### PLENUM 1

- VAV-01

> `DEMANDA` = AV85
> `VAV` = AO1
> `CM_BL` = BO14

- VAV-02

### PLENUM 2

- VAV-01

- VAV-02

### PLENUM 4

- VAV-01

- VAV-02

### PLENUM 5

- VAV-01

- VAV-02

### PLENUM 6

- VAV-01

- VAV-02

### PLENUM 7R

- VAV-01

- VAV-02