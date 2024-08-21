# PRG3 PLENUMS

Gestor del control de demanda de VAVs, se utiliza un algoritmo PI para calcular esta demanda

## VARIABLES GLOBALES

1. Variables de tiempo para ejecución de algoritmos de control de demanda

    > `SCANS`               | Variable interna de sistema, indica el número de veces que el programa se ejecuta por segundo
    >
    > `TM` = **1 / SCANS**      | Segundos
    >
    > `T_VG` = `T_VG + TM`      | Contador de tiempo de ejecución de algoritmo
    >
    > `T_VM` = `T_VM + TM`      | Contador de tiempo de ejecución de algoritmo
    >
    > `T_VC` = `T_VC + TM`      | Contador de tiempo de ejecución de algoritmo
    >
    > `T_VGR` = `T_VGR + TM`      | Contador de tiempo de ejecución de algoritmo
    >
    > `T_VCR` = `T_VCM + TM`      | Contador de tiempo de ejecución de algoritmo

2. Variable de operación del sistema

    > `SS_CP` = **BV1**	( ***On/Off*** )	| Activación de sistema de control, cuarto de pruebas
    >
    > `L_MAX` = **100**             | Límite de operación máximo de algoritmos
    >
    > `L_MIN` = **6**               | Límite de operación mínimo de algoritmos

3. Variables de operación de algoritmos para control de demanda

    - **VAV GRANDE**

        > `PERM_VG` = **BV9**     | Permisivo para operación de VAV
        >
	    > `Q_VG` = **AV98**       | Caudal de aire de VAV
        >
	    > `SP_Q_VG` = **AV107**   | Setpoint de caudal de aire de VAV
        >
	    > `P_VG` = **AV69**       | Variable *Proporcional*
        >
	    > `I_VG` = **AV70**       | Variable *Integral*
        >
        > `ERR_VG`                | Error del sistema
        >
        > `PR_VG`                 | Resultante *Proporcional*
        >
        > `IR_VG`                 | Resultante *Integral*
        >
        > `IS_VG`                 | Resultante acumulativa *Integral
        >
        > **AV82** = `DM_VG`      | Demanda de enfriamiento

    - **VAV MEDIANA**

        > `PERM_VM` = **BV10**    | Permisivo para operación de VAV
        >
	    > `Q_VM` = **AV99**       | Caudal de aire de VAV
        >
	    > `SP_Q_VM` = **AV108**   | Setpoint de caudal de aire de VAV
        >
	    > `P_VM` = **AV71**       | Variable *Proporcional*
        >
	    > `I_VM` = **AV72**       | Variable *Integral*
        >
        > `ERR_VM`                | Error del sistema
        >
        > `PR_VM`                 | Resultante *Proporcional*
        >
        > `IR_VM`                 | Resultante *Integral*
        >
        > `IS_VM`                 | Resultante acumulativa *Integral
        >
        > **AV83** = `DM_VM`      | Demanda de enfriamiento

    - **VAV CHICA**

        > `PERM_VC` = **BV11**    | Permisivo para operación de VAV
        >
	    > `Q_VC` = **AV100**      | Caudal de aire de VAV
        >
	    > `SP_Q_VC` = **AV109**   | Setpoint de caudal de aire de VAV
        >
	    > `P_VC` = **AV73**       | Variable *Proporcional*
        >
	    > `I_VC` = **AV74**       | Variable *Integral*
        >
        > `ERR_VC`                | Error del sistema
        >
        > `PR_VC`                 | Resultante *Proporcional*
        >
        > `IR_VC`                 | Resultante *Integral*
        >
        > `IS_VC`                 | Resultante acumulativa *Integral
        >
        > **AV84** = `DM_VC`      | Demanda de enfriamiento

    - **VAV GRANDE** ( RETORNO )

        > `PERM_VGR` = **BV35**   | Permisivo para operación de VAV
        >
	    > `Q_VGR` = **AV102**     | Caudal de aire de VAV
        >
	    > `SP_Q_VGR` = **AV110**  | Setpoint de caudal de aire de VAV
        >
	    > `P_VGR` = **AV69**      | Variable *Proporcional*
        >
	    > `I_VGR` = **AV70**      | Variable *Integral*
        >
        > `ERR_VGR`               | Error del sistema
        >
        > `PR_VGR`                | Resultante *Proporcional*
        >
        > `IR_VGR`                | Resultante *Integral*
        >
        > `IS_VGR`                | Resultante acumulativa *Integral
        >
        > **AV80** = `DM_VGR`     | Demanda de enfriamiento

    - **VAV CHICA** ( RETORNO )

        > `PERM_VCR` = **BV36**   | Permisivo para operación de VAV
        >
	    > `Q_VCR` = **AV103**     | Caudal de aire de VAV
        >
	    > `SP_Q_VCR` = **AV111**  | Setpoint de caudal de aire de VAV
        >
	    > `P_VCR` = **AV73**      | Variable *Proporcional*
        >
	    > `I_VCR` = **AV74**      | Variable *Integral*
        >
        > `ERR_VCR`               | Error del sistema
        >
        > `PR_VCR`                | Resultante *Proporcional*
        >
        > `IR_VCR`                | Resultante *Integral*
        >
        > `IS_VCR`                | Resultante acumulativa *Integral
        >
        > **AV81** = `DM_VCR`     | Demanda de enfriamiento
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