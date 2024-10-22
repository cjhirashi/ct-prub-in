# PRG1_CALIBRACION

- **CONTROLADOR:** Cuarto de pruebas 2 - ID 10022

- **DESCRIPCIÓN:** El programa gestiona un sistema de calibración de caudales en un entorno HVAC, permitiendo el ajuste y control de las aperturas de compuertas y la toma de muestras de caudales. Utiliza variables de activación y parámetros de calibración para asegurar que los sistemas de ventilación operen con eficiencia, ajustando los multiplicadores y compensaciones necesarias en función de las mediciones obtenidas.

- **VERSIÓN:** 2.0.0

- **AUTOR:** Carlos Jiménez Hirashi - @cjhirashi

---

# Listado de Variables de Control

## Variables de Control del Sistema de Calibración

| ID VARIABLE | UNIDADES | DESCRIPCIÓN |
|-------------|-----------|-------------|
| **AV1**     | *Sin unidades* | Valor de medición para caudal P1_VM. |
| **AV2**     | *Sin unidades* | Multiplicador de calibración para P1_VM. |
| **AV3**     | *Sin unidades* | Offset de calibración para P1_VM. |
| **AV5**     | *Sin unidades* | Valor de medición para caudal P1_VG. |
| **AV6**     | *Sin unidades* | Multiplicador de calibración para P1_VG. |
| **AV7**     | *Sin unidades* | Offset de calibración para P1_VG. |
| **AV8**     | *Sin unidades* | Número de muestras para calibración. |
| **AV9**     | *Segundos* | Tiempo entre muestras para calibración. |
| **AV10**    | *Sin unidades* | Valor de medición para caudal P2_VM. |
| **AV11**    | *Sin unidades* | Multiplicador de calibración para P2_VM. |
| **AV12**    | *Segundos* | Tiempo máximo de toma de muestras. |
| **AV13**    | *Segundos* | Tiempo mínimo de toma de muestras. |
| **AV14**    | *Sin unidades* | Factor multiplicador de calibración. |
| **AV15**    | *Sin unidades* | Offset de calibración. |
| **AV16**    | *Sin unidades* | Valor de medición para caudal P3_VG. |
| **AV17**    | *Sin unidades* | Offset de medición para P3_VG. |
| **AV18**    | *Sin unidades* | Valor máximo del sistema. |
| **AV19**    | *Sin unidades* | Valor mínimo del sistema. |
| **AV20**    | *Porcentaje* | Porcentaje de apertura para compuertas en alta. |
| **AV21**    | *Porcentaje* | Porcentaje de apertura para compuertas en baja. |
| **AV24**    | *Sin unidades* | Multiplicador de calibración para P4_VG. |
| **AV25**    | *Sin unidades* | Offset de calibración para P4_VG. |
| **AV28**    | *Sin unidades* | Multiplicador de calibración para P4_VC. |
| **AV29**    | *Sin unidades* | Offset de calibración para P4_VC. |
| **AV33**    | *Sin unidades* | Multiplicador de calibración para P5_VC. |
| **AV34**    | *Sin unidades* | Offset de calibración para P5_VC. |
| **AV37**    | *Sin unidades* | Multiplicador de calibración para P5_VG. |
| **AV38**    | *Sin unidades* | Offset de calibración para P5_VG. |
| **AV41**    | *Sin unidades* | Valor de medición para caudal P6_VG. |
| **AV42**    | *Sin unidades* | Multiplicador de calibración para P6_VG. |
| **AV43**    | *Sin unidades* | Offset de calibración para P6_VG. |
| **AV45**    | *Sin unidades* | Valor de medición para caudal P6_VM. |
| **AV46**    | *Sin unidades* | Multiplicador de calibración para P6_VM. |
| **AV47**    | *Sin unidades* | Offset de calibración para P6_VM. |
| **AV50**    | *Sin unidades* | Valor de medición para caudal PR7_VC. |
| **AV51**    | *Sin unidades* | Multiplicador de calibración para PR7_VC. |
| **AV52**    | *Sin unidades* | Offset de calibración para PR7_VC. |
| **AV54**    | *Sin unidades* | Valor de medición para caudal PR7_VG. |
| **AV55**    | *Sin unidades* | Multiplicador de calibración para PR7_VG. |
| **AV56**    | *Sin unidades* | Offset de calibración para PR7_VG. |
| **AV59**    | *Sin unidades* | Número de muestras. |
| **AV60**    | *Segundos* | Tiempo entre muestras. |
| **AV63**    | *Sin unidades* | Mínimo muestreado del sistema. |
| **AV65**    | *Sin unidades* | Máximo muestreado del sistema. |
| **AV67**    | *Sin unidades* | Factor multiplicador resultante. |
| **AV68**    | *Sin unidades* | Factor offset resultante. |
| **BV1**     | *Binario* | Activación del sistema de calibración. |
| **BV2**     | *Binario* | Inicio de toma de muestras. |
| **BV3**     | *Binario* | Leer valores para calibración. |
| **BV4**     | *Binario* | Reset de factores de calibración. |
| **BV5**     | *Binario* | Activar cálculo de factores de calibración. |
| **BV6**     | *Binario* | Comando para calibración. |
| **BV7**     | *Binario* | Activación de compuerta. |
| **BV13**    | *Binario* | Inicio de muestreo. |
| **BV16**    | *Binario* | Reset de medición de variables. |
| **BV17**    | *Binario* | Calcular factores de calibración. |
| **BV18**    | *Binario* | Guardar valores de calibración. |
| **MSV1**    | *Sin unidades* | Control de selección de caja activa. |

