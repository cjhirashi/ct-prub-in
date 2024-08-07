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

> CAUDAL `AV9`.10021 ***CFM***

#### VAV 01 - **MEDIANA** 

> Tamaño `8` ***pulgadas***
>
> Area `0.3382` ***pies2***
>
> CV `817`
>
> DP `AI3`.10021 ***"WC***
>
> CAUDAL `AV1`.10021 ***CFM***
>
> MULTIPLICADOR `AV2`.10021
>
> OFFSET `AV3`.10021
>
> CAUDAL Cal `AV4`.10021 ***CFM***

#### VAV 02 - **GRANDE** 

> Tamaño `14` ***pulgadas***
>
> Area `1.05` ***pies2***
>
> CV `2474`
>
> DP `AI4`.10021 ***"WC***
>
> CAUDAL `AV5`.10021 ***CFM***
>
> MULTIPLICADOR `AV6`.10021
>
> OFFSET `AV7`.10021
>
> CAUDAL Cal `AV8`.10021 ***CFM***

## PLENUM 2

> CAUDAL `AV18`.10021 ***CFM***

#### VAV 01 - **MEDIANA** 

> Tamaño `7` ***pulgadas***
>
> Area `0.2578` ***pies2***
>
> CV `612`
>
> DP `AI5`.10021 ***"WC***
>
> CAUDAL `AV10`.10021 ***CFM***
>
> MULTIPLICADOR `AV11`.10021
>
> OFFSET `AV12`.10021
>
> CAUDAL Cal `AV13`.10021 ***CFM***

#### VAV 02 - **GRANDE** 

> Tamaño `12` ***pulgadas***
>
> Area `0.7691` ***pies2***
>
> CV `1792`
>
> DP `AI6`.10021 ***"WC***
>
> CAUDAL `AV14`.10021 ***CFM***
>
> MULTIPLICADOR `AV15`.10021
>
> OFFSET `AV16`.10021
>
> CAUDAL Cal `AV17`.10021 ***CFM***

## PLENUM 4

> CAUDAL `AV31`.10021 ***CFM***

#### VAV 01 - **MEDIANA** 

> Tamaño `8` ***pulgadas***
>
> Area `0.3382` ***pies2***
>
> CV `817`
>
> DP `AI7`.10021 ***"WC***
>
> CAUDAL `AV19`.10021 ***CFM***
>
> MULTIPLICADOR `AV20`.10021
>
> OFFSET `AV21`.10021
>
> CAUDAL Cal `AV22`.10021 ***CFM***

#### VAV 02 - **GRANDE** 

> Tamaño `14` ***pulgadas***
>
> Area `1.05` ***pies2***
>
> CV `2474`
>
> DP `AI8`.10021 ***"WC***
>
> CAUDAL `AV23`.10021 ***CFM***
>
> MULTIPLICADOR `AV24`.10021
>
> OFFSET `AV25`.10021
>
> CAUDAL Cal `AV26`.10021 ***CFM***

#### VAV 03 - **CHICA** 

> Tamaño `4` ***pulgadas***
>
> Area `0.0819` ***pies2***
>
> CV `209`
>
> DP `AI9`.10021 ***"WC***
>
> CAUDAL `AV27`.10021 ***CFM***
>
> MULTIPLICADOR `AV28`.10021
>
> OFFSET `AV29`.10021
>
> CAUDAL Cal `AV30`.10021 ***CFM***

## PLENUM 5

> CAUDAL `AV40`.10021 ***CFM***

#### VAV 01 - **CHICA** 

> Tamaño `5` ***pulgadas***
>
> Area `0.1296` ***pies2***
>
> CV `315`
>
> DP `AI10`.10021 ***"WC***
>
> CAUDAL `AV32`.10021 ***CFM***
>
> MULTIPLICADOR `AV33`.10021
>
> OFFSET `AV34`.10021
>
> CAUDAL Cal `AV35`.10021 ***CFM***

#### VAV 02 - **GRANDE** 

> Tamaño `16` ***pulgadas***
>
> Area `1.3745` ***pies2***
>
> CV `3235`
>
> DP `AI11`.10021 ***"WC***
>
> CAUDAL `AV36`.10021 ***CFM***
>
> MULTIPLICADOR `AV37`.10021
>
> OFFSET `AV38`.10021
>
> CAUDAL Cal `AV39`.10021 ***CFM***

## PLENUM 6

> CAUDAL `AV49`.10021 ***CFM***

#### VAV 01 - **GRANDE** 

> Tamaño `14` ***pulgadas***
>
> Area `1.05` ***pies2***
>
> CV `2474`
>
> DP `AI12`.10021 ***"WC***
>
> CAUDAL `AV41`.10021 ***CFM***
>
> MULTIPLICADOR `AV42`.10021
>
> OFFSET `AV43`.10021
>
> CAUDAL Cal `AV44`.10021 ***CFM***

#### VAV 02 - **MEDIANA** 

> Tamaño `8` ***pulgadas***
>
> Area `0.3382` ***pies2***
>
> CV `817`
>
> DP `AI13`.10021 ***"WC***
>
> CAUDAL `AV45`.10021 ***CFM***
>
> MULTIPLICADOR `AV46`.10021
>
> OFFSET `AV47`.10021
>
> CAUDAL Cal `AV48`.10021 ***CFM***

## PLENUM 7 RETORNO

> CAUDAL `AV58`.10021 ***CFM***

#### VAV 01 - **CHICA** 

> Tamaño `4` ***pulgadas***
>
> Area `0.0819` ***pies2***
>
> CV `209`
>
> DP `AI14`.10021 ***"WC***
>
> CAUDAL `AV50`.10021 ***CFM***
>
> MULTIPLICADOR `AV51`.10021
>
> OFFSET `AV52`.10021
>
> CAUDAL Cal `AV53`.10021 ***CFM***

#### VAV 02 - **GRANDE** 

> Tamaño `14` ***pulgadas***
>
> Area `1.05` ***pies2***
>
> CV `2474`
>
> DP `AI15`.10021 ***"WC***
>
> CAUDAL `AV54`.10021 ***CFM***
>
> MULTIPLICADOR `AV55`.10021
>
> OFFSET `AV56`.10021
>
> CAUDAL Cal `AV57`.10021 ***CFM***