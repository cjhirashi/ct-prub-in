# PRG2 VAVS

Control de apertura de compuerta de VAV por demanda de control de suministro de aire por *CFMs* y control de apertura de compuerta de bloqueo de aire.

## VARIABLES GLOBALES

> `P1_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo
>
> `P1_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo
>
> `P1_VM_QMAX` = 1050 	( ***CFM*** )	| Caudal máximo
>
> `P1_VM_QMIN` = 175 	( ***CFM*** )	| Caudal mínimo
>
> `P1_VC_QMAX` = 250 	( ***CFM*** )	| Caudal máximo
>
> `P1_VC_QMIN` = 45 	( ***CFM*** )	| Caudal mínimo

> `P2_VG_QMAX` = 2350 	( ***CFM*** )	| Caudal máximo
>
> `P2_VG_QMIN` = 400 	( ***CFM*** )	| Caudal mínimo
>
> `P2_VM_QMAX` = 800 	( ***CFM*** )	| Caudal máximo
>
> `P2_VM_QMIN` = 140 	( ***CFM*** )	| Caudal mínimo

> `P3_VG_QMAX` = 1450 	( ***CFM*** )	| Caudal máximo
>
> `P3_VG_QMIN` = 290 	( ***CFM*** )	| Caudal mínimo

> `P4_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo
>
> `P4_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo
>
> `P4_VM_QMAX` = 1050 	( ***CFM*** )	| Caudal máximo
>
> `P4_VM_QMIN` = 175 	( ***CFM*** )	| Caudal mínimo
>
> `P4_VC_QMAX` = 250 	( ***CFM*** )	| Caudal máximo
>
> `P4_VC_QMIN` = 45	 	( ***CFM*** )	| Caudal mínimo

> `P5_VG_QMAX` = 4200 	( ***CFM*** )	| Caudal máximo
>
> `P5_VG_QMIN` = 700 	( ***CFM*** )	| Caudal mínimo
>
> `P5_VC_QMAX` = 400 	( ***CFM*** )	| Caudal máximo
>
> `P5_VC_QMIN` = 70	 	( ***CFM*** )	| Caudal mínimo

> `P6_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo
>
> `P6_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo
>
> `P6_VM_QMAX` = 1050 	( ***CFM*** )	| Caudal máximo
>
> `P6_VM_QMIN` = 175 	( ***CFM*** )	| Caudal mínimo

> `P7_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo
>
> `P7_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo
>
> `P7_VC_QMAX` = 250 	( ***CFM*** )	| Caudal máximo
>
> `P7_VC_QMIN` = 45	 	( ***CFM*** )	| Caudal mínimo

=======================================================

> `PLENUM` = **MSV1**		: REM SELECTOR DE PLENUM EN OPERACION
>
> `SS_CP` = **BV1**			: REM ACTIVACION DE SISTEMA DE CONTROL CUARTO DE PRUEBAS
>
> `Q_GR_DM` = **AV82**		: REM DEMANDA, VAV GRANDE
>
> `Q_MD_DM` = **AV83**		: REM DEMANDA, VAV MEDIANA
>
> `Q_CH_DM` = **AV84** 		: REM DEMANDA, VAV CHICA
>
> `QR_GR_DM` = **AV80**		: REM DEMANDA, VAV GRANDE RETORNO
>
> `QR_CH_DM` = **AV81**		: REM DEMANDA, VAV CHICA RETORNO
>
> `SP_Q_VG` = **AV107**		: REM SETPOINT CAUDAL, CAJA GRANDE
>
> `SP_Q_VM` = **AV108**		: REM SETPOINT CAUDAL, CAJA MEDIANA
>
> `SP_Q_VC` = **AV109**		: REM SETPOINT CAUDAL, CAJA CHICA
>
> `P1_VM_Q` = **AV4**		: REM CAUDAL, PLENUM 1, VAV MEDIANA
>
> `P1_VG_Q` = **AV8**		: REM CAUDAL, PLENUM 1, VAV GRANDE
>
> `P1_VC_Q` = 10022.**AV4**		: REM CAUDAL, PLENUM 1, VAV CHICA
>
> `P2_VM_Q` = **AV13**		: REM CAUDAL, PLENUM 2, VAV MEDIANA
>
> `P2_VG_Q` = **AV17**		: REM CAUDAL, PLENUM 2, VAV GRANDE
>
> `P3_VG_Q` = 10022.**AV8**		: REM CAUDAL, PLENUM 3, VAV GRANDE
>
> `P4_VM_Q` = AV22		: REM CAUDAL, PLENUM 4, VAV MEDIANA
>
> `P4_VG_Q` = AV26		: REM CAUDAL, PLENUM 4, VAV GRANDE
>
> `P4_VC_Q` = AV30		: REM CAUDAL, PLENUM 4, VAV CHICA
>
> `P5_VC_Q` = AV35		: REM CAUDAL, PLENUM 5, VAV CHICA
>
> `P5_VG_Q` = AV39		: REM CAUDAL, PLENUM 5, VAV GRANDE
>
> `P6_VG_Q` = AV44		: REM CAUDAL, PLENUM 6, VAV GRANDE
>
> `P6_VM_Q` = AV48		: REM CAUDAL, PLENUM 6, VAV MEDIANA
>
> `PR7_VC_Q` = AV53		: REM CAUDAL, PLENUM R7, VAV CHICA
>
> `PR7_VG_Q` = AV57		: REM CAUDAL, PLENUM R7, VAV GRANDE
>
> `P1_DP_1` = AI16 		: REM PLENUM 1, PRESION DIFERENCIAL 1
>
> `P1_DP_2`	= AI17 		: REM PLENUM 1, PRESION DIFERENCIAL 2
>
> `P2_DP` =	AI18 		: REM PLENUM 2, PRESION DIFERENCIAL
>
> `P4_DP` = 10022.AI3 	: REM PLENUM 4, PRESION DIFERENCIAL
>
> `P5_DP` = 10022.AI4 	: REM PLENUM 5, PRESION DIFERENCIAL
>
> `P6_DP` = 10022.AI5	: REM PLENUM 6, PRESION DIFERENCIAL


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