---

# Listado de Variables Locales

1. **CAL_ACTIV**  
   - ***DESCRIPCIÓN:*** Variable de activación del sistema de calibración.  
   - ***UNIDADES:*** Sin unidades.  

2. **CAL_VAV**  
   - ***DESCRIPCIÓN:*** Selección de caja activa para calibración.  
   - ***UNIDADES:*** Sin unidades.  

3. **CAL_INICIO**  
   - ***DESCRIPCIÓN:*** Indica el inicio del proceso de toma de muestras.  
   - ***UNIDADES:*** Sin unidades.  

4. **CAL_MUES_ACT**  
   - ***DESCRIPCIÓN:*** Número actual de muestras tomadas durante la calibración.  
   - ***UNIDADES:*** Sin unidades.  

5. **CAL_NUM_MUES**  
   - ***DESCRIPCIÓN:*** Número de muestras programadas para la calibración.  
   - ***UNIDADES:*** Sin unidades.  

6. **CAL_TM_MUES**  
   - ***DESCRIPCIÓN:*** Tiempo entre cada muestra tomada durante la calibración.  
   - ***UNIDADES:*** Segundos.  

7. **CAL_NUM_MAX**  
   - ***DESCRIPCIÓN:*** Número máximo de muestras permitido.  
   - ***UNIDADES:*** Sin unidades.  

8. **CAL_NUM_MIN**  
   - ***DESCRIPCIÓN:*** Número mínimo de muestras permitido.  
   - ***UNIDADES:*** Sin unidades.  

9. **CAL_TM_MAX**  
   - ***DESCRIPCIÓN:*** Tiempo máximo permitido entre muestras.  
   - ***UNIDADES:*** Segundos.  

10. **CAL_TM_MIN**  
    - ***DESCRIPCIÓN:*** Tiempo mínimo permitido entre muestras.  
    - ***UNIDADES:*** Segundos.  

11. **CAL_LEER**  
    - ***DESCRIPCIÓN:*** Comando para leer los valores de los factores de calibración.  
    - ***UNIDADES:*** Sin unidades.  

12. **CAL_RESET**  
    - ***DESCRIPCIÓN:*** Comando para resetear los factores de calibración.  
    - ***UNIDADES:*** Sin unidades.  

13. **CAL_CALCULO**  
    - ***DESCRIPCIÓN:*** Comando para activar el cálculo de los factores de calibración.  
    - ***UNIDADES:*** Sin unidades.  

14. **CAL_CALIBRAR**  
    - ***DESCRIPCIÓN:*** Comando para ejecutar la calibración con los factores calculados.  
    - ***UNIDADES:*** Sin unidades.  

