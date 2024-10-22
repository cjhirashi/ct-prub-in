# PRG1_SENSORES
- Controlador: Cuarto Control 1

- Descripción: Este programa está diseñado para la lectura, cálculo y monitoreo de caudales en unidades de volumen de aire variable (VAV) en un sistema HVAC. Utiliza mediciones de presión diferencial (DP) para calcular los caudales de flujo de aire (`CFM`) de diferentes VAVs distribuidos en varios plenums. El programa aplica fórmulas de conversión y calibración para obtener caudales precisos y calcula el caudal total por cada plenum.

- Versión: 2.0.0

- Autor: Carlos Jimenez Hirashi - @cjhirashi

---

# Variables de control

#### **PLENUM 1**

- **AV9.10021** | `CFM` | *CFM* | Caudal total del Plenum

**VAV 01 - Mediana**
- **AI3.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV1.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV2.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV3.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV4.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 02 - Grande**
- **AI4.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV5.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV6.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV7.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV8.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 03 - Chica**
- **AI16.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV59.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV60.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV61.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV62.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

#### **PLENUM 2**

- **AV18.10021** | `CFM` | *CFM* | Caudal total del Plenum

**VAV 01 - Mediana**
- **AI5.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV10.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV11.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV12.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV13.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 02 - Grande**
- **AI6.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV14.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV15.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV16.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV17.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

#### **PLENUM 3**

**VAV 01 - Grande**
- **AI17.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV63.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV64.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV65.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV66.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

#### **PLENUM 4**

- **AV31.10021** | `CFM` | *CFM* | Caudal total del Plenum

**VAV 01 - Mediana**
- **AI7.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV19.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV20.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV21.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV22.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 02 - Grande**
- **AI8.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV23.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV24.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV25.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV26.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 03 - Chica**
- **AI9.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV27.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV28.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV29.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV30.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

#### **PLENUM 5**

- **AV40.10021** | `CFM` | *CFM* | Caudal total del Plenum

**VAV 01 - Chica**
- **AI10.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV32.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV33.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV34.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV35.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 02 - Grande**
- **AI11.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV36.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV37.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV38.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV39.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

#### **PLENUM 6**

- **AV49.10021** | `CFM` | *CFM* | Caudal total del Plenum

**VAV 01 - Grande**
- **AI12.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV41.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV42.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV43.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV44.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 02 - Mediana**
- **AI13.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV45.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV46.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV47.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV48.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

#### **PLENUM R7 - RETORNO**

- **AV58.10021** | `CFM` | *CFM* | Caudal total de Plenum de Retorno

**VAV 01 - Chica**
- **AI14.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV50.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV51.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV52.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV53.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

**VAV 02 - Grande**
- **AI15.10021** | `DP` | *"WC* | Caída de presión de flujo de aire VAV
- **AV54.10021** | `CFM_R` | *CFM* | Caudal de flujo de aire VAV sin calibrar
- **AV55.10021** | `MULT` | *---* | Multiplicador para calibración de Caudal VAV
- **AV56.10021** | `OFFSET` | *---* | Offset para calibración de Caudal VAV
- **AV57.10021** | `CFM` | *CFM* | Caudal de flujo de aire VAV Calibrado

---

# Variables Locales

1. **DP**  
   - Descripción: Variable local para almacenar la lectura de presión diferencial para un VAV. Se asigna a través de entradas análogas (`AI`).
   - Unidades: `"WC`

2. **AREA**  
   - Descripción: Área de entrada de aire a cada VAV, especificada en pies cuadrados.
   - Unidades: `pies²`

3. **CV**  
   - Descripción: Coeficiente de flujo de aire para cada VAV, utilizado en la fórmula de cálculo del caudal.
   - Unidades: *---*

4. **CFM_R**  
   - Descripción: Caudal de flujo de aire no calibrado para cada VAV. Calculado utilizando `CV` y `DP`.
   - Unidades: `CFM`

5. **MULT**  
   - Descripción: Multiplicador utilizado para la calibración del caudal de cada VAV.
   - Unidades: *---*

