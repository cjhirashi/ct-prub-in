# PRG2 VAVS

Control de apertura de compuerta de VAV por demanda de control de suministro de aire por *CFMs* y control de apertura de compuerta de bloqueo de aire.

## VARIABLES GLOBALES

> `P_APER` =  5 (%) | Porcentaje para activación de control de compuertas.

> `SINC` = 10 (seg.) | Tiempo de sincronización de datos

> `DEMANDA` (%) | Demanda de enfriamiento para apertura de compuerta por porcentaje

> `VAV` (%) | Porcentaje de apertura de compuerta

> `CM_BL` (On/Off) | Comando de apertura de compuerta de bloqueo

> `ACTIV` (On/Off) | Señal de activación de sistema de control de compuertas

## MEDICION POR CAJA VAV

### ASIGNACIÓN DE VARIABLES LOCALES

Asignar variables de caja VAV a controlar

> `DEMANDA` = [AV]
>
> [AO] = `VAV`
>
> [BO] = `CM_BL`

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
				[AO] = VAV
				[BO] = CM_BL
```

Código para cajas con control de compuerta de bloqueo desde equipo remoto

```bash
			REM ***ASIGNACION DE PUNTOS DE CONTROL COMPUERTAS
				[AO] = VAV
				IF INTERVAL(SINC) THEN
					[10022.BO] = CM_BL
				ENDIF
```

### SEGMENTO COMPLETO

Código para cajas con ambas compuertas en el mismo controlador

```bash
		REM **VAV 00 - TAMANO
			DEMANDA = [AV]

			REM ***ACTIVACION DE CAJA
				IF DEMANDA > P_APER THEN ACTIV = 1
				IF DEMANDA < 1 THEN ACTIV = 0

			REM ***CONTROL DE COMPUERTAS
				IF ACTIV THEN VAV = DEMANDA , CM_BL = 1 ELSE VAV = 0 , CM_BL = 0

			REM ***ASIGNACION DE PUNTOS DE CONTROL COMPUERTAS
				[AO] = VAV
				[BO] = CM_BL
```

Código para cajas con control de compuerta de bloqueo desde equipo remoto

```bash
		REM **VAV 00 - TAMANO
			DEMANDA = [AV]

			REM ***ACTIVACION DE CAJA
				IF DEMANDA > P_APER THEN ACTIV = 1
				IF DEMANDA < 1 THEN ACTIV = 0

			REM ***CONTROL DE COMPUERTAS
				IF ACTIV THEN VAV = DEMANDA , CM_BL = 1 ELSE VAV = 0 , CM_BL = 0

			REM ***ASIGNACION DE PUNTOS DE CONTROL COMPUERTAS
				[AO] = VAV
				IF INTERVAL(SINC) THEN
					[10022.BO] = CM_BL
				ENDIF
```

## PARAMETROS POR CAJA

### PLENUM 1

#### VAV-01

> `DEMANDA` = AV85 | `VAV` = AO1 | `CM_BL` = BO14

#### VAV-02

> `DEMANDA` = AV86 | `VAV` = AO2 | `CM_BL` = BO15

### PLENUM 2

#### VAV-01

> `DEMANDA` = AV87 | `VAV` = AO3 | `CM_BL` = BO16

#### VAV-02

> `DEMANDA` = AV88 | `VAV` = AO4 | `CM_BL` = 10022.BO1

### PLENUM 4

#### VAV-01

> `DEMANDA` = AV89 | `VAV` = AO5 | `CM_BL` = 10022.BO2

#### VAV-02

> `DEMANDA` = AV90 | `VAV` = AO6 | `CM_BL` = 10022.BO3

#### VAV-03

> `DEMANDA` = AV91 | `VAV` = AO7 | `CM_BL` = 10022.BO4

### PLENUM 5

#### VAV-01

> `DEMANDA` = AV92 | `VAV` = AO8 | `CM_BL` = 10022.BO5

#### VAV-02

> `DEMANDA` = AV93 | `VAV` = AO9 | `CM_BL` = 10022.BO6

### PLENUM 6

#### VAV-01

> `DEMANDA` = AV94 | `VAV` = AO10 | `CM_BL` = 10022.BO7

#### VAV-02

> `DEMANDA` = AV95 | `VAV` = AO11 | `CM_BL` = 10022.BO8

### PLENUM 7R

#### VAV-01

> `DEMANDA` = AV96 | `VAV` = AO12 | `CM_BL` = 10022.BO9

#### VAV-02

> `DEMANDA` = AV97 | `VAV` = AO13 | `CM_BL` = 10022.BO10