# SISTEMA DE CONTROL DEL CUARTO DE PRUEBAS

Este sistema opera 15 cajas de volumen variable, las cuales están conectadas a la descarga de la Unidad Manejadora de aire 1, integradas a 7 plenums del sistema de cuarto de flujo de aire. 

## TARJETAS DE CONTROL

Sistema de control para la operación de las cajas VAV del *Cuarto de Pruebas*, el sistema está distribuido en 2 tarjetas de control maestras con módulos de expansión de entradas y salidas

> Controlador KMC [**BAC-5901C**](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/ "Documentación de equipo")
>
> - 8 Entradas Universales, 8 Salidas Universales
> - Puerto *RS-485* **BACnet MS/TP**
> - Alimentación a ***24 VAC/DC***

> Módulo de expansión KMC [**CAN-5901**](https://www.kmccontrols.com/product/expansion-io-module-8-ui-8-uo/ "Documentación de equipo")
>
> - 8 Entradas Universales, 8 Salidas Universales
> - Alimentación a ***24 VAC/DC***

> Módulo de expansión KMC [**CAN-5902**](https://www.kmccontrols.com/product/expansion-io-module-16-ui/ "Documentación de equipo")
>
> - 16 Entradas Universales
> - Alimentación a ***24 VAC/DC***

### 10021_CNTR-1

> DI `10021`
>
> MAC Address `21`

> ENTRADAS UNIVERSALES `16`
>
> SALIDAS UNIVERSALES `16`

- 1 Contrololador programable KMC [**BAC-5901C**](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/ "Documentación de equipo")

- 1 Módulo de expansión KMC [**CAN-5901**](https://www.kmccontrols.com/product/expansion-io-module-8-ui-8-uo/ "Documentación de equipo")

- 1 Módulo de expansión KMC [**CAN-5901**](https://www.kmccontrols.com/product/expansion-io-module-8-ui-8-uo/ "Documentación de equipo")

#### PUNTOS DE ENTRADA

##### CNTR (BAC-5901)

> * **IN03** `P1_VM_DP` PLENUM 1, VAV 01 - MEDIANA, PRES DIF
> * **IN04** `P1_VG_DP` PLENUM 1, VAV 02 - GRANDE, PRES DIF
> * **IN05** `P2_VM_DP` PLENUM 2, VAV 01 - MEDIANA, PRES DIF
> * **IN06** `P2_VG_DP` PLENUM 2, VAV 02 - GRANDE, PRES DIF
> * **IN07** `P4_VM_DP` PLENUM 4, VAV 01 - MEDIANA, PRES DIF
> * **IN08** `P4_VG_DP` PLENUM 4, VAV 02 - GRANDE, PRES DIF
> * **IN09** `P4_VC_DP` PLENUM 4, VAV 03 - CHICA, PRES DIF
> * **IN10** `P5_VC_DP` PLENUM 5, VAV 01 - CHICA, PRES DIF

##### EXP-1 (CAN-5901)

> * **IN11** `P5_VG_DP` PLENUM 5, VAV 02 - GRANDE, PRES DIF
> * **IN12** `P6_VG_DP` PLENUM 6, VAV 01 - GRANDE, PRES DIF
> * **IN13** `P6_VM_DP` PLENUM 6, VAV 02 - MEDIANA, PRES DIF
> * **IN14** `PR7_VC_DP` PLENUM R7, VAV 01 - CHICA, PRES DIF
> * **IN15** `PR7_VG_DP` PLENUM R7, VAV 02 - GRANDE, PRES DIF
> * **IN16** `P1_VC_DP` PLENUM 1, VAV 03 - CHICA, PRES DIF
> * **IN17** `P3_VG_DP` PLENUM 1, VAV 01 - GRANDE, PRES DIF
> * **IN18** `P1_DP-1` PLENUM 1, CAIDA DE PRESION 1

##### EXP-2 (CAN-5901)

> * **IN19** `SAT` TEMPERATURA DE SUMINISTRO DE AIRE
> * **IN20** `V1_T1` VELOCIDAD DE AIRE 1, TIRO 1
> * **IN21** `V2_T1` VELOCIDAD DE AIRE 2, TIRO 1
> * **IN22** `V3_T1` VELOCIDAD DE AIRE 3, TIRO 1
> * **IN23** `V4_T1` VELOCIDAD DE AIRE 4, TIRO 1
> * **IN24** `V5_T1` VELOCIDAD DE AIRE 5, TIRO 1
> * **IN25** `V6_T1` VELOCIDAD DE AIRE 6, TIRO 1
> * **IN26** `V7_T1` VELOCIDAD DE AIRE 7, TIRO 1

#### PUNTOS DE SALIDA

##### CNTR (BAC-5901)

> * **OUT01** `P1_VM_A` PLENUM 1, VAV 01 - MEDIANA, COMPUERTA
> * **OUT02** `P1_VG_A` PLENUM 1, VAV 02 - GRANDE, COMPUERTA
> * **OUT03** `P2_VM_A` PLENUM 2, VAV 01 - MEDIANA, COMPUERTA
> * **OUT04** `P2_VG_A` PLENUM 2, VAV 02 - GRANDE, COMPUERTA
> * **OUT05** `P4_VM_A` PLENUM 4, VAV 01 - MEDIANA, COMPUERTA
> * **OUT06** `P4_VG_A` PLENUM 4, VAV 02 - GRANDE, COMPUERTA
> * **OUT07** `P4_VC_A` PLENUM 4, VAV 03 - CHICA, COMPUERTA
> * **OUT08** `P5_VC_A` PLENUM 5, VAV 01 - CHICA, COMPUERTA

##### EXP-1 (CAN-5901)

> * **OUT09** `P5_VG_A` PLENUM 5, VAV 02 - GRANDE, COMPUERTA
> * **OUT10** `P6_VG_A` PLENUM 6, VAV 01 - GRANDE, COMPUERTA
> * **OUT11** `P6_VM_A` PLENUM 6, VAV 02 - MEDIANA, COMPUERTA
> * **OUT12** `PR7_VC_A` PLENUM R7, VAV 01 - CHICA, COMPUERTA
> * **OUT13** `PR7_VG_A` PLENUM R7, VAV 02 - GRANDE, COMPUERTA
> * **OUT14** `P1_VM_AB` PLENUM 1, VAV 01 - MEDIANA, COMP BLOQ
> * **OUT15** `P1_VG_AB` PLENUM 1, VAV 02 - GRANDE, COMP BLOQ
> * **OUT16** `P2_VM_AB` PLENUM 2, VAV 01 - MEDIANA, COMP BLOQ

##### EXP-1 (CAN-5901)

> * **OUT17** `PR7_VC_AB` PLENUM 1, VAV 01 - MEDIANA, COMP BLOQ
> * **OUT18** `PR7_VG_AB` PLENUM 1, VAV 02 - GRANDE, COMP BLOQ
> * **OUT19** `SS_HUMO` COMPUERTA DE HUMO
> * **OUT20**
> * **OUT21** `P1_VC_A` PLENUM 1, VAV 03 - CHICA, COMPUERTA
> * **OUT22** `P1_VC_AB` PLENUM 1, VAV 03 - CHICA, COMP BLOQ
> * **OUT23** `P3_VG_A` PLENUM 3, VAV 01 - GRANDE, COMPUERTA
> * **OUT24** `P3_VG_AB` PLENUM 3, VAV 01 - GRANDE, COMP BLOQ

### 10022_CNTR-2

> DI `10022`
>
> MAC Address `22`

> ENTRADAS UNIVERSALES `32`
>
> SALIDAS UNIVERSALES `16`

- 1 Contrololador programable KMC [**BAC-5901C**](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/ "Documentación de equipo")

- 1 Módulo de expansión KMC [**CAN-5902**](https://www.kmccontrols.com/product/expansion-io-module-16-ui/ "Documentación de equipo")

#### PUNTOS DE ENTRADA

##### CNTR (BAC-5901)

> * **IN03** `P1_DP-2` PLENUM 1, CAIDA DE PRESION 2
> * **IN04** `P2_DP` PLENUM 2, CAIDA DE PRESION
> * **IN05** `P2_DP` PLENUM 4, CAIDA DE PRESION
> * **IN06** `P2_DP` PLENUM 5, CAIDA DE PRESION
> * **IN07** `P2_DP` PLENUM 6, CAIDA DE PRESION
> * **IN08** `P2_DP` PLENUM R7, CAIDA DE PRESION
> * **IN09** 
> * **IN10** `V8` VELOCIDAD 8

##### EXP-1 (CAN-5901) - CONEXIONES A FUTURO

> * **IN11** `V1_T2` VELOCIDAD DE AIRE 1, TIRO 2
> * **IN12** `V1_T2` VELOCIDAD DE AIRE 2, TIRO 2
> * **IN13** `V1_T2` VELOCIDAD DE AIRE 3, TIRO 2
> * **IN14** `V1_T2` VELOCIDAD DE AIRE 4, TIRO 2
> * **IN15** `V1_T2` VELOCIDAD DE AIRE 5, TIRO 2
> * **IN16** `V1_T2` VELOCIDAD DE AIRE 6, TIRO 2
> * **IN17** `V1_T2` VELOCIDAD DE AIRE 7, TIRO 2
> * **IN18** 
> * **IN19** `V1_T2` VELOCIDAD DE AIRE 1, TIRO 3
> * **IN20** `V1_T2` VELOCIDAD DE AIRE 2, TIRO 4
> * **IN21** `V1_T2` VELOCIDAD DE AIRE 3, TIRO 5
> * **IN22** `V1_T2` VELOCIDAD DE AIRE 4, TIRO 6
> * **IN23** `V1_T2` VELOCIDAD DE AIRE 5, TIRO 7
> * **IN24** `V1_T2` VELOCIDAD DE AIRE 6, TIRO 8
> * **IN25** `V1_T2` VELOCIDAD DE AIRE 7, TIRO 9
> * **IN26**

#### PUNTOS DE SALIDA

##### CNTR (BAC-5901)

> * **OUT01** `P2_VG_AB` PLENUM 2, VAV 02 - GRANDE, COMP BLOQ
> * **OUT02** `P4_VM_AB` PLENUM 4, VAV 01 - MEDIANA, COMP BLOQ
> * **OUT03** `P4_VG_AB` PLENUM 4, VAV 02 - GRANDE, COMP BLOQ
> * **OUT04** `P4_VC_AB` PLENUM 4, VAV 03 - CHICA, COMP BLOQ
> * **OUT05** `P5_VC_AB` PLENUM 5, VAV 01 - CHICA, COMP BLOQ
> * **OUT06** `P5_VG_AB` PLENUM 5, VAV 02 - GRANDE, COMP BLOQ
> * **OUT07** `P6_VG_AB` PLENUM 6, VAV 01 - GRANDE, COMP BLOQ
> * **OUT08** `P6_VM_AB` PLENUM 6, VAV 02 - MEDIANA, COMP BLOQ

## SISTEMA

- PLENUM 1
>   **VAV-01**  MEDIANA
>
>   **VAV-02**  GRANDE
>
>   **VAV-03**  CHICA

- PLENUM 2
>   **VAV-01**  MEDIANA
>
>   **VAV-02**  GRANDE

- PLENUM 3
>   **VAV-01**  GRANDE

- PLENUM 4
>   **VAV-01**  MEDIANA
>
>   **VAV-02**  GRANDE
>
>   **VAV-03**  CHICA

- PLENUM 5
>   **VAV-01**  CHICA
>
>   **VAV-02**  GRANDE

- PLENUM 6
>   **VAV-01**  GRANDE
>
>   **VAV-02**  MEDIANA

- PLENUM R7
>   **VAV-01**  CHICA
>
>   **VAV-02**  GRANDE

Para acceder a los datos del sistema, ingresar a [***VAVs.md***](https://github.com/cjhirashi/ct-prub-in/blob/main/CUARTO-PRUEBAS/VAVs.md "Datos de cajas VAV del sistema")