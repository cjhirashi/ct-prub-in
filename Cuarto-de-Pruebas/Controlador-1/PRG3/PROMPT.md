# PROGRAMA

*   **NOMBRE**: MOD: CONTROL DE PLENUMS
*   **ID PROGRAMA**: PRG3
*   **DI CONTROLADOR**: 10021
*   **AUTOR**: Carlos Jiménez Hirashi *@cjhirashi*, Adaptación: Asistente de IA
*   **VERSION**: 1.5.0

## DESCRIPCION

Este módulo gestiona la selección del plenum activo, la activación/desactivación de las VAVs en función del plenum seleccionado, la limitación de los setpoints de caudal y la asignación de variables para el control de las VAVs y el monitoreo del sistema.

Los rangos de medición de caudales por caja son los siguientes:

### PLENUM 1

* **VAV GRANDE**

	* **MAX** = 3000 *cfm*
	* **MIN** = 1100 *cfm*

* **VAV MEDIANA**

	* **MAX** = 850 *cfm*
	* **MIN** = 350 *cfm*

* **VAV CHICA**

	* **MAX** = 200 *cfm*
	* **MIN** = 75 *cfm*

### PLENUM 2

* **VAV GRANDE**

	* **MAX** = 2000 *cfm*
	* **MIN** = 850  *cfm*

* **VAV MEDIANA**

    * **MAX** = 650 *cfm*
	* **MIN** = 275 *cfm*

### PLENUM 3

* **VAV GRANDE**

	* **MAX** = 1350 *cfm*
	* **MIN** = 575 *cfm*

### PLENUM 4

* **VAV GRANDE**

	* **MAX** = 3000 *cfm*
	* **MIN** = 1100 *cfm*

* **VAV MEDIANA**
	* **MAX** = 850 *cfm*
	* **MIN** = 350 *cfm*

* **VAV CHICA**

	* **MAX** = 200 *cfm*
	* **MIN** = 75 *cfm*
	
### PLENUM 5

* **VAV GRANDE**

	* **MAX** = 4000 *cfm*
	* **MIN** = 1500 *cfm*

* **VAV CHICA**

	* **MAX** = 300 *cfm*
	* **MIN** = 125 *cfm*

### PLENUM 6
		
* **VAV GRANDE**

	* **MAX** = 3000 *cfm*
	* **MIN** = 1100 *cfm*

* **VAV MEDIANA**

	* **MAX** = 850 *cfm*
	* **MIN** = 350 *cfm*

### PLENUM 7

* **VAV GRANDE**

	* **MAX** = 3000 *cfm*
	* **MIN** = 1100 *cfm*

* **VAV CHICA**

	* **MAX** = 200 *cfm*
	* **MIN** = 75 *cfm*


## VARIABLES DE CONTROL

**NOTA**: Todas las variables de control que contengan un prefijo `P[#]_V[T]_`, indican que son variables relacionadas al control de cada VAV, `P[#]` hace referencia al número de Plenum que pertenece, el factor `[#]` representa el número del Plenum que corresponde, `V[T]` hace referencia al tamaño de caja, el factor `[T]` representa el tamaño de caja y su valor puede ser `G` GRANDE, `M` MEDIANA o `C` CHICA, con estos parámetros podremos saber a qué caja VAV y qué Plenum pertenece.

### VARIABLES INTERNAS

#### CONSTANTES

*   **Rangos de Operación de Caudal (QMAX, QMIN):** Para cada VAV (ejemplo: `P1_VG_QMAX`, `P1_VG_QMIN`, etc.). *

### VARIABLES EXTERNAS

*   **Entradas:**
    *   `PLENUM` (MSV): Selector del plenum activo (0 = Ninguno, 1-6 = Plenum 1-6). (LEE)
    *   `SS_CP` Señal de activación del sistema. (LEE)

    *   `V[T]_Q-SP` Setpoint de caudal para VAV [TAMAÑO] activa. (LEE)
    *   `P[#]_V[T]_Q` Caudales VAV. (LEE)

    *   `P1_DP_1` Caida de presión 1 PLENUM 1. (LEE)
    *   `P1_DP_2` Caida de presión 2 PLENUM 1. (LEE)
    *   `P2_DP` Caida de presión PLENUM 2. (LEE)
    *   `P4_DP` Caida de presión PLENUM 4. (LEE)
    *   `P5_DP` Caida de presión PLENUM 5. (LEE)
    *   `P6_DP` Caida de presión PLENUM 6. (LEE)
    *   `V[T]_DEMANDA` Demanda de VAV [TAMAÑO] activa. (LEE)

