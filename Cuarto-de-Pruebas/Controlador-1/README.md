# CONTROL DE CUARTO DE PRUEBAS - CONTROLADOR 1

Control de las 15 ***Cajas VAV*** y 7 ***Plenums*** del sistema de control del cuarto de Pruebas

## TARJETAS DE CONTROL

> Controlador KMC [**BAC-5901C**](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/ "Documentación de equipo")
>
> - 8 Entradas Universales, 8 Salidas Universales
> - Puerto *RS-485* **BACnet MS/TP**
> - Alimentación a ***24 VAC/DC***

> Módulo de expansión KMC [**CAN-5901**](https://www.kmccontrols.com/product/expansion-io-module-8-ui-8-uo/ "Documentación de equipo")
>
> - 8 Entradas Universales, 8 Salidas Universales
> - Alimentación a ***24 VAC/DC***

### 10021_CNTR-1

> DI `10021`
>
> MAC Address `21`

> ENTRADAS UNIVERSALES `24`
>
> SALIDAS UNIVERSALES `24`

## PROGRAMAS

### PRG1_SENSORES

Programa diseñado para calcular y ajustar los caudales de aire de múltiples VAVs (Válvulas de Volumen de Aire Variable) dentro de diferentes plenums de un sistema HVAC. Utiliza mediciones de presión diferencial para estimar el flujo de aire, y aplica factores de calibración para ajustar cada caudal a los valores reales requeridos, logrando un control preciso del sistema.

### PRG2_VAVS

El programa controla las compuertas de un sistema de VAVs (Variable Air Volume) distribuidas en múltiples plenums. Monitorea las demandas de ventilación de cada VAV y ajusta la apertura de las compuertas en función de parámetros predefinidos para mantener un flujo de aire óptimo. La activación de los VAVs y los estados de las compuertas se gestionan con intervalos de sincronización para asegurar un control eficiente y equilibrado del sistema.

### PRG3_PLENUMS

Programa para gestionar y controlar el flujo de aire en un sistema de múltiples plenum mediante el uso de cajas VAV. La lógica del programa asigna caudales, controla las compuertas de las cajas, supervisa la presión en los plenum activos y ajusta los límites operativos de cada caja VAV de acuerdo a la demanda y las configuraciones establecidas.

### PRG4_DEMANDA

Este programa controla la demanda de plenos en un sistema HVAC mediante un algoritmo PI (Proporcional-Integral) para gestionar diferentes secciones del sistema, ajustando la demanda en función de parámetros establecidos y límites de operación. El programa asegura el funcionamiento adecuado y eficiente de cada caja de ventilación y sus respectivos retornos.

### PRG5_UMA

El programa PRG5_UMA se encarga del control periódico de una Unidad de Manejo de Aire (UMA), sincronizando datos de estado y configurando puntos específicos de un controlador BACnet. Ejecuta tareas de monitoreo y control condicionales para asegurar el correcto funcionamiento de la UMA en intervalos de tiempo predefinidos.

---

## PUNTOS DE ENTRADA

### CNTR (BAC-5901)

> * **IN03** `P1_VM_DP` PLENUM 1, VAV 01 - MEDIANA, PRES DIF
> * **IN04** `P1_VG_DP` PLENUM 1, VAV 02 - GRANDE, PRES DIF
> * **IN05** `P2_VM_DP` PLENUM 2, VAV 01 - MEDIANA, PRES DIF
> * **IN06** `P2_VG_DP` PLENUM 2, VAV 02 - GRANDE, PRES DIF
> * **IN07** `P4_VM_DP` PLENUM 4, VAV 01 - MEDIANA, PRES DIF
> * **IN08** `P4_VG_DP` PLENUM 4, VAV 02 - GRANDE, PRES DIF
> * **IN09** `P4_VC_DP` PLENUM 4, VAV 03 - CHICA, PRES DIF
> * **IN10** `P5_VC_DP` PLENUM 5, VAV 01 - CHICA, PRES DIF

### EXP-1 (CAN-5901)

> * **IN11** `P5_VG_DP` PLENUM 5, VAV 02 - GRANDE, PRES DIF
> * **IN12** `P6_VG_DP` PLENUM 6, VAV 01 - GRANDE, PRES DIF
> * **IN13** `P6_VM_DP` PLENUM 6, VAV 02 - MEDIANA, PRES DIF
> * **IN14** `PR7_VC_DP` PLENUM R7, VAV 01 - CHICA, PRES DIF
> * **IN15** `PR7_VG_DP` PLENUM R7, VAV 02 - GRANDE, PRES DIF
> * **IN16** `P1_VC_DP` PLENUM 1, VAV 03 - CHICA, PRES DIF
> * **IN17** `P3_VG_DP` PLENUM 1, VAV 01 - GRANDE, PRES DIF
> * **IN18** `P1_DP-1` PLENUM 1, CAIDA DE PRESION 1

### EXP-2 (CAN-5901)

> * **IN19** `SAT` TEMPERATURA DE SUMINISTRO DE AIRE
> * **IN20** `V1_T1` VELOCIDAD DE AIRE 1, TIRO 1
> * **IN21** `V2_T1` VELOCIDAD DE AIRE 2, TIRO 1
> * **IN22** `V3_T1` VELOCIDAD DE AIRE 3, TIRO 1
> * **IN23** `V4_T1` VELOCIDAD DE AIRE 4, TIRO 1
> * **IN24** `V5_T1` VELOCIDAD DE AIRE 5, TIRO 1
> * **IN25** `V6_T1` VELOCIDAD DE AIRE 6, TIRO 1
> * **IN26** `V7_T1` VELOCIDAD DE AIRE 7, TIRO 1

## PUNTOS DE SALIDA

### CNTR (BAC-5901)

> * **OUT01** `P1_VM_A` PLENUM 1, VAV 01 - MEDIANA, COMPUERTA
> * **OUT02** `P1_VG_A` PLENUM 1, VAV 02 - GRANDE, COMPUERTA
> * **OUT03** `P2_VM_A` PLENUM 2, VAV 01 - MEDIANA, COMPUERTA
> * **OUT04** `P2_VG_A` PLENUM 2, VAV 02 - GRANDE, COMPUERTA
> * **OUT05** `P4_VM_A` PLENUM 4, VAV 01 - MEDIANA, COMPUERTA
> * **OUT06** `P4_VG_A` PLENUM 4, VAV 02 - GRANDE, COMPUERTA
> * **OUT07** `P4_VC_A` PLENUM 4, VAV 03 - CHICA, COMPUERTA
> * **OUT08** `P5_VC_A` PLENUM 5, VAV 01 - CHICA, COMPUERTA

### EXP-1 (CAN-5901)

> * **OUT09** `P5_VG_A` PLENUM 5, VAV 02 - GRANDE, COMPUERTA
> * **OUT10** `P6_VG_A` PLENUM 6, VAV 01 - GRANDE, COMPUERTA
> * **OUT11** `P6_VM_A` PLENUM 6, VAV 02 - MEDIANA, COMPUERTA
> * **OUT12** `PR7_VC_A` PLENUM R7, VAV 01 - CHICA, COMPUERTA
> * **OUT13** `PR7_VG_A` PLENUM R7, VAV 02 - GRANDE, COMPUERTA
> * **OUT14** `P1_VM_AB` PLENUM 1, VAV 01 - MEDIANA, COMP BLOQ
> * **OUT15** `P1_VG_AB` PLENUM 1, VAV 02 - GRANDE, COMP BLOQ
> * **OUT16** `P2_VM_AB` PLENUM 2, VAV 01 - MEDIANA, COMP BLOQ

### EXP-1 (CAN-5901)

> * **OUT17** `PR7_VC_AB` PLENUM 1, VAV 01 - MEDIANA, COMP BLOQ
> * **OUT18** `PR7_VG_AB` PLENUM 1, VAV 02 - GRANDE, COMP BLOQ
> * **OUT19** `SS_HUMO` COMPUERTA DE HUMO
> * **OUT20**
> * **OUT21** `P1_VC_A` PLENUM 1, VAV 03 - CHICA, COMPUERTA
> * **OUT22** `P1_VC_AB` PLENUM 1, VAV 03 - CHICA, COMP BLOQ
> * **OUT23** `P3_VG_A` PLENUM 3, VAV 01 - GRANDE, COMPUERTA
> * **OUT24** `P3_VG_AB` PLENUM 3, VAV 01 - GRANDE, COMP BLOQ