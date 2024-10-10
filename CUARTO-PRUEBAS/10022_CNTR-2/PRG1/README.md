# PRG1 CALIBRACION - V2.0.0

Sistema de calibración a medición de caudales del sistema de control

## DECLARACION DE VARIABLES

1. VARIABLES: Parámetros de activación de sistema de calibración

    > `CAL_ACTIV` = BV1 (*ON/OFF*) | ACTIVACIÓN DEL SISTEMA DE CONTROL
    >
    > `CAL_VAV` = MSV1              | VAV EN OPERACIÓN

2. VARIABLES: Parámetros de control de toma de muestras para calibración

    > `CAL_INICIO` = **BV2** (*ON/OFF*) | INICIO DE TOMA DE MUESTRAS PARA CALIBRACIÓN
    >
    > `CAL_MUES_ACT` = **AV7**          | NÚMERO DE MUESTRA ACTIVA
    >
    > `CAL_NUM_MUES` = **AV8**          | NÚMERO DE MUESTRAS
    >
    > `CAL_TM_MUES` = **AV9** (*seg*)   | TIEMPO ENTRE MUESTRAS

3. CONSTANTES: Parámetros de control de toma de muestra para calibración

    > `CAL_NUM_MAX` = **AV10**          | NÚMERO MÁXIMO DE MUESTRAS
    >
    > `CAL_NUM_MIN` = **AV11**          | NÚMERO MÍNIMO DE MUESTRAS
    >
    > `CAL_TM_MAX` = **AV12** (*seg*)   | TIEMPO MÁXIMO PARA TOMA DE MUESTRAS
    >
    > `CAL_TM_MIN` = **AV13** (*seg*)   | TIEMPO MÍNIMO PARA TOMA DE MUESTRAS

4. VARIABLES: Parámetros de control de factores de calibración

    > `CAL_LEER` = **BV3** (*ON/OFF*)      | LEER FACTOR DE CALIBRACIÓN EXISTENTE
    >
    > `CAL_RESET` = **BV4** (*ON/OFF*)     | RESET DE VARIABLES DE FACTOR CALIBRACIÓN
    >
    > `CAL_CALCULO` = **BV5** (*ON/OFF*)   | CÁLCULO DE FACTOR DE CALIBRACIÓN
    >
    > `CAL_CALIBRAR` = **BV6** (*ON/OFF*)  | CALIBRACIÓN DE MEDICIÓN DE CAUDALES
    >
    > **AV14** = `CAL_MULTI`     | FACTOR MULTIPLICADOR PARA CALIBRACIÓN
    >
    > **AV15** = `CAL_OFFSET`    | FACTOR OFFSET PARA CALIBRACIÓN

5. VARIABLES: Muestra de medición de caudales 

    * Medición desde Balómetro de usuario

        > `CAL_HI_BAL` = **AV16** (*CFM*)  | MEDICIÓN DE CAUDALES, RANGO ALTO, BALOMETRO
        >
        > `CAL_LW_BAL` = **AV17** (*CFM*)  | MEDICIÓN DE CAUDALES, RANGO BAJO, BALOMETRO
    
    * Medición del sistema de control

        > **AV18** = `CAL_HI_SIS` (*CFM*)  | MEDICIÓN DE CAUDALES, RANGO ALTO, SISTEMA
        >
        > **AV19** = `CAL_LW_SIS` (*CFM*)  | MEDICIÓN DE CAUDALES, RANGO BAJO, SISTEMA

6. VARIABLES: Porcentaje de apertura para compuertas

    > `CAL_PR_HI` = **AV20** (*%*)      | PORCENTAJE DE APERTURA ALTO
    >
    > `CAL_PR_LW` = **AV21** (*%*)      | PORCENTAJE DE APERTURA BAJO
    >
    > `CAL_PR_SW` = **BV7** (*LW/HI*)   | SELECTOR DE PORCENTAJE DE APERTURA

7. VARIABLES: Parámetros de medición de caudales y apertura de compuerta de VAV activa

    > `VAV_Q` (*CFM*)       | CAUDAL DE VAV ACTIVA   
    >
    > `PR_COMP` (*%*)       | PORCENTAJE DE APERTURA DE COMPUERTA

