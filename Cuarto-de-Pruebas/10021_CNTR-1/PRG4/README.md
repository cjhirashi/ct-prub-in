# PRG4_DEMANDA

- **CONTROLADOR:** Cuarto de pruebas 1 - ID 10021

- **DESCRIPCIÓN:** Este programa controla la demanda de plenos en un sistema HVAC mediante un algoritmo PI (Proporcional-Integral) para gestionar diferentes secciones del sistema, ajustando la demanda en función de parámetros establecidos y límites de operación. El programa asegura el funcionamiento adecuado y eficiente de cada caja de ventilación y sus respectivos retornos.

- **VERSIÓN:** 2.0.0

- **AUTOR:** Carlos Jiménez Hirashi - @cjhirashi

---

# Variables de Control en PRG4_DEMANDA

## Sistema: Caja Grande (VG)
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                        |
|-----------------|---------------|---------------------------------------|
| **BV9**         | *"N/A"*       | Permiso de operación para Caja Grande |
| **AV69**        | *"%"*         | Componente proporcional (P) de Caja Grande |
| **AV70**        | *"%"*         | Componente integral (I) de Caja Grande |
| **AV82**        | *"%"*         | Demanda total calculada para Caja Grande |
| **AV98**        | *"N/A"*       | Valor de medición de flujo de Caja Grande |
| **AV107**       | *"N/A"*       | Setpoint de flujo para Caja Grande    |

## Sistema: Caja Mediana (VM)
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                        |
|-----------------|---------------|---------------------------------------|
| **BV10**        | *"N/A"*       | Permiso de operación para Caja Mediana |
| **AV71**        | *"%"*         | Componente proporcional (P) de Caja Mediana |
| **AV72**        | *"%"*         | Componente integral (I) de Caja Mediana |
| **AV83**        | *"%"*         | Demanda total calculada para Caja Mediana |
| **AV99**        | *"N/A"*       | Valor de medición de flujo de Caja Mediana |
| **AV108**       | *"N/A"*       | Setpoint de flujo para Caja Mediana   |

## Sistema: Caja Chica (VC)
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                        |
|-----------------|---------------|---------------------------------------|
| **BV11**        | *"N/A"*       | Permiso de operación para Caja Chica  |
| **AV73**        | *"%"*         | Componente proporcional (P) de Caja Chica |
| **AV74**        | *"%"*         | Componente integral (I) de Caja Chica |
| **AV84**        | *"%"*         | Demanda total calculada para Caja Chica |
| **AV100**       | *"N/A"*       | Valor de medición de flujo de Caja Chica |
| **AV109**       | *"N/A"*       | Setpoint de flujo para Caja Chica     |

## Sistema: Caja Grande Retorno (VGR)
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-----------------|---------------|--------------------------------------------|
| **BV35**        | *"N/A"*       | Permiso de operación para Caja Grande Retorno |
| **AV69**        | *"%"*         | Componente proporcional (P) de Caja Grande Retorno |
| **AV70**        | *"%"*         | Componente integral (I) de Caja Grande Retorno |
| **AV80**        | *"%"*         | Demanda total calculada para Caja Grande Retorno |
| **AV102**       | *"N/A"*       | Valor de medición de flujo de Caja Grande Retorno |
| **AV110**       | *"N/A"*       | Setpoint de flujo para Caja Grande Retorno |

## Sistema: Caja Chica Retorno (VCR)
| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                             |
|-----------------|---------------|--------------------------------------------|
| **BV36**        | *"N/A"*       | Permiso de operación para Caja Chica Retorno |
| **AV73**        | *"%"*         | Componente proporcional (P) de Caja Chica Retorno |
| **AV74**        | *"%"*         | Componente integral (I) de Caja Chica Retorno |
| **AV81**        | *"%"*         | Demanda total calculada para Caja Chica Retorno |
| **AV103**       | *"N/A"*       | Valor de medición de flujo de Caja Chica Retorno |
| **AV111**       | *"N/A"*       | Setpoint de flujo para Caja Chica Retorno  |

---

# Variables Locales en PRG4_DEMANDA

