# PRG3 PLENUMS

Asignación de variables de control a parametros de cajas de plenum activo

## DECLARACION DE VARIABLES DEL SISTEMA

1. CONSTANTES: Rango de operación de caudal por caja VAV ( ***Caudal máximo***, ***Caudal mínimo*** )

    - **PLENUM_1**
        > ***GRANDE***
        >
        > `P1_VG_QMAX` = **3000** [3200] 	( *CFM* )	| Caudal máximo
        >
        > `P1_VG_QMIN` = **1100** [500] 	( *CFM* )	| Caudal mínimo

        > ***MEDIANA***
        >
        > `P1_VM_QMAX` = **850** [1050] 	( *CFM* )	| Caudal máximo
        >
        > `P1_VM_QMIN` = **350** [175] 	    ( *CFM* )	| Caudal mínimo

        > ***CHICA***
        >
        > `P1_VC_QMAX` = **200** [250] 	    ( *CFM* )	| Caudal máximo
        >
        > `P1_VC_QMIN` = **75** [45] 	    ( *CFM* )	| Caudal mínimo

    - **PLENUM_2**
        > ***GRANDE***
        >
        > `P2_VG_QMAX` = **2000** [2350] 	( *CFM* )	| Caudal máximo
        >
        > `P2_VG_QMIN` = **850** [400] 	    ( *CFM* )	| Caudal mínimo

        > ***MEDIANA***
        >
        > `P2_VM_QMAX` = **650** [800] 	    ( *CFM* )	| Caudal máximo
        >
        > `P2_VM_QMIN` = **275** [140] 	    ( *CFM* )	| Caudal mínimo

    - **PLENUM_3**
        > ***GRANDE***
        >
        > `P3_VG_QMAX` = **1350** [1450] 	( *CFM* )	| Caudal máximo
        >
        > `P3_VG_QMIN` = **575** [290] 	    ( *CFM* )	| Caudal mínimo

    - **PLENUM_4**
        > ***GRANDE***
        >
        > `P4_VG_QMAX` = **3000** [3200] 	( *CFM* )	| Caudal máximo
        >
        > `P4_VG_QMIN` = **1100** [500] 	( *CFM* )	| Caudal mínimo

        > ***MEDIANA***
        >
        > `P4_VM_QMAX` = **850** [1050] 	( *CFM* )	| Caudal máximo
        >
        > `P4_VM_QMIN` = **350** [175] 	    ( *CFM* )	| Caudal mínimo

        > ***CHICA***
        >
        > `P4_VC_QMAX` = **200** [250] 	    ( *CFM* )	| Caudal máximo
        >
        > `P4_VC_QMIN` = **75** [45]	 	( *CFM* )	| Caudal mínimo

    - **PLENUM_5**
        > ***GRANDE***
        >
        > `P5_VG_QMAX` = **4000** [4200] 	( *CFM* )	| Caudal máximo
        >
        > `P5_VG_QMIN` = **1500** [700] 	( *CFM* )	| Caudal mínimo

        > ***CHICA***
        >
        > `P5_VC_QMAX` = **300** [400] 	    ( *CFM* )	| Caudal máximo
        >
        > `P5_VC_QMIN` = **125** [70]	 	( *CFM* )	| Caudal mínimo

    - **PLENUM_6**
        > ***GRANDE***
        >
        > `P6_VG_QMAX` = **3000** [3200] 	( *CFM* )	| Caudal máximo
        >
        > `P6_VG_QMIN` = **1100** [500] 	( *CFM* )	| Caudal mínimo

        > ***MEDIANA***
        >
        > `P6_VM_QMAX` = **850** [1050] 	( *CFM* )	| Caudal máximo
        >
        > `P6_VM_QMIN` = **350** [175] 	    ( *CFM* )	| Caudal mínimo

    - **PLENUM_7R**
        > ***GRANDE***
        >
        > `P7_VG_QMAX` = **3000** [3200] 	( *CFM* )	| Caudal máximo
        >
        > `P7_VG_QMIN` = **1100** [500] 	( *CFM* )	| Caudal mínimo

        > ***CHICA***
        >
        > `P7_VC_QMAX` = **200** [250] 	    ( *CFM* )	| Caudal máximo
        >
        > `P7_VC_QMIN` = **75** [45]	 	( *CFM* )	| Caudal mínimo

