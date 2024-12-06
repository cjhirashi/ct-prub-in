# PRG2_VAVS

- **CONTROLADOR:** Cuarto de Pruebas 1 - ID 10021
- **DESCRIPCIÓN:** El programa controla las compuertas de un sistema de VAVs (Variable Air Volume) distribuidas en múltiples plenums. Monitorea las demandas de ventilación de cada VAV y ajusta la apertura de las compuertas en función de parámetros predefinidos para mantener un flujo de aire óptimo. La activación de los VAVs y los estados de las compuertas se gestionan con intervalos de sincronización para asegurar un control eficiente y equilibrado del sistema.
- **VERSIÓN:** 2.0.0
- **AUTOR:** Carlos Jiménez Hirashi - @cjhirashi

---

# Proposito general

El propósito del programa es gestionar el control de las compuertas de las VAV en diferentes plenums (espacios de distribución de aire) de un sistema HVAC. Cada plenum contiene una o más VAVs con diferentes tamaños (mediana, grande, chica). El control se basa en la "demanda" de cada VAV y los parámetros definidos, como el umbral de apertura (P_APER) y un intervalo de sincronización (SINC).

---

# Variables de Control del Sistema de VAVs

## Plenum 1
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-------------------------------|--------------|--------------------------------------------|
| **AV85**                      | *N/A*        | Demanda de ventilación para VAV 01 - Mediana |
| **AO1**                       | *N/A*        | Apertura de compuerta para VAV 01 - Mediana |
| **BO14**                      | *N/A*        | Estado del bloque de control para VAV 01 - Mediana |
| **AV86**                      | *N/A*        | Demanda de ventilación para VAV 02 - Grande  |
| **AO2**                       | *N/A*        | Apertura de compuerta para VAV 02 - Grande  |
| **BO15**                      | *N/A*        | Estado del bloque de control para VAV 02 - Grande  |
| **AV67**                      | *N/A*        | Demanda de ventilación para VAV 03 - Chica   |
| **AO21**                      | *N/A*        | Apertura de compuerta para VAV 03 - Chica   |
| **BO22**                      | *N/A*        | Estado del bloque de control para VAV 03 - Chica |

## Plenum 2
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-------------------------------|--------------|--------------------------------------------|
| **AV87**                      | *N/A*        | Demanda de ventilación para VAV 01 - Mediana |
| **AO3**                       | *N/A*        | Apertura de compuerta para VAV 01 - Mediana |
| **BO16**                      | *N/A*        | Estado del bloque de control para VAV 01 - Mediana |
| **AV88**                      | *N/A*        | Demanda de ventilación para VAV 02 - Grande  |
| **AO4**                       | *N/A*        | Apertura de compuerta para VAV 02 - Grande  |
| **10022.BO1**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 02 - Grande |

## Plenum 3
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-------------------------------|--------------|--------------------------------------------|
| **AV68**                      | *N/A*        | Demanda de ventilación para VAV 01 - Grande |
| **AO23**                      | *N/A*        | Apertura de compuerta para VAV 01 - Grande |
| **BO24**                      | *N/A*        | Estado del bloque de control para VAV 01 - Grande |

## Plenum 4
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-------------------------------|--------------|--------------------------------------------|
| **AV89**                      | *N/A*        | Demanda de ventilación para VAV 01 - Mediana |
| **AO5**                       | *N/A*        | Apertura de compuerta para VAV 01 - Mediana |
| **10022.BO2**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 01 - Mediana |
| **AV90**                      | *N/A*        | Demanda de ventilación para VAV 02 - Grande  |
| **AO6**                       | *N/A*        | Apertura de compuerta para VAV 02 - Grande  |
| **10022.BO3**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 02 - Grande |
| **AV91**                      | *N/A*        | Demanda de ventilación para VAV 03 - Chica   |
| **AO7**                       | *N/A*        | Apertura de compuerta para VAV 03 - Chica   |
| **10022.BO4**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 03 - Chica |

## Plenum 5
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-------------------------------|--------------|--------------------------------------------|
| **AV92**                      | *N/A*        | Demanda de ventilación para VAV 01 - Chica  |
| **AO8**                       | *N/A*        | Apertura de compuerta para VAV 01 - Chica  |
| **10022.BO5**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 01 - Chica |
| **AV93**                      | *N/A*        | Demanda de ventilación para VAV 02 - Grande  |
| **AO9**                       | *N/A*        | Apertura de compuerta para VAV 02 - Grande  |
| **10022.BO6**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 02 - Grande |

## Plenum 6
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-------------------------------|--------------|--------------------------------------------|
| **AV94**                      | *N/A*        | Demanda de ventilación para VAV 01 - Grande |
| **AO10**                      | *N/A*        | Apertura de compuerta para VAV 01 - Grande |
| **10022.BO7**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 01 - Grande |
| **AV95**                      | *N/A*        | Demanda de ventilación para VAV 02 - Mediana |
| **AO11**                      | *N/A*        | Apertura de compuerta para VAV 02 - Mediana |
| **10022.BO8**                 | *N/A*        | Estado sincronizado del bloque de control para VAV 02 - Mediana |

