El nombre del programa será: PRG2 - CONTROL DE COMPUERTAS DE VAVS
La versión del programa será: 1.5.0

Quiero que crees un programa que active y desactive el control de las compuertas de la VAV (compuerta VAV [`A`] y compuerta de bloqueo [`AB`]). El punto que determinará la activación del sistema es la Demanda de operación de la Compuerta [`DM`]. Para activar el sistema, el valor de demanda [`DM`] sea mayor al valor de la constante [`PORC_ACTIV`] y este tiene un valor de 5, para desactivar el sistema, el valor de demanda [`DM`] tiene que ser menor que 1. Cuando el sistema se activa, se conecta el valor de demanda [`DM`] al control de la compuerta [`A`] y la compuerta de bloqueo [`AB`] se manda abrir. En caso de que el sistema está inactivo, se envían los valores de las compuertas [`A`] y [`AB`] a 0.

Descripción de variables utilizadas:

* `DM` = Variable externa, de lectura, (UNIDADES = %)
* `A` = Variable externa, de escritura, (UNIDADES = %)
* `AB` = Variable externa, de escritura, (UNIDADES = ABIERTA / CERRADA)
* `PORC_ACTIV` = Constante, (VALOR = 5), (UNIDADES = %)

Son 15 VAV en las que se aplicará el mismo proceso, estas están distribuidas en 7 Plenums:

~~~VAVs
Plenu 1
    VAV Mediana (P1_VM)
    VAV Grande (P1_VG)
    VAV Chica (P1_VC)

Plenu 2
    VAV Mediana (P2_VM)
    VAV Grande (P2_VG)

Plenu 3
    VAV Grande (P3_VG)

Plenu 4
    VAV Mediana (P4_VM)
    VAV Grande (P4_VG)
    VAV Chica (P4_VC)

Plenu 5
    VAV Chica (P5_VC)
    VAV Grande (P5_VG)

Plenu 6
    VAV Grande (P1_VM)
    VAV Mediana (P1_VM)

Plenu 7R
    VAV Chica (P7R_VC)
    VAV Grande (P7R_VG)
~~~~~~

1. Primero establecer las Variables de Control del código en la sección de variables de control, vas a seguir esta estructura para cada VAV:

Ejemplo.
```basic
    REM PLENUM 1 - VAV MEDIANA
    LOCALS P1_VM_ACTIV, P1_VM_DM, P1_VM_A, P1_VM_AB
		REM P1_VM_ACTIV		Estado de activación del control de compuertas (VAV y Bloqueo)
		P1_VM_DM = AV85		: REM Control de demanda de apertura de la Compuerta VAV
		AO1 = P1_VM_A		: REM Control de apertura de Compuerta VAV
		BO1= P1_VM_AB		: REM Control de apertura de Compuerta Bloqueo
```

2. Establece en la misma sección de variables de control la Constante del sistema

Ejemplo.
```basic
    REM CONSTANTES: AJUSTES DE OPERACION
	LOCALS PORC_ACTIV
		PORC_ACTIV = 5		: REM Porcentaje de activación del control de compuertas
```

3. En la sección de lógica de control desarrolla la lógica de control para cada VAV

Ejemplo.
```basic
	REM *PLENUM 1

		REM **VAV MEDIANA 

			REM ***ACTIVACION DE CAJA
				IF P1_VM_DM > PORC_ACTIV THEN P1_VM_ACTIV = 1
				IF P1_VM_DM < 1 THEN P1_VM_ACTIV = 0

			REM ***CONEXION A CONTROL DE COMPUERTAS
				IF P1_VM_ACTIV THEN 
					P1_VM_A = P1_VM_DM
					P1_VM_AB = 1 
				 ELSE 
				 	P1_VM_A = 0
					P1_VM_AB = 0
                ENDIF
```