2. VARIABLES: Operación del sistema de control de caudales por Plenum

    > `PLENUM` = **MSV1**					| Selector de plenum en operación
    >
    > `SS_CP` = **BV1**		( *On/Off* )	| Activación de sistema de control, cuarto de pruebas 

3. VARIABLES: Demanda de cajas en plenum activo para operación

    - **CAJA GRANDE**

        > `Q_GR_DM` = **AV82**	( *%* )			| Demanda de caudal

    - **CAJA MEDIANA**

        > `Q_MD_DM` = **AV83**	( *%* )			| Demanda de caudal

    - **CAJA CHICA**

        > `Q_CH_DM` = **AV84** 	( *%* )			| Demanda de caudal

    - **CAJA GRANDE** ( RETORNO )

        > `QR_GR_DM` = **AV80**	( *%* )			| Demanda de caudal

    - **CAJA_CHICA** ( RETORNO )

        > `QR_CH_DM` = **AV81**	( *%* )			| Demanda de caudal

4. VARIABLES: Setpoint de caudales para cajas de plenum activo

    - **CAJA GRANDE**

        > `SP_Q_VG` = **AV107**	( *CFM* )		| Setpoint de caudal

    - **CAJA MEDIANA**

        > `SP_Q_VM` = **AV108**	( *CFM* )		| Setpoint de caudal

    - **CAJA CHICA**

        > `SP_Q_VC` = **AV109**	( *CFM* )		| Setpoint de caudal

    - **CAJA GRANDE** ( RETORNO )

        > `SP_Q_VGR` = **AV110**	( *CFM* )		| Setpoint de caudal

    - **CAJA CHICA** ( RETORNO )

        > `SP_Q_VCR` = **AV111**	( *CFM* )		| Setpoint de caudal

5. VARIABLES: Caudal de aire de cajas VAV

    - **PLENUM 1**

        > `P1_VM_Q` = **AV4**	( *CFM* )		| Caudal, VAV mediana 
        >
        > `P1_VG_Q` = **AV8**	( *CFM* )		| Caudal, VAV grande 
        >
        > `P1_VC_Q` = **AV62**	( *CFM* )	    | Caudal, VAV chica 

    - **PLENUM 2**

        > `P2_VM_Q` = **AV13**	( *CFM* )		| Caudal, VAV mediana 
        >
        > `P2_VG_Q` = **AV17**	( *CFM* )		| Caudal, VAV grande 

    - **PLENUM 3**

        > `P3_VG_Q` = **AV66**	( *CFM* )	    | Caudal, VAV grande 

    - **PLENUM 4**

        > `P4_VM_Q` = **AV22**	( *CFM* )		| Caudal, VAV mediana 
        >
        > `P4_VG_Q` = **AV26**	( *CFM* )		| Caudal, VAV grande 
        >
        > `P4_VC_Q` = **AV30**	( *CFM* )		| Caudal, VAV chica 

    - **PLENUM 5**

        > `P5_VC_Q` = **AV35**	( *CFM* )		| Caudal, VAV chica 
        >
        > `P5_VG_Q` = **AV39**	( *CFM* )		| Caudal, VAV grande 

    - **PLENUM 6**

        > `P6_VG_Q` = **AV44**	( *CFM* )		| Caudal, VAV grande 
        >
        > `P6_VM_Q` = **AV48**	( *CFM* )		| Caudal, VAV mediana 

    - **PLENUM 7** ( RETORNO )

        > `PR7_VC_Q` = **AV53**	( *CFM* )		| Caudal, VAV chica 
        >
        > `PR7_VG_Q` = **AV57**	( *CFM* )		| Caudal, VAV grande 