## Plenum R7
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-------------------------------|--------------|--------------------------------------------|
| **AV96**                      | *N/A*        | Demanda de ventilación para VAV 01 - Chica  |
| **AO12**                      | *N/A*        | Apertura de compuerta para VAV 01 - Chica  |
| **BO17**                      | *N/A*        | Estado del bloque de control para VAV 01 - Chica |
| **AV97**                      | *N/A*        | Demanda de ventilación para VAV 02 - Grande  |
| **AO13**                      | *N/A*        | Apertura de compuerta para VAV 02 - Grande  |
| **BO18**                      | *N/A*        | Estado del bloque de control para VAV 02 - Grande |

---

# Variables Locales

1. **P_APER**  
   - ***DESCRIPCIÓN:*** Punto de apertura mínimo para la activación de las cajas VAV. Define el valor de demanda a partir del cual se activa un VAV.  
   - ***UNIDADES:*** N/A

2. **SINC**  
   - ***DESCRIPCIÓN:*** Intervalo de sincronización utilizado para condicionales que requieren control a intervalos específicos.  
   - ***UNIDADES:*** N/A

3. **DEMANDA**  
   - ***DESCRIPCIÓN:*** Variable que recibe el valor de demanda de cada VAV según las lecturas de los sensores (identificados como AVxx).  
   - ***UNIDADES:*** N/A

4. **VAV**  
   - ***DESCRIPCIÓN:*** Valor de apertura de la compuerta del VAV en función de la demanda.  
   - ***UNIDADES:*** N/A

5. **CM_BL**  
   - ***DESCRIPCIÓN:*** Indicador binario del estado de control de la compuerta. Se activa (1) o desactiva (0) según el estado de la demanda.  
   - ***UNIDADES:*** N/A

6. **ACTIV**  
   - ***DESCRIPCIÓN:*** Indicador de activación de la caja VAV. Se activa (1) si la demanda supera el punto de apertura mínimo (`P_APER`), y se desactiva (0) si la demanda es menor a 1.  
   - ***UNIDADES:*** N/A

---

# Lógica de Control del Programa

## Paso a Paso

1. **Inicialización de Variables Locales**
   - Se declaran las siguientes variables locales:
     - `P_APER`: Punto de apertura mínimo para la activación de las cajas VAV, con un valor inicial de 5.
     - `SINC`: Intervalo de sincronización utilizado en condicionales específicos, con un valor inicial de 10.

2. **Estructuración del Programa por *Plenums***
   - El programa está organizado en secciones denominadas *Plenums*, cada uno de los cuales agrupa varios VAVs por tamaño (Mediana, Grande o Chica).

3. **Asignación de Demanda a Cada VAV**
   - Para cada VAV dentro de un *Plenum*, se asigna un valor de demanda proveniente de un punto de control específico (`AVxx`).
   - La variable `DEMANDA` toma el valor de `AVxx`, que representa el nivel de demanda de ventilación para ese VAV en particular.

4. **Lógica de Activación de la Caja VAV**
   - **Condiciones de Activación:**
     - Si `DEMANDA` es mayor que `P_APER`, se activa el VAV (`ACTIV = 1`).
     - Si `DEMANDA` es menor a 1, el VAV se desactiva (`ACTIV = 0`).

5. **Control de Compuertas**
   - Según el estado de activación (`ACTIV`), se controla la apertura de las compuertas de los VAVs:
     - **VAV Activo (`ACTIV = 1`):**
       - La variable `VAV` toma el valor de `DEMANDA`.
       - La variable de control del bloque (`CM_BL`) se establece en 1.
     - **VAV Inactivo (`ACTIV = 0`):**
       - La variable `VAV` se establece en 0, cerrando la compuerta.
       - La variable de control del bloque (`CM_BL`) se establece en 0.

6. **Asignación de Puntos de Control**
   - Se asignan los valores calculados de apertura (`VAV`) y de control de bloque (`CM_BL`) a los puntos de control específicos:
     - `AOxx` se utiliza para controlar la apertura de las compuertas de los VAVs.
     - `BOxx` se utiliza para el estado del bloque de control de las compuertas.

7. **Sincronización de Estados en Plenums Específicos (Variables de control remotas)**
   - En algunos *Plenums*, se requiere una sincronización periódica:
     - Se verifica la condición `IF INTERVAL(SINC)` para sincronizar los estados de los bloques de control (`CM_BL`).
     - Si la condición se cumple, se asignan los valores de `CM_BL` a puntos de control externos (`10022.BOx`).

---

## Resumen de la Lógica de Control

El programa gestiona un sistema de VAVs distribuidos en múltiples *Plenums*. Cada VAV recibe una demanda de ventilación (`DEMANDA`), que se compara con un punto mínimo de apertura (`P_APER`). Según el resultado, se activa o desactiva el VAV y se ajusta la apertura de la compuerta en consecuencia. Los valores de apertura y de control se asignan a puntos de salida específicos para el control de las compuertas y los bloques. En algunos *Plenums*, se sincronizan los estados de las compuertas a intervalos definidos por `SINC`.

Esta lógica permite un control eficiente y modular del flujo de aire, garantizando que cada VAV se gestione de manera individual y sincronizada cuando sea necesario.