8. VARIABLES: Parámetros de VAVs, caudal y apertura de compuerta, estos parámetros se sincronizan cada 5 seg, solo cuando la variable `CAL_ACTIV` se encuentra en estado activo

    * PLENUM 1

        > ***MEDIANA***
        >
        > `P1_VM_Q` = 10021.**AV1**         | CAUDAL DE AIRE
        >
        > 10021.**AO1** = `P1_VM_A`         | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV2**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV3**      | OFFSET

        > ***GRANDE***
        >
        > `P1_VG_Q` = 10021.**AV5**         | CAUDAL DE AIRE
        >
        > 10021.**AO2** = `P1_VG_A`         | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV6**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV7**      | OFFSET

        > ***CHICA***
        >
        > `P1_VC_Q` = 10021.**AV59**        | CAUDAL DE AIRE
        >
        > 10021.**AO21** = `P1_VC_A`        | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV60**      | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV61**     | OFFSET

    * PLENUM 2

        > ***MEDIANA***
        >
        > `P2_VM_Q` = 10021.**AV10**      | CAUDAL DE AIRE
        >
        > 10021.**AO3** = `P2_VM_A`       | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV11**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV12**      | OFFSET

        > ***GRANDE***
        >
        > `P2_VG_Q` = 10021.**AV14**      | CAUDAL DE AIRE
        >
        > 10021.**AO4** = `P2_VG_A`       | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV15**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV16**      | OFFSET

    * PLENUM 3

        > ***GRANDE***
        >
        > `P3_VG_Q` = 10021.**AV63**       | CAUDAL DE AIRE
        >
        > 10021.**AO23** = `P3_VG_A`       | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV64**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV65**      | OFFSET

    * PLENUM 4

        > ***MEDIANA***
        >
        > `P4_VM_Q` = 10021.**AV19**       | CAUDAL DE AIRE
        >
        > 10021.**AO5** = `P4_VM_A`        | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV20**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV21**      | OFFSET

        > ***GRANDE***
        >
        > `P4_VG_Q` = 10021.**AV23**       | CAUDAL DE AIRE
        >
        > 10021.**AO6** = `P4_VG_A`        | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV24**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV25**      | OFFSET

        > ***CHICA***
        >
        > `P4_VC_Q` = 10021.**AV27**       | CAUDAL DE AIRE
        >
        > 10021.**AO7** = `P4_VC_A`        | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV28**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV29**      | OFFSET

    * PLENUM 5

        > ***CHICA***
        >
        > `P5_VC_Q` = 10021.**AV32**       | CAUDAL DE AIRE
        >
        > 10021.**AO8** = `P5_VC_A`        | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV33**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV34**      | OFFSET

        > ***GRANDE***
        >
        > `P5_VG_Q` = 10021.**AV36**       | CAUDAL DE AIRE
        >
        > 10021.**AO9** = `P5_VG_A`        | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV37**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV38**      | OFFSET

    * PLENUM 6

        > ***GRANDE***
        >
        > `P6_VG_Q` = 10021.**AV41**       | CAUDAL DE AIRE
        >
        > 10021.**AO10** = `P6_VG_A`       | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV42**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV43**      | OFFSET

        > ***MEDIANA***
        >
        > `P6_VM_Q` = 10021.**AV45**       | CAUDAL DE AIRE
        >
        > 10021.**AO11** = `P6_VM_A`       | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV46**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV47**      | OFFSET

    * PLENUM R7

        > ***CHICA***
        >
        > `PR7_VC_Q` = 10021.**AV50**       | CAUDAL DE AIRE
        >
        > 10021.**AO12** = `PR7_VC_A`       | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV51**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV52**      | OFFSET

        > ***GRANDE***
        >
        > `PR7_VG_Q` = 10021.**AV54**       | CAUDAL DE AIRE
        >
        > 10021.**AO13** = `PR7_VG_A`       | APERTURA DE COMPUERTA
        >
        > `CAL_MULTI` = 10021.**AV55**       | MULTIPLICADOR
        >
        > `CAL_OFFSET` = 10021.**AV56**      | OFFSET