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

> DI `10022`
>
> MAC Address `22`

> ENTRADAS UNIVERSALES `24`
>
> SALIDAS UNIVERSALES `24`

## PROGRAMAS

### PRG1_CALIBRACION

El programa gestiona un sistema de calibración de caudales en un entorno HVAC, permitiendo el ajuste y control de las aperturas de compuertas y la toma de muestras de caudales. Utiliza variables de activación y parámetros de calibración para asegurar que los sistemas de ventilación operen con eficiencia, ajustando los multiplicadores y compensaciones necesarias en función de las mediciones obtenidas.

## PUNTOS DE ENTRADA

### CNTR (BAC-5901)

> * **IN03** `` 

## PUNTOS DE SALIDA

### CNTR (BAC-5901)

> * **OUT01** `` 