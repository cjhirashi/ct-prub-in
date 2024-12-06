# PRG3 PLENUMS

Control de caudal de aire por plenums, este programa asigna las variables para operación del plenum, a las cajas VAV del Plenum activo. Solo considera la operación de la ***VAV CHICA - PLENUM 1*** y ***VAV GRANDE - PLENUM 3***

## VARIABLES GLOBALES

1. Variables de operación del sistema de control de caudales por Plenum

    > `PLENUM` = **MSV1**						| Selector de plenum en operación
    >
    > `SS_CP` = **BV10**	( ***On/Off*** )	| Activación de sistema de control, cuarto de pruebas 

2. Variables de demanda de cajas en plenum activo para operación

    - **CAJA GRANDE**

        > `Q_GR_DM` = **AV19**	( ***%*** )			| Demanda de caudal

    - **CAJA CHICA**

        > `Q_CH_DM` = **AV20** 	( ***%*** )			| Demanda de caudal

3. Control de compuertas de VAVs

    - **PLENUM 1**

        > **AV14** = `P1_VC_A` ( ***%*** )            | Compuerta, VAV Chica

    - **PLENUM 3**

        > **AV15** = `P3_VG_A` ( ***%*** )            | Compuerta, VAV Grande

____________________

## OPERACIÓN DE PROGRAMA

El usuario deverá elegír qué plenum es el que deberá operar a través de la variable `PLENUM`, el sistema asignará todas las variables de operación del plenum elegido al sistema, esto considerando los siguientes grupos de parámetros

1. Demanda de aire

    ```basic
    DP_1 = P{#}_DP_1
	DP_2 = P{#}_DP_2
    ```

Si el sistema se encuentra inactivo `SS_CP` = ***Off***, todas las compuertas de las VAV tomarán un estado general

```basic
IF SS_CP = 0 THEN

	P1_VC_A = 100
	P3_VG_A = 100

ENDIF
```