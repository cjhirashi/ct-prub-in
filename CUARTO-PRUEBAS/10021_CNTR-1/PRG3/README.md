# PRG3_PLENUMS

- **CONTROLADOR:** Cuarto Control 1
- **DESCRIPCIÓN:** Programa para gestionar y controlar el flujo de aire en un sistema de múltiples *plenum* mediante el uso de cajas VAV. La lógica del programa asigna caudales, controla las compuertas de las cajas, supervisa la presión en los *plenum* activos y ajusta los límites operativos de cada caja VAV de acuerdo a la demanda y las configuraciones establecidas.
- **VERSIÓN:** 2.0.0
- **AUTOR:** Carlos Jiménez Hirashi - @cjhirashi

---

# Variables de Control del Programa PRG3_PLENUMS

## Sistema de Control de Presión y Caudal

| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                                  |
|-----------------|---------------|-------------------------------------------------|
| **AI18**        | *"WC*         | Caída de presión de Plenum 1, sensor 1.         |
| **10022.AI3**   | *"WC*         | Caída de presión de Plenum 1, sensor 2.         |
| **10022.AI4**   | *"WC*         | Caída de presión de Plenum 2.                   |
| **10022.AI5**   | *"WC*         | Caída de presión de Plenum 4.                   |
| **10022.AI6**   | *"WC*         | Caída de presión de Plenum 5.                   |
| **10022.AI7**   | *"WC*         | Caída de presión de Plenum 6.                   |

## Sistema de Caudales de Aire de Cajas VAV

| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                                   |
|-----------------|---------------|--------------------------------------------------|
| **AV4**         | CFM           | Caudal de aire de Plenum 1, caja mediana.        |
| **AV8**         | CFM           | Caudal de aire de Plenum 1, caja grande.         |
| **AV13**        | CFM           | Caudal de aire de Plenum 2, caja mediana.        |
| **AV17**        | CFM           | Caudal de aire de Plenum 2, caja grande.         |
| **AV22**        | CFM           | Caudal de aire de Plenum 4, caja mediana.        |
| **AV26**        | CFM           | Caudal de aire de Plenum 4, caja grande.         |
| **AV30**        | CFM           | Caudal de aire de Plenum 4, caja chica.          |
| **AV35**        | CFM           | Caudal de aire de Plenum 5, caja chica.          |
| **AV39**        | CFM           | Caudal de aire de Plenum 5, caja grande.         |
| **AV44**        | CFM           | Caudal de aire de Plenum 6, caja grande.         |
| **AV48**        | CFM           | Caudal de aire de Plenum 6, caja mediana.        |
| **AV53**        | CFM           | Caudal de aire de Plenum 7, caja chica.          |
| **AV57**        | CFM           | Caudal de aire de Plenum 7, caja grande.         |
| **AV62**        | CFM           | Caudal de aire de Plenum 1, caja chica.          |
| **AV66**        | CFM           | Caudal de aire de Plenum 3, caja grande.         |

## Sistema de Demanda y Setpoints de Caudal

| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                                   |
|-----------------|---------------|--------------------------------------------------|
| **AV80**        | CFM           | Caudal de aire requerido, caja grande.           |
| **AV81**        | CFM           | Caudal de aire requerido, caja chica.            |
| **AV82**        | CFM           | Demanda de caudal de aire, caja grande.          |
| **AV83**        | CFM           | Demanda de caudal de aire, caja mediana.         |
| **AV84**        | CFM           | Demanda de caudal de aire, caja chica.           |
| **AV107**       | CFM           | Setpoint de caudal de caja grande.               |
| **AV108**       | CFM           | Setpoint de caudal de caja mediana.              |
| **AV109**       | CFM           | Setpoint de caudal de caja chica.                |
| **AV110**       | CFM           | Setpoint de caudal de caja grande, Plenum 7.     |
| **AV111**       | CFM           | Setpoint de caudal de caja chica, Plenum 7.      |
| **AV112**       | CFM           | Caudal mínimo de operación, caja grande.         |
| **AV113**       | CFM           | Caudal máximo de operación, caja grande.         |
| **AV114**       | CFM           | Caudal mínimo de operación, caja mediana.        |
| **AV115**       | CFM           | Caudal máximo de operación, caja mediana.        |
| **AV116**       | CFM           | Caudal mínimo de operación, caja chica.          |
| **AV117**       | CFM           | Caudal máximo de operación, caja chica.          |

