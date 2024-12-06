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
  
2. Variable de operación del sistema

    > `SS_CP` = **BV1**	( ***On/Off*** )	| Activación de sistema de control, cuarto de pruebas
    >
    > `L_MAX` = **100**             | Límite de operación máximo de algoritmos
    >
    > `L_MIN` = **6**               | Límite de operación mínimo de algoritmos

3. Variables de operación de algoritmos para control de demanda

    - **VAV GRANDE**

        > `PERM_VG` = **BV7**     | Permisivo para operación de VAV
        >
	    > `Q_VG` = **AV8**       | Caudal de aire de VAV
        >
	    > `SP_Q_VG` = **AV16**   | Setpoint de caudal de aire de VAV
        >
	    > `P_VG` = **AV23**       | Variable *Proporcional*
        >
	    > `I_VG` = **AV24**       | Variable *Integral*
        >
        > `ERR_VG`                | Error del sistema
        >
        > `PR_VG`                 | Resultante *Proporcional*
        >
        > `IR_VG`                 | Resultante *Integral*
        >
        > `IS_VG`                 | Resultante acumulativa *Integral
        >
        > **AV19** = `DM_VG`      | Demanda de enfriamiento

    - **VAV CHICA**

        > `PERM_VC` = **BV9**    | Permisivo para operación de VAV
        >
	    > `Q_VC` = **AV4**      | Caudal de aire de VAV
        >
	    > `SP_Q_VC` = **AV18**   | Setpoint de caudal de aire de VAV
        >
	    > `P_VC` = **AV27**       | Variable *Proporcional*
        >
	    > `I_VC` = **AV28**       | Variable *Integral*
        >
        > `ERR_VC`                | Error del sistema
        >
        > `PR_VC`                 | Resultante *Proporcional*
        >
        > `IR_VC`                 | Resultante *Integral*
        >
        > `IS_VC`                 | Resultante acumulativa *Integral
        >
        > **AV20** = `DM_VC`      | Demanda de enfriamiento

____________________

## OPERACIÓN DE PROGRAMA

Control PI para generación de demanda de flujo de caudal de aire, cada tipo de caja en operación cuenta con su propio algoritmo.

1. Validación de activación de algoritmo, si la variable de activación del sistema está activa `SS_CP` = **On**, y el permisivo de operación de la caja está activo `PERM_{VAV}`

    ```basic
    IF SS_CP = 1 AND PERM_{VAV} = 1 THEN
		
        REM ALGORITMO DE DEMANDA SE EJECUTA

	  ELSE

		PR_{VAV} = 0, IR_{VAV} = 0, IS_{VAV} = 0, DM_{VAV} = 0
		
    ENDIF
    ```

2. Se calcula el error de la variable en operación del sistema, para esto le resta al valor del caudal de la caja `Q_{VAV}`, el valor del setpoint `SP_Q_{VAV}`, el factor `-1` indica el sentido de control del algoritmo, si este es negativo, el control es inverso, si es positivo la dirección es normal

    ```Basic
    REM **ERROR DEL SISTEMA
        ERR_{VAV} = ( Q_{VAV} - SP_Q_{VAV} ) * -1
    ```

3. Se calcula la resultante de la *Proporción* `PR_{VAV}`

    ```basic
    REM **RESULTANTE PROPORCIONAL
        PR_{VAV} = ( ERR_{VAV} / ( SP_Q_{VAV} * P_{VAV} )) * 100
    ```

4. Se calcula la resultante acumulativa *Integral* `IS_{VAV}`

    ```basic
    REM **RESULTANTE INTEGRAL
        IR_{VAV} = (( 100 * ERR_{VAV} ) / SP_Q_{VAV} ) * I_{VAV}
	    IF T_{VAV} > 1 THEN IS_{VAV} = IS_{VAV} + IR_{VAV}, T_{VAV} = 0
	    IS_{VAV} = MAX( L_MIN - 10, MIN( L_MAX + 10, IS_{VAV} ))
    ```

5. Se asigna la demanda calculada del sistema `DM_{VAV}`

    ```basic
    REM **DEMANDA DE SISTEMA
        DM_{VAV} = PR_{VAV} + IS_{VAV}
	    DM_{VAV} = MAX( L_MIN , MIN( L_MAX, DM_{VAV} ))
    ```

Sistema con modulos integrados

```basic
IF SS_CP = 1 AND PERM_{VAV} = 1 THEN
		
    REM **ERROR DEL SISTEMA
        ERR_{VAV} = ( Q_{VAV} - SP_Q_{VAV} ) * -1

    REM **RESULTANTE PROPORCIONAL
        PR_{VAV} = ( ERR_{VAV} / ( SP_Q_{VAV} * P_{VAV} )) * 100

    REM **RESULTANTE INTEGRAL
        IR_{VAV} = (( 100 * ERR_{VAV} ) / SP_Q_{VAV} ) * I_{VAV}
	    IF T_{VAV} > 1 THEN IS_{VAV} = IS_{VAV} + IR_{VAV}, T_{VAV} = 0
	    IS_{VAV} = MAX( L_MIN - 10, MIN( L_MAX + 10, IS_{VAV} ))

    REM **DEMANDA DE SISTEMA
        DM_{VAV} = PR_{VAV} + IS_{VAV}
	    DM_{VAV} = MAX( L_MIN , MIN( L_MAX, DM_{VAV} ))

  ELSE

	PR_{VAV} = 0, IR_{VAV} = 0, IS_{VAV} = 0, DM_{VAV} = 0
		
ENDIF
```

Desactivación del sistema por permisivos inactivos

```basic
REM CAJAS VAV
	IF PERM_VG = 0 AND PERM_VM = 0 AND PERM_VC = 0 THEN BV9@8 = 1
```