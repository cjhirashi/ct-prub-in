# PRG2 VAVS

Control de apertura de compuerta de VAV por demanda de control de suministro de aire por *CFMs* y control de apertura de compuerta de bloqueo de aire.

## VARIABLES GLOBALES

Rangos de operación de caudal por caja VAV ( ***Caudal máximo***, ***Caudal mínimo*** )

> `P1_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo, Plenum 1, grande
>
> `P1_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo, Plenum 1, grande
>
> `P1_VM_QMAX` = 1050 	( ***CFM*** )	| Caudal máximo, Plenum 1, mediana
>
> `P1_VM_QMIN` = 175 	( ***CFM*** )	| Caudal mínimo, Plenum 1, mediana
>
> `P1_VC_QMAX` = 250 	( ***CFM*** )	| Caudal máximo, Plenum 1, chica
>
> `P1_VC_QMIN` = 45 	( ***CFM*** )	| Caudal mínimo, Plenum 1, chica

> `P2_VG_QMAX` = 2350 	( ***CFM*** )	| Caudal máximo, Plenum 2, grande
>
> `P2_VG_QMIN` = 400 	( ***CFM*** )	| Caudal mínimo, Plenum 2, grande
>
> `P2_VM_QMAX` = 800 	( ***CFM*** )	| Caudal máximo, Plenum 2, mediana
>
> `P2_VM_QMIN` = 140 	( ***CFM*** )	| Caudal mínimo, Plenum 2, mediana

> `P3_VG_QMAX` = 1450 	( ***CFM*** )	| Caudal máximo, Plenum 3, grande
>
> `P3_VG_QMIN` = 290 	( ***CFM*** )	| Caudal mínimo, Plenum 3, grande

> `P4_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo, Plenum 4, grande
>
> `P4_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo, Plenum 4, grande
>
> `P4_VM_QMAX` = 1050 	( ***CFM*** )	| Caudal máximo, Plenum 4, mediana
>
> `P4_VM_QMIN` = 175 	( ***CFM*** )	| Caudal mínimo, Plenum 4, mediana
>
> `P4_VC_QMAX` = 250 	( ***CFM*** )	| Caudal máximo, Plenum 4, chica
>
> `P4_VC_QMIN` = 45	 	( ***CFM*** )	| Caudal mínimo, Plenum 4, chica

> `P5_VG_QMAX` = 4200 	( ***CFM*** )	| Caudal máximo, Plenum 5, grande
>
> `P5_VG_QMIN` = 700 	( ***CFM*** )	| Caudal mínimo, Plenum 5, grande
>
> `P5_VC_QMAX` = 400 	( ***CFM*** )	| Caudal máximo, Plenum 5, chica
>
> `P5_VC_QMIN` = 70	 	( ***CFM*** )	| Caudal mínimo, Plenum 5, chica

> `P6_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo, Plenum 6, grande
>
> `P6_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo, Plenum 6, grande
>
> `P6_VM_QMAX` = 1050 	( ***CFM*** )	| Caudal máximo, Plenum 6, mediana
>
> `P6_VM_QMIN` = 175 	( ***CFM*** )	| Caudal mínimo, Plenum 6, mediana

> `P7_VG_QMAX` = 3200 	( ***CFM*** )	| Caudal máximo, Plenum 7, grande
>
> `P7_VG_QMIN` = 500 	( ***CFM*** )	| Caudal mínimo, Plenum 7, grande
>
> `P7_VC_QMAX` = 250 	( ***CFM*** )	| Caudal máximo, Plenum 7, chica
>
> `P7_VC_QMIN` = 45	 	( ***CFM*** )	| Caudal mínimo, Plenum 7, chica

=======================================================

> `PLENUM` = **MSV1**						| Selector de plenum en operación
>
> `SS_CP` = **BV1**		( ***On/Off*** )	| Activación de sistema de control, cuarto de pruebas 