## Sistema de Control de Compuertas y Estado de Plenum

| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                                   |
|-----------------|---------------|--------------------------------------------------|
| **BV2**         | Binario       | Estado general de plenum activo.                 |
| **BV3**         | Binario       | Estado de plenum 1.                              |
| **BV4**         | Binario       | Estado de plenum 2.                              |
| **BV5**         | Binario       | Estado de plenum 3.                              |
| **BV6**         | Binario       | Estado de plenum 4.                              |
| **BV7**         | Binario       | Estado de plenum 5.                              |
| **BV8**         | Binario       | Estado de plenum 6.                              |
| **BV9**         | Binario       | Permisivo de operación de caja VAV 1.            |
| **BV10**        | Binario       | Permisivo de operación de caja VAV 2.            |
| **BV11**        | Binario       | Permisivo de operación de caja VAV 3.            |

## Sistema de Caídas de Presión y Variables de Salida

| **ID VARIABLE** | **UNIDADES** | **DESCRIPCIÓN**                                   |
|-----------------|---------------|--------------------------------------------------|
| **AV98**        | CFM           | Caudal de aire activo, caja grande.              |
| **AV99**        | CFM           | Caudal de aire activo, caja mediana.             |
| **AV100**       | CFM           | Caudal de aire activo, caja chica.               |
| **AV101**       | CFM           | Suma total de caudal de aire activo.             |
| **AV105**       | *"WC*         | Caída de presión en el plenum activo, sensor 1.  |
| **AV106**       | *"WC*         | Caída de presión en el plenum activo, sensor 2.  |

---

# Listado de Variables Locales del Programa PRG3_PLENUMS

1. **P1_VG_QMAX**  
   - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja grande en Plenum 1.  
   - ***UNIDADES:*** CFM.

2. **P1_VM_QMAX**  
   - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja mediana en Plenum 1.  
   - ***UNIDADES:*** CFM.

3. **P1_VC_QMAX**  
   - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja chica en Plenum 1.  
   - ***UNIDADES:*** CFM.

4. **P1_VG_QMIN**  
   - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja grande en Plenum 1.  
   - ***UNIDADES:*** CFM.

5. **P1_VM_QMIN**  
   - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja mediana en Plenum 1.  
   - ***UNIDADES:*** CFM.

6. **P1_VC_QMIN**  
   - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja chica en Plenum 1.  
   - ***UNIDADES:*** CFM.

7. **P2_VG_QMAX**  
   - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja grande en Plenum 2.  
   - ***UNIDADES:*** CFM.

8. **P2_VM_QMAX**  
   - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja mediana en Plenum 2.  
   - ***UNIDADES:*** CFM.

9. **P2_VG_QMIN**  
   - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja grande en Plenum 2.  
   - ***UNIDADES:*** CFM.

10. **P2_VM_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja mediana en Plenum 2.  
    - ***UNIDADES:*** CFM.

11. **P3_VG_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja grande en Plenum 3.  
    - ***UNIDADES:*** CFM.

12. **P3_VG_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja grande en Plenum 3.  
    - ***UNIDADES:*** CFM.

13. **P4_VG_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja grande en Plenum 4.  
    - ***UNIDADES:*** CFM.

14. **P4_VM_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja mediana en Plenum 4.  
    - ***UNIDADES:*** CFM.

15. **P4_VC_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja chica en Plenum 4.  
    - ***UNIDADES:*** CFM.

16. **P4_VG_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja grande en Plenum 4.  
    - ***UNIDADES:*** CFM.

17. **P4_VM_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja mediana en Plenum 4.  
    - ***UNIDADES:*** CFM.

