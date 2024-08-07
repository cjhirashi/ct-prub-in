# PRG2 VAVS

Control de apertura de compuerta de VAV por demanda de control de suministro de aire por *CFMs* y control de apertura de compuerta de bloqueo de aire.

## VARIABLES GLOBALES

> `P1_VG_QMAX` = 3200 ( ***CFM*** )	| Caudal máximo
> `P1_VG_QMIN` = 500 ( ***CFM*** )	| Caudal mínimo
> `P1_VM_QMAX` = 1050 ( ***CFM*** )	| Caudal máximo
> `P1_VM_QMIN` = 175 ( ***CFM*** )	| Caudal mínimo
> `P1_VC_QMAX` = 250 ( ***CFM*** )	| Caudal máximo
> `P1_VC_QMIN` = 45 ( ***CFM*** )	| Caudal mínimo
> `P2_VG_QMAX` = 2350 ( ***CFM*** )	| Caudal máximo
> `P2_VG_QMIN` = 400 ( ***CFM*** )	| Caudal mínimo
> `P2_VM_QMAX` = 800 ( ***CFM*** )	| Caudal máximo
> `P2_VM_QMIN` = 140 ( ***CFM*** )	| Caudal mínimo
> `P3_VG_QMAX` = 1450 ( ***CFM*** )	| Caudal máximo
> `P3_VG_QMIN` = 290 ( ***CFM*** )	| Caudal mínimo
> `P4_VG_QMAX` = 3200 ( ***CFM*** )	| Caudal máximo
> `P4_VG_QMIN` = 500 ( ***CFM*** )	| Caudal mínimo
> `P4_VM_QMAX` = 1050 ( ***CFM*** )	| Caudal máximo
> `P4_VM_QMIN` = 175 ( ***CFM*** )	| Caudal mínimo
> `P4_VC_QMAX` = 250 ( ***CFM*** )	| Caudal máximo
> `P4_VC_QMIN` = 45	 ( ***CFM*** )	| Caudal mínimo
> `P5_VG_QMAX` = 4200 ( ***CFM*** )	| Caudal máximo
> `P5_VG_QMIN` = 700 ( ***CFM*** )	| Caudal mínimo
> `P5_VC_QMAX` = 400 ( ***CFM*** )	| Caudal máximo
> `P5_VC_QMIN` = 70	 ( ***CFM*** )	| Caudal mínimo
> `P6_VG_QMAX` = 3200 ( ***CFM*** )	| Caudal máximo
> `P6_VG_QMIN` = 500 ( ***CFM*** )	| Caudal mínimo
> `P6_VM_QMAX` = 1050 ( ***CFM*** )	| Caudal máximo
> `P6_VM_QMIN` = 175 ( ***CFM*** )	| Caudal mínimo
> `P7_VG_QMAX` = 3200 ( ***CFM*** )	| Caudal máximo
> `P7_VG_QMIN` = 500 ( ***CFM*** )	| Caudal mínimo
> `P7_VC_QMAX` = 250 ( ***CFM*** )	| Caudal máximo
> `P7_VC_QMIN` = 45	 ( ***CFM*** )	| Caudal mínimo


## MEDICION POR CAJA VAV

### ASIGNACIÓN DE VARIABLES LOCALES

Asignar variables de caja VAV a controlar

> `DEMANDA` = [AV]
>
> [AO] = `VAV`
>
> [BO] = `CM_BL`

### ACTIVACION DE CAJA

***ACTIVACION*** El control de la compuerta se activa cuando la `DEMANDA` de la compuerta sea mayor a lo establecido en la variable `P_APER`

***DESACTIVACION*** El control de la compuerta se desactiva cuando la `DEMANDA` sea menor que 1%

```bash

```

### ASIGNACION DE DEMANDA A COMPUETAS POR ESTADO DE ACTIVACIÓN

Cuando el estado de `ACTIV` sea *On*, se asignará al control de compuerta `VAV` el valor de `DEMANDA` y a la compueta de bloqueo `CM_BL` el valor de *On*

Cuando el estado de `ACTIV` sea *Off*, se asignará al control de compuerta `VAV` el valor de 0% y a la compueta de bloqueo `CM_BL` el valor de *Off*

```bash

```

### ASIGNACIÓN DE CONTROL DE COMPUERTAS A SALIDAS 

Asignación de de estados de apertura del control de compuerta `VAV` y control de compuerta de bloqueo `CM_BL` a puertos de salida del controlador.

```bash

```

Código para cajas con control de compuerta de bloqueo desde equipo remoto

```bash

```

### SEGMENTO COMPLETO

Código para cajas con ambas compuertas en el mismo controlador

```bash

```

Código para cajas con control de compuerta de bloqueo desde equipo remoto

```bash

```

## PARAMETROS DE CAJAS

### PLENUM 1

#### VAV-01 - MEDIANA

> `DEMANDA` = ***AV85*** | `VAV` = ***AO1*** | `CM_BL` = ***BO14***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV86*** | `VAV` = ***AO2*** | `CM_BL` = ***BO15***

### PLENUM 2

#### VAV-01 - MEDIANA

> `DEMANDA` = ***AV87*** | `VAV` = ***AO3*** | `CM_BL` = ***BO16***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV88*** | `VAV` = ***AO4*** | `CM_BL` = ***10022.BO1***

### PLENUM 4

#### VAV-01 - MEDIANA

> `DEMANDA` = ***AV89*** | `VAV` = ***AO5*** | `CM_BL` = ***10022.BO2***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV90*** | `VAV` = ***AO6*** | `CM_BL` = ***10022.BO3***

#### VAV-03 - CHICA

> `DEMANDA` = ***AV91*** | `VAV` = ***AO7*** | `CM_BL` = ***10022.BO4***

### PLENUM 5

#### VAV-01 - CHICA

> `DEMANDA` = ***AV92*** | `VAV` = ***AO8*** | `CM_BL` = ***10022.BO5***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV93*** | `VAV` = ***AO9*** | `CM_BL` = ***10022.BO6***

### PLENUM 6

#### VAV-01 - GRANDE

> `DEMANDA` = ***AV94*** | `VAV` = ***AO10*** | `CM_BL` = ***10022.BO7***

#### VAV-02 - MEDIANA

> `DEMANDA` = ***AV95*** | `VAV` = ***AO11*** | `CM_BL` = ***10022.BO8***

### PLENUM 7R

#### VAV-01 - CHICA

> `DEMANDA` = ***AV96*** | `VAV` = ***AO12*** | `CM_BL` = ***10022.BO9***

#### VAV-02 - GRANDE

> `DEMANDA` = ***AV97*** | `VAV` = ***AO13*** | `CM_BL` = ***10022.BO10***