*   **Salidas:**
    *   `ST_CP`Estado de operación general. (ESCRIBE)
    *   `ST_P1` - `ST_P6` Estado de operación de cada plenum (1-6). (ESCRIBE)

    *   `V[T]_Q` Caudal de VAV Grande Activa (ESCRIBE)
    *   `Q_T` Caudal Total Activo (ESCRIBE)
    *   `P[#]_V[T]_DEMANDA` Control de compuerta VAV (ESCRIBE)

    *   `DP_1` Caida de presión 1 de plenum activo (ESCRIBE)
    *   `DP_2` Caida de presión 2 de plenum activo (ESCRIBE)
    *   `VG_MIN` Caudal Mínimo de VAV Grande activa (ESCRIBE)
    *   `VG_MAX` Caudal Máximo de VAV Grande activa (ESCRIBE)
    *   `VM_MIN` Caudal Mínimo de VAV Mediana activa (ESCRIBE)
    *   `VM_MAX` Caudal Máximo de VAV Mediana activa (ESCRIBE)
    *   `VC_MIN` Caudal Mínimo de VAV Chica activa (ESCRIBE)
    *   `VC_MAX` Caudal Máximo de VAV Chica activa (ESCRIBE)

    *Nota: para los rangos de caudales Máximos y Mínimos de retorno, ocupar los valores de las cajas VAV del plenum 7R* (ejemplo: `PR7_VG_QMAX`, `PR7_VG_QMIN`, etc.)

## LOGICA DE OPERACION

Este módulo realiza las siguientes acciones:

1.  **Lectura de Entradas:** Lee el estado de las variables de entrada (PLENUM, SS_CP, setpoints, caudales, caídas de presión).

2.  **Limitación de Setpoints:** Limita los setpoints de caudal de las VAVs dentro de los rangos de operación definidos por las constantes QMAX y QMIN.

3.  **Selección de Plenum Activo:**
    *   Si el sistema está activo (`SS_CP = 1`) y se ha seleccionado un plenum válido (`PLENUM` entre 1 y 6):
        *   Se activa el plenum correspondiente.
        *   Se asignan las variables de caudal, demanda y control de compuertas correspondientes al plenum activo.
        *   Se establecen los límites de caudal (MAX, MIN) para las VAVs del plenum activo.
        *   Se desactivan los otros plenums.

4.  **Control de Plenum de Retorno (Plenum 7):**
    *   Si el sistema está activo (`SS_CP = 1`):
        *   Se asignan las demandas a las variables de control de las compuertas de las VAVs de retorno.

5.  **Sistema Inactivo:**
    *   Si el sistema está inactivo (`SS_CP = 0`):
        *   Se establecen las variables de control de las compuertas a 0 (cerrando todas las VAVs).
        *   Se establecen los estados de operación de los plenums a 0.

6.  **Estado de Operación General:**
    *   Se calcula el estado de operación general (`ST_CP`) como el máximo de los estados de los plenums.

7.  **Escritura de Salidas:** Se escriben los valores calculados en las variables de salida.

**Pseudocódigo (Simplificado):**