15. **CAL_MULTI**  
    - ***DESCRIPCIÓN:*** Factor multiplicador calculado en la calibración.  
    - ***UNIDADES:*** Sin unidades.  

16. **CAL_OFFSET**  
    - ***DESCRIPCIÓN:*** Factor de desplazamiento calculado en la calibración.  
    - ***UNIDADES:*** Sin unidades.  

17. **CAL_HI_BAL**  
    - ***DESCRIPCIÓN:*** Valor de referencia alto de calibración.  
    - ***UNIDADES:*** Sin unidades.  

18. **CAL_LW_BAL**  
    - ***DESCRIPCIÓN:*** Valor de referencia bajo de calibración.  
    - ***UNIDADES:*** Sin unidades.  

19. **CAL_HI_SIS**  
    - ***DESCRIPCIÓN:*** Valor alto del sistema medido durante la calibración.  
    - ***UNIDADES:*** Sin unidades.  

20. **CAL_LW_SIS**  
    - ***DESCRIPCIÓN:*** Valor bajo del sistema medido durante la calibración.  
    - ***UNIDADES:*** Sin unidades.  

21. **CAL_PR_HI**  
    - ***DESCRIPCIÓN:*** Porcentaje de apertura de compuerta en alta.  
    - ***UNIDADES:*** Porcentaje.  

22. **CAL_PR_LW**  
    - ***DESCRIPCIÓN:*** Porcentaje de apertura de compuerta en baja.  
    - ***UNIDADES:*** Porcentaje.  

23. **CAL_PR_SW**  
    - ***DESCRIPCIÓN:*** Selector de porcentaje de apertura (alta o baja).  
    - ***UNIDADES:*** Sin unidades.  

24. **VAV_Q**  
    - ***DESCRIPCIÓN:*** Valor de medición de caudal del VAV seleccionado.  
    - ***UNIDADES:*** Sin unidades.  

25. **PR_COMP**  
    - ***DESCRIPCIÓN:*** Porcentaje de compuerta asignado a la caja activa.  
    - ***UNIDADES:*** Porcentaje.  

26. **INICIO**  
    - ***DESCRIPCIÓN:*** Comando para iniciar el muestreo de caudales.  
    - ***UNIDADES:*** Sin unidades.  

27. **MUESTRA**  
    - ***DESCRIPCIÓN:*** Contador de muestras tomadas.  
    - ***UNIDADES:*** Sin unidades.  

28. **N_MUESTRA**  
    - ***DESCRIPCIÓN:*** Número de muestras programadas para tomar.  
    - ***UNIDADES:*** Sin unidades.  

29. **T_MUESTRA**  
    - ***DESCRIPCIÓN:*** Tiempo entre muestras en el muestreo.  
    - ***UNIDADES:*** Segundos.  

30. **N_MAX**  
    - ***DESCRIPCIÓN:*** Número máximo de muestras permitidas.  
    - ***UNIDADES:*** Sin unidades.  

31. **N_MIN**  
    - ***DESCRIPCIÓN:*** Número mínimo de muestras permitidas.  
    - ***UNIDADES:*** Sin unidades.  

32. **T_MAX**  
    - ***DESCRIPCIÓN:*** Tiempo máximo permitido entre muestras.  
    - ***UNIDADES:*** Segundos.  

33. **T_MIN**  
    - ***DESCRIPCIÓN:*** Tiempo mínimo permitido entre muestras.  
    - ***UNIDADES:*** Segundos.  

34. **VARIABLE**  
    - ***DESCRIPCIÓN:*** Variable temporal para el almacenamiento de valores de medición.  
    - ***UNIDADES:*** Sin unidades.  

35. **CALCULAR**  
    - ***DESCRIPCIÓN:*** Comando para activar el cálculo de factores de calibración.  
    - ***UNIDADES:*** Sin unidades.  

36. **X1**  
    - ***DESCRIPCIÓN:*** Valor alto del sistema utilizado en el cálculo de la pendiente.  
    - ***UNIDADES:*** Sin unidades.  

37. **X2**  
    - ***DESCRIPCIÓN:*** Valor bajo del sistema utilizado en el cálculo de la pendiente.  
    - ***UNIDADES:*** Sin unidades.  