1. **TM**  
   - ***DESCRIPCIÓN:*** Tiempo entre escaneos del controlador.  
   - ***UNIDADES:*** Segundos (s).

2. **T_VG**  
   - ***DESCRIPCIÓN:*** Contador de tiempo para Caja Grande.  
   - ***UNIDADES:*** Segundos (s).

3. **T_VM**  
   - ***DESCRIPCIÓN:*** Contador de tiempo para Caja Mediana.  
   - ***UNIDADES:*** Segundos (s).

4. **T_VC**  
   - ***DESCRIPCIÓN:*** Contador de tiempo para Caja Chica.  
   - ***UNIDADES:*** Segundos (s).

5. **T_VGR**  
   - ***DESCRIPCIÓN:*** Contador de tiempo para Caja Grande Retorno.  
   - ***UNIDADES:*** Segundos (s).

6. **T_VCR**  
   - ***DESCRIPCIÓN:*** Contador de tiempo para Caja Chica Retorno.  
   - ***UNIDADES:*** Segundos (s).

7. **SS_CP**  
   - ***DESCRIPCIÓN:*** Estado del sistema de control principal (activo o inactivo).  
   - ***UNIDADES:*** N/A.

8. **L_MAX**  
   - ***DESCRIPCIÓN:*** Límite máximo para las demandas de sistema.  
   - ***UNIDADES:*** N/A.

9. **L_MIN**  
   - ***DESCRIPCIÓN:*** Límite mínimo para las demandas de sistema.  
   - ***UNIDADES:*** N/A.

10. **PERM_VG**  
    - ***DESCRIPCIÓN:*** Permisivo para la operación de Caja Grande.  
    - ***UNIDADES:*** N/A.

11. **PERM_VM**  
    - ***DESCRIPCIÓN:*** Permisivo para la operación de Caja Mediana.  
    - ***UNIDADES:*** N/A.

12. **PERM_VC**  
    - ***DESCRIPCIÓN:*** Permisivo para la operación de Caja Chica.  
    - ***UNIDADES:*** N/A.

13. **PERM_VGR**  
    - ***DESCRIPCIÓN:*** Permisivo para la operación de Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

14. **PERM_VCR**  
    - ***DESCRIPCIÓN:*** Permisivo para la operación de Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

15. **Q_VG**  
    - ***DESCRIPCIÓN:*** Flujo medido en Caja Grande.  
    - ***UNIDADES:*** N/A.

16. **Q_VM**  
    - ***DESCRIPCIÓN:*** Flujo medido en Caja Mediana.  
    - ***UNIDADES:*** N/A.

17. **Q_VC**  
    - ***DESCRIPCIÓN:*** Flujo medido en Caja Chica.  
    - ***UNIDADES:*** N/A.

18. **Q_VGR**  
    - ***DESCRIPCIÓN:*** Flujo medido en Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

19. **Q_VCR**  
    - ***DESCRIPCIÓN:*** Flujo medido en Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

20. **SP_Q_VG**  
    - ***DESCRIPCIÓN:*** Setpoint de flujo en Caja Grande.  
    - ***UNIDADES:*** N/A.

21. **SP_Q_VM**  
    - ***DESCRIPCIÓN:*** Setpoint de flujo en Caja Mediana.  
    - ***UNIDADES:*** N/A.

22. **SP_Q_VC**  
    - ***DESCRIPCIÓN:*** Setpoint de flujo en Caja Chica.  
    - ***UNIDADES:*** N/A.

23. **SP_Q_VGR**  
    - ***DESCRIPCIÓN:*** Setpoint de flujo en Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

24. **SP_Q_VCR**  
    - ***DESCRIPCIÓN:*** Setpoint de flujo en Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

25. **P_VG**  
    - ***DESCRIPCIÓN:*** Constante proporcional para Caja Grande.  
    - ***UNIDADES:*** N/A.

26. **P_VM**  
    - ***DESCRIPCIÓN:*** Constante proporcional para Caja Mediana.  
    - ***UNIDADES:*** N/A.