6. VARIABLES: Caida de presión de aire en plenums

    - **PLENUM 1**

        > `P1_DP_1` = **AI18** 	    ( *"WC"* )		| Presión diferencial 1
        >
        > `P1_DP_2`	= 10022.**AI3** ( *"WC"* )		| Presión diferencial 2 ( ***sicronización cada 5 seg*** ) 

    - **PLENUM 2**

        > `P2_DP` =	10022.**AI4** 	( *"WC"* )		| Presión diferencial ( ***sicronización cada 5 seg*** )

    - **PLENUM 4**

        > `P4_DP` = 10022.**AI5**   ( *"WC"* )	    | Presión diferencial ( ***sicronización cada 5 seg*** )

    - **PLENUM 5**

        > `P5_DP` = 10022.**AI6**   ( *"WC"* )	    | Presión diferencial ( ***sicronización cada 5 seg*** ) 

    - **PLENUM 6**

        > `P6_DP` = 10022.**AI7**   ( *"WC"* )	    | Presión diferencial ( ***sicronización cada 5 seg*** ) 

7. VARIABLES (DS): Caudal de aire de cajas activas

    > **AV98** = `Q_GR` ( *CFM* )           | Caudal de aire, VAV Grande Activa
    >
    > **AV99** = `Q_MD` ( *CFM* )           | Caudal de aire, VAV Mediana Activa
    >
    > **AV100** = `Q_CH` ( *CFM* )          | Caudal de aire, VAV Chica Activa
    >
    > **AV101** = `Q_GR + Q_MD + Q_CH`      | Caudal total, Plenum Activo

8. VARIABLES (DS): Control de compuertas de VAVs

    - **PLENUM 1**

        > **AV85** = `P1_VM_A` ( *%* )      | Compuerta, VAV Mediana
        >
        > **AV86** = `P1_VG_A` ( *%* )      | Compuerta, VAV Grande
        >
        > **AV67** = `P1_VC_A` ( *%* )      | Compuerta, VAV Chica

    - **PLENUM 2**

        > **AV87** = `P2_VM_A` ( *%* )      | Compuerta, VAV Mediana
        >
        > **AV88** = `P2_VG_A` ( *%* )      | Compuerta, VAV Grande

    - **PLENUM 3**

        > **AV68** = `P3_VG_A` ( *%* )      | Compuerta, VAV Grande

    - **PLENUM 4**

        > **AV89** = `P4_VM_A` ( *%* )      | Compuerta, VAV Mediana
        >  
        > **AV90** = `P4_VG_A` ( *%* )      | Compuerta, VAV Grande
        >
        > **AV91** = `P$_VC_A` ( *%* )      | Compuerta, VAV Chica

    - **PLENUM 5**

        > **AV92** = `P5_VC_A` ( *%* )      | Compuerta, VAV Chica
        >
        > **AV93** = `P5_VG_A` ( *%* )      | Compuerta, VAV Grande

    - **PLENUM 6**

        > **AV94** = `P6_VG_A` ( *%* )      | Compuerta, VAV Grande
        >
        > **AV95** = `P6_VM_A` ( *%* )      | Compuerta, VAV Mediana

    - **PLENUM R7**

        > **AV96** = `PR7_VC_A` ( *%* )      | Compuerta, VAV Chica
        >
        > **AV97** = `PR7_VG_A` ( *%* )      | Compuerta, VAV Grande

9. VARIABLES (DS): Estados de Plenums

    > **BV3** = `ST_P1`         | Estado de plenum 1
    >
    > **BV4** = `ST_P2`         | Estado de plenum 2
    >
    > **BV5** = `ST_P3`         | Estado de plenum 3
    >
    > **BV6** = `ST_P4`         | Estado de plenum 4
    >
    > **BV7** = `ST_P5`         | Estado de plenum 5
    >
    > **BV8** = `ST_P6`         | Estado de plenum 6

10. VARIABLES (DS): Caida de presión de plenum activo

    > **AV105** = `DP_1`        | Presión diferencial 1
    >
    > **AV106** = `DP_2`        | Presión diferencial 2

11. VARIABLES (DS): Rango de operación de caudal en VAVs activas

    - **VAV GRANDE**

        > **AV112** = `MIN_VG`      | Caudal mínimo
        >
        > **AV113** = `MAX_VG`      | Caudal máximo

    - **VAV MEDIANA**
        
        > **AV114** = `MIN_VM`      | Caudal mínimo
        >
        > **AV115** = `MAX_VM`      | Caudal máximo

    - **VAV CHICA**
        
        > **AV116** = `MIN_VC`      | Caudal mínimo
        >
        > **AV117** = `MAN_VC`      | Caudal máximo

