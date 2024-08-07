# PRG2 VAVS

Control de medición de caudales del sistema, a través de la señal medida por los transmisores de presión diferencial de las cajas Dwayer **MS-311**, rango de medición *0-2"WC* 

## VARIABLES GLOBALES

> `DP` ( **"WC** ) | Presión diferencial en caja VAV 
>
> `AREA` ( **pies2** ) | Area de paso de aire en caja VAV 
>
> `CV` | Factor de volumen de aire de caja VAV
>
> `CFM` ( **CFM** ) | Caudal de aire de caja VAV, con factor de calibración aplicado
>
> `CFM_R` ( **CFM** ) | Caudal de aire de caja VAV
>
> `MULT` | Multiplicador de factor de calibración
>
> `OFFSET` | Offset de factor de calibración

## MEDICION DE CAUDALES POR CAJA VAV

### ASIGNACIÓN DE VARIABLES LOCALES

Asignar variables de caja VAV a controlar

> `AREA` | Asignar el área de paso de flujo de aire de la *caja VAV*
>
> `CV` | Asignar el factor de flujo de aire de la *caja VAV*
>
> `DP` = [AI] | Asignar la entrada de medición de caida de presión de la *caja VAV*
>
> [AV] = `CFM_R` | Asignar variable para caudal de aire de la *caja VAV*
>
> `MULT` = [AV] | Asignar variable con multiplicador de calibración de la *caja VAV*
>
> `OFFSET` = [AV] | Asignar variable con offset de calibración de la *caja VAV*
>
> [AV] = `CFM` | Asignar variable para caudal de aire calibrado de la *caja VAV*

### ASIGNACION DE PARAMETROS DE CAJA VAV

Se asignan parametros de tamaño, factor de flujo y medición de sensor de *caja VAV*

```bash
			REM ***TAM = [00]
				AREA = [0.0] 	
				CV = [0]	
				DP = [AI]	
```

### CALCULO PARA MEDIR CFM A PARTIR DE PRESIÓN DINÁMICA

Se calcula por presión dinámica el caudal de aire de la caja y se asigna a la variable analógica para su lectura, solo permite valores positivos

```bash
			REM ***CONVERSION
				CFM_R = CV * ((DP)^0.5)	
				[AV] = MAX(0 ,CFM_R)
```

### AIGNACIÓN DE FACTORES DE CALIBRACIÓN PARA MEDICIÓN DE CUADAR DE AIRE 

A la medición de caudales inicial se le aplican los factores de calibración asignados a la *caja VAV*, solo permite valores positivos

```bash
			REM ***CALIBRACION
				MULT = [AV]
				OFFSET = [AV]
				CFM = (CFM_R * MULT) + OFFSET
				[AV] = MAX(0 ,CFM)	
```

### SEGMENTO COMPLETO

Código para cajas con ambas compuertas en el mismo controlador

```bash
			REM ***TAM = [00]
				AREA = [0.0]
				CV = [0]
				DP = [AI]
	
			REM ***CONVERSION
				CFM_R = CV * ((DP)^0.5)
				[AV] = MAX(0 ,CFM_R)
	
			REM ***CALIBRACION
				MULT = [AV]	
				OFFSET = [AV]
				CFM = (CFM_R * MULT) + OFFSET
				[AV] = MAX(0 ,CFM)
```

## PARAMETROS DE CAJAS

## PLENUM 1

#### VAV 03 - **CHICA** 

> Tamaño `4` ***pulgadas***
>
> Area `0.0819` ***pies2***
>
> CV `209`
>
> DP `AI7`.10022 ***"WC***
>
> CAUDAL `AV1`.10022 ***CFM***
>
> MULTIPLICADOR `AV2`.10022
>
> OFFSET `AV3`.10022
>
> CAUDAL Cal `AV4`.10022 ***CFM***

## PLENUM 3

> CAUDAL `AV9`.10022 ***CFM***

#### VAV 01 - **GRANDE**

> Tamaño `10` ***pulgadas***
>
> Area `0.5319 ` ***pies2***
>
> CV `1250`
>
> DP `AI8`.10022 ***"WC***
>
> CAUDAL `AV5`.10022 ***CFM***
>
> MULTIPLICADOR `AV6`.10022
>
> OFFSET `AV7`.10022
>
> CAUDAL Cal `AV8`.10022 ***CFM***