```basic
// Leer entradas
PLENUM = MSV1
SS_CP = BV1
... (leer todos los setpoints y caudales) ...
... (escribir todas las variables de entrada y salida) ...

    REM VARIABLES: CAIDA DE PRESION EN PLENUMS
		LOCALS P1_DP_1, P1_DP_2, P2_DP, P4_DP, P5_DP, P6_DP
	
		P1_DP_1 = AI18 	
		IF INTERVAL(00:00:05) THEN
			IF PLENUM = 1 THEN P1_DP_2 = 10022.AI3  	
			IF PLENUM = 2 THEN P2_DP = 10022.AI4
			IF PLENUM = 4 THEN P4_DP = 10022.AI5
			IF PLENUM = 5 THEN P5_DP = 10022.AI6
			IF PLENUM = 6 THEN P6_DP = 10022.AI7
		ENDIF

// Limitar setpoints de caudales
VG_Q-SP = MIN(MAX(VG_Q-SP, VG_MIN), VG_MAX)
VM_Q-SP = MIN(MAX(VM_Q-SP, VM_MIN), VM_MAX)
VC_Q-SP = MIN(MAX(VC_Q-SP, VC_MIN), VC_MAX)
VGR_Q-SP = MIN(MAX(VGR_Q-SP, VGR_MIN), VGQ_MAX)
VCR_Q-SP = MIN(MAX(VCR_Q-SP, VCR_MIN), VCQ_MAX)

// Limitar selector de plenum
PLENUM = MAX(1, MIN(PLENUM, 6))

// Lógica de selección de plenum y activación/desactivación de VAVs
IF SS_CP = 1 THEN
    IF PLENUM = 1 THEN
        // Activar Plenum 1
        REM ***PRESION DE PLENUM
					DP_1 = P1_DP_1
					DP_2 = P1_DP_2
			
				REM ***BLOQUEO DE ACTIVACION DE VAV ACTIVA

					RLQ BV9@7
					RLQ BV10@7
					RLQ BV11@7
			
				REM ***LIMITE DE CAUDAL POR TAMANO DE CAJA
					VG_MAX = P1_VG_QMAX
					VG_MIN = P1_VG_QMIN
					VM_MAX = P1_VM_QMAX
					VM_MIN = P1_VM_QMIN
					VC_MAX = P1_VC_QMAX
					VC_MIN = P1_VC_QMIN
			
				REM ***CAUDAL DE AIRE
					VG_Q = P1_VG_Q
					VM_Q = P1_VM_Q
					VC_Q = P1_VC_Q
			
				REM ***DEMANDA DE AIRE
					P1_VG_DEMANDA = VG_DEMANDA
					P1_VM_DEMANDA = VM_DEMANDA
					P1_VC_DEMANDA = VC_DEMANDA
					P2_VG_DEMANDA = 0
					P2_VM_DEMANDA = 0
					P3_VG_DEMANDA = 0
					P4_VG_DEMANDA = 0
					P4_VM_DEMANDA = 0
					P4_VC_DEMANDA = 0
					P5_VG_DEMANDA = 0
					P5_VC_DEMANDA = 0
					P6_VG_DEMANDA = 0
					P6_VM_DEMANDA = 0
			
				REM ***ESTADO DE PLENUM ACTIVO
					ST_P1 = 1
					ST_P2 = 0
					ST_P3 = 0
					ST_P4 = 0
					ST_P5 = 0
					ST_P6 = 0
        ...
    ELSE IF PLENUM = 2 THEN
        // Activar Plenum 2
        REM ***PRESION DE PLENUM
					DP_1 = P2_DP
					DP_2 = 0
			
				REM ***BLOQUEO DE ACTIVACION DE VAV ACTIVA

					RLQ BV9@7
					RLQ BV10@7
					BV11@7 = 0
			
				REM ***LIMITE DE CAUDAL POR TAMANO DE CAJA
					VG_MAX = P1_VG_QMAX
					VG_MIN = P1_VG_QMIN
					VM_MAX = P1_VM_QMAX
					VM_MIN = P1_VM_QMIN
					VC_MAX = 0
					VC_MIN = 0
			
				REM ***CAUDAL DE AIRE
					VG_Q = P1_VG_Q
					VM_Q = P1_VM_Q
					VC_Q = 0
			
				REM ***DEMANDA DE AIRE
					P1_VG_DEMANDA = 0
					P1_VM_DEMANDA = 0
					P1_VC_DEMANDA = 0
					P2_VG_DEMANDA = VG_DEMANDA
					P2_VM_DEMANDA = VM_DEMANDA
					P3_VG_DEMANDA = 0
					P4_VG_DEMANDA = 0
					P4_VM_DEMANDA = 0
					P4_VC_DEMANDA = 0
					P5_VG_DEMANDA = 0
					P5_VC_DEMANDA = 0
					P6_VG_DEMANDA = 0
					P6_VM_DEMANDA = 0
			
				REM ***ESTADO DE PLENUM ACTIVO
					ST_P1 = 0
					ST_P2 = 1
					ST_P3 = 0
					ST_P4 = 0
					ST_P5 = 0
					ST_P6 = 0
        ...
    ELSE IF PLENUM = 3 THEN
        // Activar Plenum 3
        ...
    ELSE IF PLENUM = 4 THEN
        // Activar Plenum 4
        ...
    ELSE IF PLENUM = 5 THEN
        // Activar Plenum 5
        ...
    ELSE IF PLENUM = 6 THEN
        // Activar Plenum 6
        ...
    ENDIF

    // Control de Plenum de Retorno (siempre activo si SS_CP = 1)
    PR7_VG_DEMANDA = VGR_DEMANDA
    PR7_VC_DEMANDA = VCR_DEMANDA

ELSE // SS_CP = 0
    // Desactivar todos los plenums
    P1_VG_DEMANDA = 100
    P1_VM_DEMANDA = 100
    P1_VC_DEMANDA = 100
    ...
ENDIF

// Calcular estado de operación general
ST_CP = MAX(ST_P1, ST_P2, ST_P3, ST_P4, ST_P5, ST_P6)

```