<!-- ## SINCRONIZACION DE DATOS

1. Rangos máximo y mínimo de cajas de retorno, cotrol remoto Controlador 2 - cada 10 seg.

    - **VAV GRANDE**

        > 10022.**AV120** = `P7_VG_QMAX`      | Caudal máximo
        >
        > 10022.**AV121** = `P7_VG_QMIN`      | Caudal mínimo

    - **VAV CHICA**

        > 10022.**AV122** = `P7_VC_QMAX`      | Caudal máximo
        >
        > 10022.**AV123** = `P7_VC_QMIN`      | Caudal mínimo

2. Variables de operación para equipo, control remoto Controlador 2 - cada 10 seg.

    > 10022.**BV10** = **BV1**          | Activación, cuarto de pruebas
    >
    > 10022.**MSV1** = **MSV1**         | Plenum en operación
    >
    > 10022.**AV16** = **AV107**        | Setpoint, VAV Grande
    >
    > 10022.**AV17** = **AV108**        | Setpoint, VAV Mediana
    >
    > 10022.**AV18** = **AV109**        | Setpoint, VAV Chica
    >
    > 10022.**BV9** = **BV9**           | Permisivo, VAV Grande
    >
    > 10022.**BV10** = **BV10**         | Permisivo, VAV Mediana
    >
    > 10022.**BV11** = **BV11**         | Permisivo, VAV Chica -->

## LOGICA DE CONTROL

### ASIGNACION DE LIMITES A VARIABLES

1. Limita la asignación del setpoint dada por el usuario, para que el valor nunca quede fuera del rango de operación de la VAV

    - VAV GRANDE

    ```basic
    IF SP_Q_VG > MAX_VG THEN AV107@8 = MAX_VG
	IF SP_Q_VG < MIN_VG THEN AV107@8 = MIN_VG
    ```

    - VAV MEDIANA

    ```basic
    IF SP_Q_VM > MAX_VM THEN AV108@8 = MAX_VM
	IF SP_Q_VM < MIN_VM THEN AV108@8 = MIN_VM
    ```

    - VAV CHICA

    ```basic
    IF SP_Q_VC > MAX_VC THEN AV109@8 = MAX_VC
	IF SP_Q_VC < MIN_VC THEN AV109@8 = MIN_VC
    ```

    - VAV GRANDE ( RETORNO )

    ```basic
    IF SP_Q_VGR > P7_VG_QMAX THEN AV110 = P7_VG_QMAX
	IF SP_Q_VGR < P7_VG_QMIN THEN AV110 = P7_VG_QMIN
    ```

    - VAV CHICA ( RETORNO )

    ```basic
    IF SP_Q_VCR > P7_VC_QMAX THEN AV111 = P7_VC_QMAX
	IF SP_Q_VCR < P7_VC_QMIN THEN AV111 = P7_VC_QMIN
    ```

2. Limita la asignación de opciones del plenum, rango de 1 a 6

    ```basic
    IF PLENUM < 1 THEN PLENUM = 1
	IF PLENUM > 6 THEN PLENUM = 6
    ```
____________________

### SISTEMA ACTIVO - ASIGNACION DE PARAMETROS DE CONTROL A PLENUM ACTIVO

El usuario debe seleccionar qué *Plenum* `PLENUM` requiere activar, esto conectará todas las variables de operación a las cajas del *Plenum* activado.

#### PRESION DE PLENUM

Se asigna la caida de presión correspondiente al plenum activo, el *Plenum 1* cuenta con dos sensores que miden la caida de presión del *Plenum*, el resto de los *Plenums* solo cuentan con un sensor de caida de presión.

*Plenum* con **2** sensores.
```basic
DP_1 = P{#}_DP_1
DP_2 = P{#}_DP_2
```

*Plenum* con **1** sensor.
```basic
DP_1 = P{#}_DP_1
DP_2 = 0
```

#### BLOQUEO DE PERMISIVO DE OPERACION

Se bloquean el permisivos de operación en el plenum activo si no se cuenta con un tamaño de caja