27. **P_VC**  
    - ***DESCRIPCIÓN:*** Constante proporcional para Caja Chica.  
    - ***UNIDADES:*** N/A.

28. **P_VGR**  
    - ***DESCRIPCIÓN:*** Constante proporcional para Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

29. **P_VCR**  
    - ***DESCRIPCIÓN:*** Constante proporcional para Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

30. **I_VG**  
    - ***DESCRIPCIÓN:*** Constante integral para Caja Grande.  
    - ***UNIDADES:*** N/A.

31. **I_VM**  
    - ***DESCRIPCIÓN:*** Constante integral para Caja Mediana.  
    - ***UNIDADES:*** N/A.

32. **I_VC**  
    - ***DESCRIPCIÓN:*** Constante integral para Caja Chica.  
    - ***UNIDADES:*** N/A.

33. **I_VGR**  
    - ***DESCRIPCIÓN:*** Constante integral para Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

34. **I_VCR**  
    - ***DESCRIPCIÓN:*** Constante integral para Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

35. **ERR_VG**  
    - ***DESCRIPCIÓN:*** Error de flujo medido en Caja Grande.  
    - ***UNIDADES:*** N/A.

36. **ERR_VM**  
    - ***DESCRIPCIÓN:*** Error de flujo medido en Caja Mediana.  
    - ***UNIDADES:*** N/A.

37. **ERR_VC**  
    - ***DESCRIPCIÓN:*** Error de flujo medido en Caja Chica.  
    - ***UNIDADES:*** N/A.

38. **ERR_VGR**  
    - ***DESCRIPCIÓN:*** Error de flujo medido en Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

39. **ERR_VCR**  
    - ***DESCRIPCIÓN:*** Error de flujo medido en Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

40. **PR_VG**  
    - ***DESCRIPCIÓN:*** Resultado proporcional de Caja Grande.  
    - ***UNIDADES:*** N/A.

41. **PR_VM**  
    - ***DESCRIPCIÓN:*** Resultado proporcional de Caja Mediana.  
    - ***UNIDADES:*** N/A.

42. **PR_VC**  
    - ***DESCRIPCIÓN:*** Resultado proporcional de Caja Chica.  
    - ***UNIDADES:*** N/A.

43. **PR_VGR**  
    - ***DESCRIPCIÓN:*** Resultado proporcional de Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

44. **PR_VCR**  
    - ***DESCRIPCIÓN:*** Resultado proporcional de Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

45. **IR_VG**  
    - ***DESCRIPCIÓN:*** Resultado integral de Caja Grande.  
    - ***UNIDADES:*** N/A.

46. **IR_VM**  
    - ***DESCRIPCIÓN:*** Resultado integral de Caja Mediana.  
    - ***UNIDADES:*** N/A.

47. **IR_VC**  
    - ***DESCRIPCIÓN:*** Resultado integral de Caja Chica.  
    - ***UNIDADES:*** N/A.

48. **IR_VGR**  
    - ***DESCRIPCIÓN:*** Resultado integral de Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

49. **IR_VCR**  
    - ***DESCRIPCIÓN:*** Resultado integral de Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

50. **IS_VG**  
    - ***DESCRIPCIÓN:*** Acumulador de la acción integral para Caja Grande.  
    - ***UNIDADES:*** N/A.

51. **IS_VM**  
    - ***DESCRIPCIÓN:*** Acumulador de la acción integral para Caja Mediana.  
    - ***UNIDADES:*** N/A.

52. **IS_VC**  
    - ***DESCRIPCIÓN:*** Acumulador de la acción integral para Caja Chica.  
    - ***UNIDADES:*** N/A.

53. **IS_VGR**  
    - ***DESCRIPCIÓN:*** Acumulador de la acción integral para Caja Grande Retorno.  
    - ***UNIDADES:*** N/A.

54. **IS_VCR**  
    - ***DESCRIPCIÓN:*** Acumulador de la acción integral para Caja Chica Retorno.  
    - ***UNIDADES:*** N/A.

55. **DM_VG**  
    - ***DESCRIPCIÓN:*** Demanda de sistema para Caja Grande.  
    - ***UNIDADES:*** N/A.

