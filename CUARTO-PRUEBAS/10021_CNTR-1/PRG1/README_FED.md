# PRG1_SENSORES (Control: Cuarto Control 1)

## Descripción del Programa
Este programa controla y monitorea la lectura de caudales en los sistemas de ventilación variable por volumen (VAV) en un edificio, realizando cálculos de caudales en varios plenums. El programa toma las lecturas de presión diferencial (DP) de sensores análogos y calcula el caudal volumétrico (CFM) en diferentes unidades de VAV, además de aplicar correcciones de calibración y sumar los caudales totales por cada plenum.

## Autor del Programa
Carlos Jimenez Hirashi (@cjhirashi)

## Versión del Programa
2.0.0

---

## Variables de Control

| **NOMBRE** | **NUMERO Y TIPO DE VARIABLE** | **Descripción** |
|------------|-------------------------------|-----------------|
| `DP`       | AI                             | Lectura de presión diferencial (sensor análogo) |
| `AREA`     | Local                          | Área de la unidad VAV |
| `CV`       | Local                          | Coeficiente de caudal de la unidad VAV |
| `CFM_R`    | Local                          | Caudal calculado antes de la calibración |
| `CFM`      | Local                          | Caudal calibrado de la unidad VAV |
| `MULT`     | AV                             | Factor de multiplicación para la calibración |
| `OFFSET`   | AV                             | Desplazamiento para la calibración del caudal |
| `AV1-AV66` | AV                             | Variables de almacenamiento de los valores de caudal y conversiones de cada VAV |
| `AI3-AI17` | AI                             | Lecturas análogas de presión diferencial para cada VAV |

---

## Lógica de Operación

1. **Cálculo de Caudales en VAVs**
    - El programa calcula el caudal para cada unidad VAV en diferentes plenums del edificio.
    - La fórmula de conversión de caudal es `CFM_R = CV * (DP^0.5)` donde `DP` es la lectura de presión diferencial de cada VAV y `CV` es el coeficiente específico de la unidad VAV.

2. **Plenum 1**  
    - **VAV 01 (Mediana)**  
      - Área: 0.3382, Coeficiente CV: 817, DP: `AI3`.
      - El caudal se calcula y se almacena en `AV1`.
      - Se aplica la calibración con `MULT = AV2` y `OFFSET = AV3`, y el resultado se almacena en `AV4`.
    - **VAV 02 (Grande)**  
      - Área: 1.05, CV: 2474, DP: `AI4`.
      - Caudal en `AV5`, calibración con `MULT = AV6` y `OFFSET = AV7`. Resultado final en `AV8`.
    - **VAV 03 (Chica)**  
      - Área: 0.0819, CV: 209, DP: `AI16`.
      - Caudal en `AV59`, calibración con `MULT = AV60` y `OFFSET = AV61`. Resultado final en `AV62`.
    - **Caudal Total (Plenum 1)**  
      - Suma total de los caudales: `AV9 = AV4 + AV8 + AV62`.

3. **Plenum 2**  
    - Similar proceso de cálculo para los VAVs en el Plenum 2.
    - **VAV 01 (Mediana)**: `AI5`, `CV = 612`, resultado en `AV10`, calibración con `AV11` y `AV12`, resultado final en `AV13`.
    - **VAV 02 (Grande)**: `AI6`, `CV = 1792`, resultado en `AV14`, calibración con `AV15` y `AV16`, resultado final en `AV17`.
    - **Caudal Total (Plenum 2)**: `AV18 = AV13 + AV17`.

4. **Plenum 3**  
    - **VAV 01 (Grande)**: `AI17`, `CV = 1250`, resultado en `AV63`, calibración en `AV64` y `AV65`, resultado en `AV66`.

5. **Plenum 4**  
    - **VAV 01 (Mediana)**: `AI7`, `CV = 817`, resultado en `AV19`, calibración en `AV20` y `AV21`, resultado en `AV22`.
    - **VAV 02 (Grande)**: `AI8`, `CV = 2474`, resultado en `AV23`, calibración en `AV24` y `AV25`, resultado en `AV26`.
    - **VAV 03 (Chica)**: `AI9`, `CV = 209`, resultado en `AV27`, calibración en `AV28` y `AV29`, resultado en `AV30`.
    - **Caudal Total (Plenum 4)**: `AV31 = AV22 + AV26 + AV30`.

6. **Plenum 5**  
    - **VAV 01 (Chica)**: `AI10`, `CV = 315`, resultado en `AV32`, calibración en `AV33` y `AV34`, resultado en `AV35`.
    - **VAV 02 (Grande)**: `AI11`, `CV = 3235`, resultado en `AV36`, calibración en `AV37` y `AV38`, resultado en `AV39`.
    - **Caudal Total (Plenum 5)**: `AV40 = AV35 + AV39`.

7. **Plenum 6**  
    - **VAV 01 (Grande)**: `AI12`, `CV = 2474`, resultado en `AV41`, calibración en `AV42` y `AV43`, resultado en `AV44`.
    - **VAV 02 (Mediana)**: `AI13`, `CV = 817`, resultado en `AV45`, calibración en `AV46` y `AV47`, resultado en `AV48`.
    - **Caudal Total (Plenum 6)**: `AV49 = AV44 + AV48`.

8. **Plenum R7**  
    - **VAV 01 (Chica)**: `AI14`, `CV = 209`, resultado en `AV50`, calibración en `AV51` y `AV52`, resultado en `AV53`.
    - **VAV 02 (Grande)**: `AI15`, `CV = 2474`, resultado en `AV54`, calibración en `AV55` y `AV56`, resultado en `AV57`.
    - **Caudal Total (Plenum R7)**: `AV58 = AV53 + AV57`.

9. **Caudales de Retorno**  
    - `AV102 = AV57` (Caudal Caja Grande de Retorno).
    - `AV103 = AV53` (Caudal Caja Chica de Retorno).
    - `AV104 = AV102 + AV103` (Caudal Total de Retorno).

---

## Conclusión

El programa permite monitorear y controlar los caudales en diferentes sistemas VAV, aplicando una lógica de conversión y calibración específica para cada unidad en función de su presión diferencial, área y coeficiente de caudal.
