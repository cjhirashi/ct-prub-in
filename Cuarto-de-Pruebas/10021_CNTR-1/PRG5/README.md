# PRG5_UMA

- **CONTROLADOR:** Cuarto Control 1
- **DESCRIPCIÓN:** El programa PRG5_UMA se encarga del control periódico de una Unidad de Manejo de Aire (UMA), sincronizando datos de estado y configurando puntos específicos de un controlador BACnet. Ejecuta tareas de monitoreo y control condicionales para asegurar el correcto funcionamiento de la UMA en intervalos de tiempo predefinidos.
- **VERSIÓN:** 2.0.0
- **AUTOR:** Carlos Jimenez Hirashi - @cjhirashi

---

# Variables de Control por Sistema

## Sistema 10003

| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                            |
|-----------------|---------------|-------------------------------------------|
| **10003.BV3**   | *N/A*         | Variable binaria utilizada para sincronización de estado. |
| **10003.AV4**   | *N/A*         | Variable analógica para sincronización de datos de control. |
| **10003.AV8**   | *N/A*         | Variable analógica para la transferencia de datos de monitoreo. |
| **10003.MSV1@7**| *N/A*         | Punto de valor múltiple utilizado para el control condicional de la UMA. |

## Variables Locales del Sistema

| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                            |
|-----------------|---------------|-------------------------------------------|
| **BV1**         | *N/A*         | Variable binaria local para habilitar o deshabilitar el control de la UMA. |
| **BV2**         | *N/A*         | Variable binaria utilizada para reflejar el estado del sistema externo. |
| **AV118**       | *N/A*         | Variable analógica que almacena datos externos para sincronización. |
| **AV119**       | *N/A*         | Variable analógica que almacena datos adicionales de monitoreo. |

---

# Variables Locales

1. **SS_CP**  
   - ***DESCRIPCIÓN:*** Variable utilizada para el almacenamiento o monitoreo de un estado o setpoint del sistema de control.  
   - ***UNIDADES:*** No especificadas.

2. **ST_UMA**  
   - ***DESCRIPCIÓN:*** Variable que posiblemente almacena el estado operativo de la Unidad de Manejo de Aire (UMA).  
   - ***UNIDADES:*** No especificadas.

---

# Lógica de Control del Programa

## Paso a Paso

1. **Sincronización periódica**  
   La lógica principal del programa se ejecuta en intervalos de 5 segundos. Se utiliza una instrucción de tiempo (`IF INTERVAL(00:00:05)`) para asegurar que el bloque de código se ejecute periódicamente, permitiendo la actualización de los puntos de control de manera constante.

2. **Actualización de variables binarias y analógicas**  
   Dentro del bloque de sincronización, el programa realiza las siguientes asignaciones:

   - `BV2` recibe el valor actual de `10003.BV3`, estableciendo así una sincronización entre una variable binaria local y un punto binario del controlador con ID 10003.
   - La variable `10003.AV4` se actualiza con el valor de `AV118`, reflejando datos analógicos externos en el sistema principal.
   - De manera similar, `10003.AV8` se actualiza con el valor de `AV119`, completando la sincronización de variables analógicas.

3. **Evaluación del estado de control**  
   El programa verifica el valor de la variable binaria `BV1` para decidir qué acción tomar:

   - **Si `BV1` es igual a 1**:  
     Asigna el valor `4` al punto `10003.MSV1@7`, indicando probablemente un estado de operación o control específico para la Unidad de Manejo de Aire (UMA).  
   - **Si `BV1` no es igual a 1**:  
     Ejecuta la instrucción `RLQ` sobre `10003.MSV1@7`. Este comando puede estar diseñado para restablecer, desactivar o liberar el punto `MSV1@7`.

## Resumen de la Lógica de Control

El programa realiza un ciclo de sincronización cada 5 segundos para mantener actualizadas las variables de control entre los sistemas locales y los puntos del controlador `10003`. Se verifica el estado de una variable binaria (`BV1`) para determinar si se debe asignar un valor específico a un punto de valor múltiple (`10003.MSV1@7`) o restablecerlo. En general, el código se encarga de mantener un flujo de datos continuo y de activar condiciones específicas de la UMA según el estado del sistema.