```

### ASIGNACION DE DEMANDA A COMPUETAS POR ESTADO DE ACTIVACIÓN

Cuando el estado de `ACTIV` sea *On*, se asignará al control de compuerta `VAV` el valor de `DEMANDA` y a la compueta de bloqueo `CM_BL` el valor de *On*

Cuando el estado de `ACTIV` sea *Off*, se asignará al control de compuerta `VAV` el valor de 0% y a la compueta de bloqueo `CM_BL` el valor de *Off*

```bash

```

### ASIGNACIÓN DE CONTROL DE COMPUERTAS A SALIDAS 

Asignación de de estados de apertura del control de compuerta `VAV` y control de compuerta de bloqueo `CM_BL` a puertos de salida del controlador.

```bash

```

Código para cajas con control de compuerta de bloqueo desde equipo remoto

```bash

```

### SEGMENTO COMPLETO

Código para cajas con ambas compuertas en el mismo controlador

```bash

```

Código para cajas con control de compuerta de bloqueo desde equipo remoto

```bash

```

## PARAMETROS DE CAJAS

### PLENUM 1

#### VAV-01 - MEDIANA

> `DEMANDA` = ***AV85*** | `VAV` = ***AO1*** | `CM_BL` = ***BO14***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV86*** | `VAV` = ***AO2*** | `CM_BL` = ***BO15***

### PLENUM 2

#### VAV-01 - MEDIANA

> `DEMANDA` = ***AV87*** | `VAV` = ***AO3*** | `CM_BL` = ***BO16***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV88*** | `VAV` = ***AO4*** | `CM_BL` = ***10022.BO1***

### PLENUM 4

#### VAV-01 - MEDIANA

> `DEMANDA` = ***AV89*** | `VAV` = ***AO5*** | `CM_BL` = ***10022.BO2***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV90*** | `VAV` = ***AO6*** | `CM_BL` = ***10022.BO3***

#### VAV-03 - CHICA

> `DEMANDA` = ***AV91*** | `VAV` = ***AO7*** | `CM_BL` = ***10022.BO4***

### PLENUM 5

#### VAV-01 - CHICA

> `DEMANDA` = ***AV92*** | `VAV` = ***AO8*** | `CM_BL` = ***10022.BO5***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV93*** | `VAV` = ***AO9*** | `CM_BL` = ***10022.BO6***

### PLENUM 6

#### VAV-01 - GRANDE

> `DEMANDA` = ***AV94*** | `VAV` = ***AO10*** | `CM_BL` = ***10022.BO7***

#### VAV-02 - MEDIANA

> `DEMANDA` = ***AV95*** | `VAV` = ***AO11*** | `CM_BL` = ***10022.BO8***

### PLENUM 7R

#### VAV-01 - CHICA

> `DEMANDA` = ***AV96*** | `VAV` = ***AO12*** | `CM_BL` = ***10022.BO9***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV97*** | `VAV` = ***AO13*** | `CM_BL` = ***10022.BO10***