Si cuenta con todos los tamaños de caja
```basic
RLQ BV9@7
RLQ BV10@7
RLQ BV11@7
```

Si no cuenta con caja mediana
```basic
RLQ BV9@7
BV10@7 = 0
RLQ BV11@7
```

Si no cuenta con caja chica
```basic
RLQ BV9@7
RLQ BV10@7
BV11@7 = 0
```

#### LIMITE DE CAUDAL POR TAMAÑO DE CAJA

Se asignan los límites de operación de las cajas del plenum activo

Si cuenta con todos los tamaños de caja
```basic
MAX_VG = P{#}_VG_QMAX
MIN_VG = P{#}_VG_QMIN
MAX_VM = P{#}_VM_QMAX
MIN_VM = P{#}_VM_QMIN
MAX_VC = P{#}_VC_QMAX
MIN_VC = P{#}_VC_QMIN
```

Si no cuenta con caja mediana
```basic
MAX_VG = P{#}_VG_QMAX
MIN_VG = P{#}_VG_QMIN
MAX_VM = 0
MIN_VM = 0
MAX_VC = P{#}_VC_QMAX
MIN_VC = P{#}_VC_QMIN
```

Si no cuenta con caja chica
```basic
MAX_VG = P{#}_VG_QMAX
MIN_VG = P{#}_VG_QMIN
MAX_VM = P{#}_VM_QMAX
MIN_VM = P{#}_VM_QMIN
MAX_VC = 0
MIN_VC = 0
```

#### CAUDAL DE AIRE

Se conecta la medición de caudales de las cajas del plenum activo a las variables de control

Si cuenta con todos los tamaños de caja
```basic
Q_GR = P{#}_VG_Q
Q_MD = P{#}_VM_Q
Q_CH = P{#}_VC_Q
```

Si no cuenta con caja mediana
```basic
Q_GR = P{#}_VG_Q
Q_MD = 0
Q_CH = P{#}_VC_Q
```

Si no cuenta con caja chica
```basic
Q_GR = P{#}_VG_Q
Q_MD = P{#}_VM_Q
Q_CH = 0
```

#### DEMANDA DE AIRE

Se asigna el control de demanda de aire a las compuertas de las VAV del Plenum activo.

Ejemplo de asignación, Plenum 1 activo.
```basic
P1_VG_A = Q_GR_DM
P1_VM_A = Q_MD_DM
P1_VC_A = Q_CH_DM
P2_VG_A = 0
P2_VM_A = 0
P3_VG_A = 0
P4_VG_A = 0
P4_VM_A = 0
P4_VC_A = 0
P5_VG_A = 0
P5_VC_A = 0
P6_VG_A = 0
P6_VM_A = 0
```

En el caso de la cajas del Plenum de retorno, la asignación se hacer directa, ya que solo hay un Plenum de retorno.

```basic
PR7_VG_A = QR_GR_DM
PR7_VC_A = QR_CH_DM
```

#### ESTADO DE PLENUM ACTIVO

Se asigna el estado de los Plenums.

Ejemplo de estado, Plenum 1 activo.
```basic
ST_P1 = 1
ST_P2 = 0
ST_P3 = 0
ST_P4 = 0
ST_P5 = 0
ST_P6 = 0
```

### SISTEMA INACTIVO - RESTABLECIMIENTO DE PARAMETROS DE CONTROL

Si el sistema se encuentra inactivo `SS_CP` = ***Off***, todas las compuertas de las VAV tomarán un estado general

```basic
IF SS_CP = 0 THEN

	P1_VG_A = 100
	P1_VM_A = 100
	P1_VC_A = 100
	P2_VG_A = 100
	P2_VM_A = 100
	P3_VG_A = 100
	P4_VG_A = 100
	P4_VM_A = 100
	P4_VC_A = 100
	P5_VG_A = 100
	P5_VC_A = 100
	P6_VG_A = 100
	P6_VM_A = 100
	PR7_VG_A = 100
	PR7_VC_A = 100
	ST_P1 = 0
	ST_P2 = 0
	ST_P3 = 0
	ST_P4 = 0
	ST_P5 = 0
	ST_P6 = 0
	BV9@7 = 0
	BV10@7 = 0
	BV11@7 = 0
		
ENDIF
```