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

***CNTR-1***

* **IN03** `P1_VM_DP` PELNUM 1, VAV 01 - MEDIANA
* **IN04** `P1_VG_DP` PLENUM 1, VAV 02 - GRANDE
* **IN05** `P2_VM_DP`
* **IN06** `P2_VG_DP`
* **IN07** ``
* **IN08** ``
* **IN09** ``
* **IN10** ``

***EXP-1***

* **IN11** ``
* **IN12** ``
* **IN13** ``
* **IN14** ``
* **IN15** ``
* **IN16** ``
* **IN17** ``
* **IN18** ``

***EXP-2***

* **IN19** ``
* **IN20** ``
* **IN21** ``
* **IN22** ``
* **IN23** ``
* **IN24** ``
* **IN25** ``
* **IN26** ``

### 10022_CNTR-2

> DI `10022`
>
> MAC Address `22`

> ENTRADAS UNIVERSALES `32`
>
> SALIDAS UNIVERSALES `16`

- 1 Contrololador programable KMC [**BAC-5901C**](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/ "Documentación de equipo")

- 1 Módulo de expansión KMC [**CAN-5902**](https://www.kmccontrols.com/product/expansion-io-module-16-ui/ "Documentación de equipo")

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