56. **DM_VM**  
    - ***DESCRIPCIÓN:*** Demanda de sistema para Caja Med

---

# Lógica de Control del Programa PRG4_DEMANDA

## Paso a Paso de la Lógica de Control

1. **Inicialización de Contadores y Parámetros del Sistema**
   - Se define el tiempo entre escaneos (`TM`) y se utilizan contadores de tiempo específicos para cada caja (`T_VG`, `T_VM`, `T_VC`, `T_VGR`, `T_VCR`), que incrementan su valor en cada ciclo del programa.
   - Se configuran límites de operación (`L_MAX = 100`, `L_MIN = 6`) para establecer los valores máximo y mínimo de demanda permitida.
   - Se definen los permisos de operación (`PERM_VG`, `PERM_VM`, `PERM_VC`, `PERM_VGR`, `PERM_VCR`) para cada caja de control y su retorno, los cuales se utilizarán para habilitar o deshabilitar la lógica de control en cada sección.

2. **Control PI para Cada Caja de Ventilación**
   - **Condición de Habilitación:** Para cada caja, se verifica si el sistema principal de control está activo (`SS_CP = 1`) y si la caja está permitida (`PERM_* = 1`).
   - **Cálculo del Error:** Se determina la diferencia entre el valor medido (`Q_*`) y el setpoint (`SP_Q_*`), y se multiplica por -1 para obtener el error del sistema (`ERR_*`).
   - **Componente Proporcional (`PR_*`):** Se calcula como el porcentaje del error respecto al setpoint, ajustado con la constante proporcional (`P_*`).
   - **Componente Integral (`IR_*`):** Se calcula la parte integral basada en el error y el setpoint, multiplicada por la constante integral (`I_*`). Este componente se acumula en un integrador (`IS_*`) si ha transcurrido un tiempo determinado (`T_* > 1`), y se resetea el contador de tiempo (`T_* = 0`).
   - **Ajuste del Valor Integral:** El valor integral acumulado (`IS_*`) se ajusta para mantenerse dentro de un rango establecido por los límites `L_MIN - 10` y `L_MAX + 10`.
   - **Cálculo de la Demanda Total (`DM_*`):** La demanda se obtiene como la suma de la componente proporcional (`PR_*`) y la componente integral ajustada (`IS_*`). Se limita la demanda final entre los valores `L_MIN` y `L_MAX`.

3. **Deshabilitación de Demanda**
   - Si la condición de habilitación no se cumple (es decir, `SS_CP` o `PERM_*` son igual a 0), todas las variables de control (`PR_*`, `IR_*`, `IS_*`, `DM_*`) se asignan a cero.

4. **Asignación de la Demanda Total**
   - La demanda total calculada para cada caja se asigna a una variable de salida correspondiente (`AV82`, `AV83`, `AV84`, `AV80`, `AV81`) para cada caja de ventilación.

5. **Permisos de Operación Activos**
   - Se verifican las condiciones de los permisivos de operación para todas las cajas. Si todos los permisos de las cajas de ventilación (`PERM_VG`, `PERM_VM`, `PERM_VC`) son cero, se activa un permiso global (`BV9@8 = 1`).
   - De manera similar, se verifica si los permisos de las cajas de retorno (`PERM_VGR`, `PERM_VCR`) son cero y se activa un permiso global (`BV35@8 = 1`).

## Resumen

La lógica de control en el programa **PRG4_DEMANDA** se basa en el uso de controladores PI (Proporcional-Integral) para gestionar diferentes cajas de ventilación y sus retornos en un sistema HVAC. Cada caja tiene su propio cálculo de error, proporción e integral, que se combinan para obtener una demanda total que se ajusta dentro de un rango permitido. El programa evalúa condiciones de habilitación para cada caja y ajusta las variables de control en consecuencia. Finalmente, se gestiona un permiso global de operación basado en los estados de los permisivos de cada caja.

El enfoque modular y organizado de la lógica PI permite un control eficiente y estable del sistema de ventilación, garantizando la respuesta adecuada de las cajas de ventilación y sus retornos en función de los setpoints y valores de medición.