18. **P4_VC_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja chica en Plenum 4.  
    - ***UNIDADES:*** CFM.

19. **P5_VG_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja grande en Plenum 5.  
    - ***UNIDADES:*** CFM.

20. **P5_VC_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja chica en Plenum 5.  
    - ***UNIDADES:*** CFM.

21. **P5_VG_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja grande en Plenum 5.  
    - ***UNIDADES:*** CFM.

22. **P5_VC_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja chica en Plenum 5.  
    - ***UNIDADES:*** CFM.

23. **P6_VG_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja grande en Plenum 6.  
    - ***UNIDADES:*** CFM.

24. **P6_VM_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja mediana en Plenum 6.  
    - ***UNIDADES:*** CFM.

25. **P6_VG_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja grande en Plenum 6.  
    - ***UNIDADES:*** CFM.

26. **P6_VM_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja mediana en Plenum 6.  
    - ***UNIDADES:*** CFM.

27. **P7_VG_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja grande en Plenum 7.  
    - ***UNIDADES:*** CFM.

28. **P7_VC_QMAX**  
    - ***DESCRIPCIÓN:*** Caudal máximo permitido para caja chica en Plenum 7.  
    - ***UNIDADES:*** CFM.

29. **P7_VG_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja grande en Plenum 7.  
    - ***UNIDADES:*** CFM.

30. **P7_VC_QMIN**  
    - ***DESCRIPCIÓN:*** Caudal mínimo permitido para caja chica en Plenum 7.  
    - ***UNIDADES:*** CFM.

31. **PLENUM**  
    - ***DESCRIPCIÓN:*** Identificador del plenum activo en el sistema.  
    - ***UNIDADES:*** Sin unidades.

32. **SS_CP**  
    - ***DESCRIPCIÓN:*** Selector del sistema de control principal (activo/inactivo).  
    - ***UNIDADES:*** Sin unidades.

33. **SP_Q_VG**  
    - ***DESCRIPCIÓN:*** Setpoint de caudal para caja grande.  
    - ***UNIDADES:*** CFM.

34. **SP_Q_VM**  
    - ***DESCRIPCIÓN:*** Setpoint de caudal para caja mediana.  
    - ***UNIDADES:*** CFM.

35. **SP_Q_VC**  
    - ***DESCRIPCIÓN:*** Setpoint de caudal para caja chica.  
    - ***UNIDADES:*** CFM.

36. **SP_Q_VGR**  
    - ***DESCRIPCIÓN:*** Setpoint de caudal para caja grande, Plenum 7.  
    - ***UNIDADES:*** CFM.

37. **SP_Q_VCR**  
    - ***DESCRIPCIÓN:*** Setpoint de caudal para caja chica, Plenum 7.  
    - ***UNIDADES:*** CFM.

38. **DP_1**  
    - ***DESCRIPCIÓN:*** Variable de presión diferencial en el plenum activo, sensor 1.  
    - ***UNIDADES:*** *"WC.*

39. **DP_2**  
    - ***DESCRIPCIÓN:*** Variable de presión diferencial en el plenum activo, sensor 2.  
    - ***UNIDADES:*** *"WC.*

40. **ST_P1**  
    - ***DESCRIPCIÓN:*** Estado de operación de Plenum 1.  
    - ***UNIDADES:*** Sin unidades.

41. **ST_P2**  
    - ***DESCRIPCIÓN:*** Estado de operación de Plenum 2.  
    - ***UNIDADES:*** Sin unidades.

42. **ST_P3**  
    - ***DESCRIPCIÓN:*** Estado de operación de Plenum 3.  
    - ***UNIDADES:*** Sin unidades.

43. **ST_P4**  
    - ***DESCRIPCIÓN:*** Estado de operación de Plenum 4.  
    - ***UNIDADES:*** Sin unidades.

44. **ST_P5**  
    - ***DESCRIPCIÓN:*** Estado de operación de Plenum 5.  
    - ***UNIDADES:*** Sin unidades.

