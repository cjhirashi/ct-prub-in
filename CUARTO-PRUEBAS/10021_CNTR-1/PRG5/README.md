# PRG5 UMA - V2.0.0

Conexión con controles de operación de Unidad manejadora de aire 01

## DECLARACION DE VARIABLES DEL SISTEMA

1. VARIABLES: Parámetros de Cuarto de Pruebas (BAC_ID: 10021)

    > `SS_CP` = **BV1** | Activación de sistema de cuarto de pruebas
    > `ST_UMA` = **BV2**    | Estado de operación de UMA
    > `SP_TEMP` = **AV118** | Setpoint de temperatura de suministro
    > `SP_PRES` = **AV119** | Setpoint de presión de suministro

2. VARIABLES: Parámetros de UMA (BAC_ID: 10003)
    > `SS_UMA` = **MSV1**   | Arranque de UMA
    > `ST_UMA` = **BV3**    | Estado de operación de UMA
    > `SP_TEMP` = **AV4** | Setpoint de temperatura de suministro
    > `SP_PRES` = **AV8** | Setpoint de presión de suministro

## LOGICA DE CONTROL

### SINCRONIZACION DE VARIABLES DE CONTROL DE CUARTO DE PRUEBAS CON UMA-01

1. Escritura de parámetros de UMA en cuarto de pruebas, todas las variables se sincronizan cada 5 seg.

    > (CP) BV2 << ST_UMA << BV3 (UMA-1)
    > (CP) AV118 >> SP_TEMP >> AV4 (UMA-1)
    > (CP) AV119 >> SP_PRES >> AV8 (UMA-1)

2. Cuando la variable de activación del cuarto de pruebas se activa, la variable de arranque de la UMA-01 se va al estado de operación cuarto de pruebas y se mantiene bloqueda en ese estado, si la variable de activación del cuarto de pruebas es inactiva, el se libera el control de arranque de la UMA-01 en el ultimo estado que tenía antes del bloqueo de arranque.

```basic
    IF INTERVAL(00:00:05) THEN
		BV2 = 10003.BV3

		10003.AV4 = AV118

		10003.AV8 = AV119

		IF BV1 = 1 THEN
			10003.MSV1@7 = 4
		 ELSE
			RLQ 10003.MSV1@7
		ENDIF
	ENDIF
```

