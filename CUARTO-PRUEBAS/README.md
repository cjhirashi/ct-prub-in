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

#### PUNTOS DE CONTROL DEL SISTEMA

***CNTR*** (BAC-5901)

* **IN03** `P1_VM_DP` PLENUM 1, VAV 01 - MEDIANA
* **IN04** `P1_VG_DP` PLENUM 1, VAV 02 - GRANDE
* **IN05** `P2_VM_DP` PLENUM 2, VAV 01 - MEDIANA
* **IN06** `P2_VG_DP` PLENUM 2, VAV 02 - GRANDE
* **IN07** `P4_VM_DP` PLENUM 4, VAV 01 - MEDIANA
* **IN08** `P4_VG_DP` PLENUM 4, VAV 02 - GRANDE
* **IN09** `P4_VC_DP` PLENUM 4, VAV 03 - CHICA
* **IN10** `P5_VC_DP` PLENUM 5, VAV 01 - CHICA

***EXP-1*** (CAN-5901)

* **IN11** `P5_VG_DP` PLENUM 5, VAV 02 - GRANDE
* **IN12** `P6_VG_DP` PLENUM 6, VAV 01 - GRANDE
* **IN13** `P6_VM_DP` PLENUM 6, VAV 02 - MEDIANA
* **IN14** `PR7_VC_DP` PLENUM R7, VAV 01 - CHICA
* **IN15** `PR7_VG_DP` PLENUM R7, VAV 02 - GRANDE
* **IN16** `P1_VC_DP` PLENUM 1, VAV 03 - CHICA
* **IN17** `P3_VG_DP` PLENUM 1, VAV 01 - GRANDE
* **IN18** `P1_DP-1` PLENUM 1, CAIDA DE PRESION 1

***EXP-2*** (CAN-5901)

* **IN19** `SAT` TEMPERATURA DE SUMINISTRO DE AIRE
* **IN20** `V1_T1` VELOCIDAD DE AIRE 1, TIRO 1
* **IN21** `V2_T1` VELOCIDAD DE AIRE 2, TIRO 1
* **IN22** `V3_T1` VELOCIDAD DE AIRE 3, TIRO 1
* **IN23** `V4_T1` VELOCIDAD DE AIRE 4, TIRO 1
* **IN24** `V5_T1` VELOCIDAD DE AIRE 5, TIRO 1
* **IN25** `V6_T1` VELOCIDAD DE AIRE 6, TIRO 1
* **IN26** `V7_T1` VELOCIDAD DE AIRE 7, TIRO 1

### 10022_CNTR-2

> DI `10022`
>
> MAC Address `22`

> ENTRADAS UNIVERSALES `32`
>
> SALIDAS UNIVERSALES `16`

- 1 Contrololador programable KMC [**BAC-5901C**](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/ "Documentación de equipo")

- 1 Módulo de expansión KMC [**CAN-5902**](https://www.kmccontrols.com/product/expansion-io-module-16-ui/ "Documentación de equipo")

#### PUNTOS DE CONTROL DEL SISTEMA

***CNTR*** (BAC-5901)

* **IN03** `P1_DP-2` PLENUM 1, CAIDA DE PRESION 2
* **IN04** `P2_DP` PLENUM 2, CAIDA DE PRESION
* **IN05** `P2_DP` PLENUM 4, CAIDA DE PRESION
* **IN06** `P2_DP` PLENUM 5, CAIDA DE PRESION
* **IN07** `P2_DP` PLENUM 6, CAIDA DE PRESION
* **IN08** `P2_DP` PLENUM R7, CAIDA DE PRESION
* **IN09** 
* **IN10** `V8` VELOCIDAD 8

***EXP-1*** (CAN-5901) - CONEXIONES A FUTURO

* **IN11** `V1_T2` VELOCIDAD DE AIRE 1, TIRO 2
* **IN12** `V1_T2` VELOCIDAD DE AIRE 2, TIRO 2
* **IN13** `V1_T2` VELOCIDAD DE AIRE 3, TIRO 2
* **IN14** `V1_T2` VELOCIDAD DE AIRE 4, TIRO 2
* **IN15** `V1_T2` VELOCIDAD DE AIRE 5, TIRO 2
* **IN16** `V1_T2` VELOCIDAD DE AIRE 6, TIRO 2
* **IN17** `V1_T2` VELOCIDAD DE AIRE 7, TIRO 2
* **IN18** 
* **IN19** `V1_T2` VELOCIDAD DE AIRE 1, TIRO 3
* **IN20** `V1_T2` VELOCIDAD DE AIRE 2, TIRO 4
* **IN21** `V1_T2` VELOCIDAD DE AIRE 3, TIRO 5
* **IN22** `V1_T2` VELOCIDAD DE AIRE 4, TIRO 6
* **IN23** `V1_T2` VELOCIDAD DE AIRE 5, TIRO 7
* **IN24** `V1_T2` VELOCIDAD DE AIRE 6, TIRO 8
* **IN25** `V1_T2` VELOCIDAD DE AIRE 7, TIRO 9
* **IN26**

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