> `Q_GR_DM` = **AV82**	( ***%*** )			| Demanda de caudal, VAV grande 
>
> `Q_MD_DM` = **AV83**	( ***%*** )			| Demanda de caudal, VAV mediana 
>
> `Q_CH_DM` = **AV84** 	( ***%*** )			| Demanda de caudal, VAV chica 
>
> `QR_GR_DM` = **AV80**	( ***%*** )			| Demanda de caudal, VAV grande (retorno) 
>
> `QR_CH_DM` = **AV81**	( ***%*** )			| Demanda de caudal, VAV chica (retorno) 

> `SP_Q_VG` = **AV107**	( ***CFM*** )		| Setpoint de caudal, caja grande 
>
> `SP_Q_VM` = **AV108**	( ***CFM*** )		| Setpoint de caudal, caja mediana 
>
> `SP_Q_VC` = **AV109**	( ***CFM*** )		| Setpoint de caudal, caja chica 
>
> `SP_Q_VGR` = **AV10**	( ***CFM*** )		| Setpoint de caudal, caja grande (retorno)
>
> `SP_Q_VCR` = **AV11**	( ***CFM*** )		| Setpoint de caudal, caja chica (retorno)

> `P1_VM_Q` = **AV4**	( ***CFM*** )		| Caudal de Plenum 1, VAV mediana 
>
> `P1_VG_Q` = **AV8**	( ***CFM*** )		| Caudal de Plenum 1, VAV grande 
>
> `P1_VC_Q` = 10022.**AV4**	( ***CFM*** )	| Caudal de Plenum 1, VAV chica ( ***sicronización cada 5 seg y plenum 1 activo*** ) 

> `P2_VM_Q` = **AV13**	( ***CFM*** )		| Caudal de Plenum 2, VAV mediana 
>
> `P2_VG_Q` = **AV17**	( ***CFM*** )		| Caudal de Plenum 2, VAV grande 
>
> `P3_VG_Q` = 10022.**AV8**	( ***CFM*** )	| Caudal de Plenum 3, VAV grande ( ***sicronización cada 5 seg y plenum 3 activo*** )
>
> `P4_VM_Q` = **AV22**	( ***CFM*** )		| Caudal de Plenum 4, VAV mediana 
>
> `P4_VG_Q` = **AV26**	( ***CFM*** )		| Caudal de Plenum 4, VAV grande 
>
> `P4_VC_Q` = **AV30**	( ***CFM*** )		| Caudal de Plenum 4, VAV chica 
>
> `P5_VC_Q` = **AV35**	( ***CFM*** )		| Caudal de Plenum 5, VAV chica 
>
> `P5_VG_Q` = **AV39**	( ***CFM*** )		| Caudal de Plenum 5, VAV grande 
>
> `P6_VG_Q` = **AV44**	( ***CFM*** )		| Caudal de Plenum 6, VAV grande 
>
> `P6_VM_Q` = **AV48**	( ***CFM*** )		| Caudal de Plenum 6, VAV mediana 
>
> `PR7_VC_Q` = **AV53**	( ***CFM*** )		| Caudal de Plenum R7, VAV chica 
>
> `PR7_VG_Q` = **AV57**	( ***CFM*** )		| Caudal de Plenum R7, VAV grande 
>
> `P1_DP_1` = **AI16** 	( ***"WC"*** )		| Presión diferencial 1, Plenum 1 
>
> `P1_DP_2`	= **AI17** 	( ***"WC"*** )		| Presión diferencial 2, Plenum 1 
>
> `P2_DP` =	**AI18** 	( ***"WC"*** )		| Presión diferencial, Plenum 2 
>
> `P4_DP` = 10022.**AI3** ( ***"WC"*** )	| Presión diferencial, Plenum 4 ( ***sicronización cada 5 seg*** )
>
> `P5_DP` = 10022.**AI4** ( ***"WC"*** )	| Presión diferencial, Plenum 5 ( ***sicronización cada 5 seg*** ) 
>
> `P6_DP` = 10022.**AI5** ( ***"WC"*** )	| Presión diferencial, Plenum 6 ( ***sicronización cada 5 seg*** ) 


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