38. **Y1**  
    - ***DESCRIPCIÓN:*** Valor alto de referencia utilizado en el cálculo de la pendiente.  
    - ***UNIDADES:*** Sin unidades.  

39. **Y2**  
    - ***DESCRIPCIÓN:*** Valor bajo de referencia utilizado en el cálculo de la pendiente.  
    - ***UNIDADES:*** Sin unidades.  

40. **B**  
    - ***DESCRIPCIÓN:*** Desplazamiento calculado a partir de la referencia y los valores medidos.  
    - ***UNIDADES:*** Sin unidades.  

41. **M**  
    - ***DESCRIPCIÓN:*** Pendiente calculada a partir de la referencia y los valores medidos.  
    - ***UNIDADES:*** Sin unidades.  

---

# Lógica de Control del Programa

## Paso a Paso de la Lógica de Control

1. **Activación del Sistema**  
   - Si `CAL_ACTIV` es igual a 1, el sistema se activa y se inicializan los parámetros para el muestreo y control de caudales.

2. **Inicio del Muestreo**  
   - Si se ha iniciado el muestreo (`CAL_INICIO` = 1), el programa verifica si el número de muestras (`CAL_NUM_MUES`) y el tiempo entre ellas (`CAL_TM_MUES`) están dentro de los límites permitidos (`CAL_NUM_MAX`, `CAL_NUM_MIN`, `CAL_TM_MAX`, `CAL_TM_MIN`).
   - Si los valores están dentro de los límites, se procede con la toma de muestras en intervalos de tiempo especificados. El número de muestras acumuladas se incrementa con cada ciclo de muestreo y se calcula un promedio del valor medido.

3. **Asignación de Apertura de Compuertas**  
   - La lógica asigna un valor de apertura de compuertas basado en la comparación entre los límites de porcentaje (`CAL_PR_HI`, `CAL_PR_LW`) y el valor del selector (`CAL_PR_SW`). Dependiendo del estado del selector, se asigna un porcentaje alto o bajo de apertura de las compuertas.

4. **Cálculo de Factores de Calibración**  
   - Cuando se activa la lectura de los factores (`CAL_LEER` = 1), se obtienen los valores de multiplicador (`CAL_MULTI`) y offset (`CAL_OFFSET`) de calibración de la caja activa.
   - Si se inicia el cálculo de factores (`CAL_CALCULO` = 1), el programa calcula la pendiente y desplazamiento utilizando las mediciones de referencia (`CAL_HI_BAL`, `CAL_LW_BAL`) y los valores del sistema (`CAL_HI_SIS`, `CAL_LW_SIS`), actualizando los factores de calibración.

5. **Asignación de Caudales y Control de VAV**  
   - Según el valor de la caja activa (`CAL_VAV`), el programa selecciona los caudales y compuertas correspondientes y actualiza las variables de control del sistema.
   - Si `CAL_ACTIV` es igual a 0, se establece la apertura de todas las compuertas en 0 para desactivar el sistema de control.

6. **Reset de Variables**  
   - Si se detecta un cambio en la caja activa (`CAL_VAV`), se reinician los valores de medición del sistema (`CAL_HI_SIS`, `CAL_LW_SIS`) y se resetean los factores de calibración a sus valores iniciales.

7. **Control de Compuertas de Demanda**  
   - La demanda de apertura de las compuertas se ajusta en función de los valores medidos y de la configuración establecida, utilizando intervalos de tiempo y límites de seguridad para asegurar una operación estable del sistema de compuertas.

## Resumen

El programa sigue una lógica estructurada para activar el sistema de calibración, tomar muestras, y ajustar los factores de calibración en un sistema HVAC. Se basa en la activación de diferentes variables de control y verifica constantemente que los valores se mantengan dentro de los límites establecidos para la toma de muestras y la apertura de compuertas. Además, se asegura de reiniciar y ajustar los factores de calibración y caudales según las mediciones obtenidas.

Esta lógica garantiza que el sistema HVAC opere con un caudal calibrado de manera eficiente, permitiendo ajustes automáticos y reseteos en función de las condiciones de operación y las cajas activas.
