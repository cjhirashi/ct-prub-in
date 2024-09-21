# PRG2 VAVS

Control de apertura de compuertas de VAV y bloqueo de aire, por demanda de flujo de aire

## VARIABLES DEL SISTEMA

### PLENUM 1

#### VAV-01 - MEDIANA

> `DEMANDA` = **AV85** (*%*) | Demanda de flujo de aire
>
> **AO1** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> **BO14** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-02 - GRANDE

> `DEMANDA` = **AV86** (*%*) | Demanda de flujo de aire
>
> **AO2** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> **BO15** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-03 - CHICA

> `DEMANDA` = **AV67** (*%*) | Demanda de flujo de aire
>
> **AO21** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> **BO22** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

### PLENUM 2

#### VAV-01 - MEDIANA

> `DEMANDA` = **AV87** (*%*) | Demanda de flujo de aire
>
> **AO3** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> **BO16** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-02 - GRANDE

> `DEMANDA` = **AV88** (*%*) | Demanda de flujo de aire
>
> **AO4** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO1** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

### PLENUM 3

#### vav-01 - GRANDE

> `DEMANDA` = **AV68** (*%*) | Demanda de flujo de aire
>
> **AO23** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> **BO24** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

### PLENUM 4

#### VAV-01 - MEDIANA

> `DEMANDA` = **AV89** (*%*) | Demanda de flujo de aire
>
> **AO5** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO2** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-02 - GRANDE

> `DEMANDA` = **AV90** (*%*) | Demanda de flujo de aire
>
> **AO6** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO3** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-03 - CHICA

> `DEMANDA` = **AV91** (*%*) | Demanda de flujo de aire
>
> **AO7** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO4** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

### PLENUM 5

#### VAV-01 - CHICA

> `DEMANDA` = **AV92** (*%*) | Demanda de flujo de aire
>
> **AO8** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO5** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-02 - GRANDE

> `DEMANDA` = **AV93** (*%*) | Demanda de flujo de aire
>
> **AO9** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO6** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

### PLENUM 6

#### VAV-01 - GRANDE

> `DEMANDA` = **AV94** (*%*) | Demanda de flujo de aire
>
> **AO10** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO7** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-02 - MEDIANA

> `DEMANDA` = **AV95** (*%*) | Demanda de flujo de aire
>
> **AO11** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> 10022.**BO8** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

### PLENUM 7R

#### VAV-01 - CHICA

> `DEMANDA` = **AV96** (*%*) | Demanda de flujo de aire
>
> **AO12** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> **BO17** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

#### VAV-02 - GRANDE

> `DEMANDA` = **AV97** (*%*) | Demanda de flujo de aire
>
> **AO13** = `VAV` (*%*) | Porcentaje de apertura de compuerta
>
> **BO18** = `CM_BL` (*On/Off*) | Compuerta de bloqueo

## VARIABLES GLOBALES

> `P_APER` =  5 (*%*) | Porcentaje para activación de control de compuertas.
>
> `ACTIV` (*On/Off*) | Activación control de compuertas
>
> `SINC` = 10 (*seg*) | Tiempo de sincronización de datos

## LOGICA DE CONTROL

### ASIGNACIÓN DE VARIABLE DE DEMANDA

```basic
		DEMANDA = [AV]
```

### ACTIVACION DE CAJA

***ACTIVACION*** El control de la compuerta se activa cuando la `DEMANDA` de la compuerta sea mayor al porcentaje establecido en la variable `P_APER`.

***DESACTIVACION*** El control de la compuerta se desactiva cuando la `DEMANDA` sea menor que 1%.

```basic
			REM ***ACTIVACION DE CAJA
				IF DEMANDA > P_APER THEN ACTIV = 1
				IF DEMANDA < 1 THEN ACTIV = 0
```

### ASIGNACION DE DEMANDA A COMPUETAS POR ESTADO DE ACTIVACIÓN

Cuando el estado de `ACTIV` sea *On*, se asignará al valor de `DEMANDA` a la variable de control de la compuerta `VAV` y se abrirá la compuerta de bloqueo `CM_BL`.

Cuando el estado de `ACTIV` sea *Off*, se mandará a `0` *%* el control de la compuerta `VAV` y se cerrará la copuerta de bloqueo `CM_BL`.

```basic
			REM ***CONTROL DE COMPUERTAS
				IF ACTIV THEN VAV = DEMANDA , CM_BL = 1 ELSE VAV = 0 , CM_BL = 0

```

### ASIGNACIÓN DE CONTROL DE COMPUERTAS A SALIDAS 

Asignación de estados de apertura del control de compuerta `VAV` y control de compuerta de bloqueo `CM_BL` a variables de salida del controlador.

1. Compuerta de bloqueo local

	```basic
			REM ***ASIGNACION DE PUNTOS DE CONTROL COMPUERTAS
				[AO] = VAV
				[BO] = CM_BL
	```

2. Compuerta de bloqueo remota

```basic
			REM ***ASIGNACION DE PUNTOS DE CONTROL COMPUERTAS
				[AO] = VAV
				IF INTERVAL(SINC) THEN
					[00000.BO] = CM_BL
				ENDIF
```

### SEGMENTO COMPLETO

Código para cajas con ambas compuertas en el mismo controlador

```basic
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

```basic
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
					[00000.BO] = CM_BL
				ENDIF
```