6. **OFFSET**  
   - Descripción: Desplazamiento utilizado para la calibración del caudal de cada VAV.
   - Unidades: *---*

7. **CFM**  
   - Descripción: Caudal de flujo de aire calibrado para cada VAV.
   - Unidades: `CFM`

---

# Lógica de Control

La lógica de control del programa se enfoca en la lectura, cálculo y calibración de los caudales de aire para diferentes cajas VAV (Variable Air Volume). A continuación, se explica paso a paso cómo se lleva a cabo esta lógica:

1. **Lectura de la presión diferencial (`DP`)**  
   
   Cada caja VAV está equipada con un sensor de presión diferencial. La presión diferencial (`DP`) es leída mediante entradas análogas (`AI`). Estas lecturas son esenciales para calcular el caudal de aire (`CFM`) de cada VAV.  
   **Ejemplo de asignación:**  
   `DP = AI3` para la VAV Mediana del Plenum 1.

2. **Cálculo del caudal no calibrado (`CFM_R`)**  
   
   Se calcula el caudal de aire no calibrado (`CFM_R`) utilizando la fórmula de flujo de aire que toma en cuenta la presión diferencial (`DP`) y un coeficiente de flujo (`CV`) característico de cada VAV. La fórmula utilizada es:  
   ```plaintext
   CFM_R = CV * sqrt(DP)
   ```
   Este valor se calcula de forma individual para cada caja VAV.

3. **Calibración del caudal (`CFM`)**
    
    Una vez obtenido el valor de CFM_R, se aplica un proceso de calibración para ajustar el caudal, utilizando dos parámetros: un    multiplicador (MULT) y un desplazamiento (OFFSET). La fórmula de calibración es:
    ```plaintext
    CFM = (CFM_R * MULT) + OFFSET
    ```
    `MULT` permite realizar ajustes lineales en el valor calculado.

    `OFFSET` compensa errores sistemáticos en la medición o variaciones específicas del sistema.

4. **Ajuste del caudal a valores positivos**
    
    Se asegura que el caudal final (CFM) no tenga valores negativos aplicando una función de máximo:
    ```plaintext
    CFM = MAX(0, CFM)

    ```

5. **Almacenamiento de los caudales calculados**
    
    Cada valor de caudal no calibrado (`CFM_R`) y calibrado (`CFM`) se almacena en variables de control (por ejemplo, `AV1` para el `CFM_R` y `AV4` para el `CFM` en la VAV Mediana del Plenum 1).

6. **Cálculo del caudal total por plenum**
    
    Para cada plenum, se calcula el caudal total como la suma de los caudales calibrados (`CFM`) de las diferentes cajas VAV que forman parte de dicho plenum.
    **Ejemplo de cálculo del caudal total en Plenum 1:**
    ```plaintext
    AV9 = AV4 + AV8 + AV62

    ```
    Donde `AV4`, `AV8`, y `AV62` representan los caudales calibrados de las VAV Mediana, Grande y Chica respectivamente en el Plenum 1.

7. **Cálculo de los caudales de retorno**
    
    En los plenums de retorno (por ejemplo, Plenum 7), se suman los caudales calibrados de las cajas grandes y chicas de retorno para obtener el caudal total de retorno:
    ```plaintext
    AV104 = AV102 + AV103

    ```

## Resumen
La lógica de control se basa en:

 - Lectura de la presión diferencial (DP) a través de sensores análogos (AI).
 - Cálculo del caudal no calibrado (CFM_R) utilizando un coeficiente de flujo (CV).
 - Calibración del caudal (CFM) aplicando un multiplicador (MULT) y un desplazamiento (OFFSET).
 - Suma de caudales calibrados para obtener el caudal total de cada plenum.
 - Cálculo del caudal total de retorno sumando los caudales de las cajas de retorno

Este enfoque asegura un monitoreo preciso y ajustable de los caudales de aire en el sistema HVAC, ajustando los valores según las necesidades operativas y características de cada caja VAV.