**Diagrama de Flujo:**

```mermaid
flowchart TB
    VAREXT[/"Variables Externas<br>PLENUM, SS_CP, Q-SP, Q, DP"/] --> VARINT
    VARINT[/"Constantes<br>MAX, MIN"/] --> SPQ
    SPQ["Q-SP = MIN(MAX(Q-SP, MIN), MAX)"] --> PLENUM
    PLENUM["PLENUM = MAX(1, MIN(PLENUM, 6))"] --> SSCP
    SSCP{"SS_CP = 1"} -- SI --> PL1
    SSCP -- NO --> OFF1
    OFF1["DEMANDA = 100"] --> OFF2
    OFF2["ST_P[#] = 0"] --> OFF3
    OFF3["BLOQUEO DE ACTIVACION DE VAVS ACTIVAS"] --> ST
    PL1{PLENUM = 1} -- SI --> CNX1
    CNX1[CONEXION DE VARIABLE PLENUM 1 A CONTROL] --> ST
    PL1 -- NO --> PL2
    PL2{PLENUM =2} -- SI --> CNX2
    CNX2[CONEXION DE VARIABLE PLENUM 2 A CONTROL] --> ST
    PL2 -- NO --> PL3
    PL3{PLENUM = 3} -- SI --> CNX3
    CNX3[CONEXION DE VARIABLE PLENUM 3 A CONTROL] --> ST
    PL3 -- NO --> PL4
    PL4{PLENUM = 4} -- SI --> CNX4
    CNX4[CONEXION DE VARIABLE PLENUM 4 A CONTROL] --> ST
    PL4 -- NO --> PL5
    PL5{PLENUM = 5} -- SI --> CNX5
    CNX5[CONEXION DE VARIABLE PLENUM 5 A CONTROL] --> ST
    PL5 -- NO --> PL6
    PL6{PLENUM = 6} -- SI --> CNX6
    CNX6[CONEXION DE VARIABLE PLENUM 6 A CONTROL] --> ST
    PL6 -- NO --> ST
    ST["ST_CP = MAX(ST_P1, ST_P2, ST_P3, ST_P4, ST_P5, ST_P6)"] --> VAROUT

    VAROUT[/"Variables externas<br>"/]
    

    classDef var fill:#0077CC, stroke:#00BFFF, stroke-width:2px, color:#FFFFFF
    class VAREXT,VARINT,VAROUT var

    classDef proceso fill:#003366, stroke:#006699, stroke-width:2px, color:#ADD8E6
    class SPQ,PLENUM,SSCP,OFF1,OFF2,OFF3,PL1,CNX1,PL2,CNX2,PL3,CNX3,PL4,CNX4,PL5,CNX5,PL6,CNX6,ST proceso

    classDef negativo fill:#663300, stroke:#522900, stroke-width:2px, color:#FFFFFF
    class OFF1,OFF2,OFF3 negativo


```