45. **ST_P6**  
    - ***DESCRIPCIÓN:*** Estado de operación de Plenum 6.  
    - ***UNIDADES:*** Sin unidades.

46. **ST_CP**  
    - ***DESCRIPCIÓN:*** Estado de operación general del sistema de *plenum*.  
    - ***UNIDADES:*** Sin unidades.

---

# Lógica de Control del Programa PRG3_PLENUMS

## Paso 1: Limitación de Variables

1. **Límite de Setpoints para Cajas VAV**:  
   Se verifica si los *setpoints* de caudal (`SP_Q_VG`, `SP_Q_VM`, `SP_Q_VC`, `SP_Q_VGR`, `SP_Q_VCR`) están dentro de los rangos permitidos. Si algún valor se encuentra fuera del límite, se ajusta al valor máximo o mínimo correspondiente.

2. **Límite de Selector de Plenum Activo**:  
   Se valida que la variable `PLENUM` esté dentro del rango de 1 a 6. Si el valor está fuera de estos límites, se ajusta al valor mínimo o máximo permitido.

## Paso 2: Sistema Activo - Asignación de Parámetros de Control a Plenum Activo

1. **Asignación de Parámetros por Plenum**:  
   Para cada *plenum*, si el sistema de control (`SS_CP`) está activo y el *plenum* actual es el seleccionado (`PLENUM`), se realizan las siguientes acciones:

   - **Asignación de Presión de Plenum**:  
     Se asignan los valores de presión diferencial (`DP_1` y `DP_2`) correspondientes al *plenum* activo.

   - **Bloqueo de Permisivos de Operación**:  
     Se gestionan los permisos de operación mediante variables binarias (`BV9`, `BV10`, `BV11`), estableciéndolas según los requerimientos del *plenum* activo.

   - **Límite de Caudal por Tamaño de Caja**:  
     Se asignan los límites de caudal (`MAX_VG`, `MIN_VG`, `MAX_VM`, `MIN_VM`, `MAX_VC`, `MIN_VC`) para las cajas del *plenum* activo.

   - **Asignación de Caudal de Aire**:  
     Se establecen los valores de caudal (`Q_GR`, `Q_MD`, `Q_CH`) según los flujos de aire del *plenum* activo.

   - **Asignación de Demanda de Aire**:  
     Se asignan los caudales demandados para las cajas del *plenum* activo.

   - **Estado del Plenum Activo**:  
     Se establece la variable de estado correspondiente al *plenum* activo (`ST_P1`, `ST_P2`, `ST_P3`, `ST_P4`, `ST_P5`, `ST_P6`) en 1, y el resto en 0.

## Paso 3: Sistema Inactivo - Restablecimiento de Parámetros de Control

1. **Restablecimiento de Compuertas de Cajas VAV**:  
   Se establecen todas las variables de apertura de compuertas de cada *plenum* al 100%, indicando un estado de inactividad.

2. **Restablecimiento de Estados de Operación de Plenum**:  
   Se restablecen todas las variables de estado (`ST_P1` a `ST_P6`) a 0, indicando que no hay *plenum* activo.

3. **Desbloqueo de Permisivos de Operación**:  
   Se desactivan las variables binarias (`BV9`, `BV10`, `BV11`), deshabilitando los permisos de operación para las cajas VAV.

## Paso 4: Estado de Operación General

- Se calcula el estado general de operación del sistema (`ST_CP`) como el valor máximo de los estados de todos los *plenum*, lo cual indica si algún *plenum* se encuentra activo.

## Resumen de la Lógica de Control

La lógica de control del programa PRG3_PLENUMS se centra en la gestión de un sistema de control de flujo de aire mediante *plenum* y cajas VAV. El sistema valida y ajusta los límites de operación, selecciona un *plenum* activo, asigna los caudales y demanda de aire, y monitoriza las caídas de presión. Cuando el sistema está activo, asigna parámetros específicos al *plenum* seleccionado, y cuando se desactiva, restablece todos los valores a un estado de inactividad. La lógica garantiza la operación segura y eficiente del sistema ajustando caudales y monitoreando estados.

