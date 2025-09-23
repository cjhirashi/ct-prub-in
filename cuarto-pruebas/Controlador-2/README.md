# SISTEMA DE CALIBRACIÓN CUARTO DE PRUEBAS - CONTROLADOR 2

![badge-status](https://img.shields.io/badge/status-operativo-green)
![badge-protocol](https://img.shields.io/badge/protocol-BACnet%20MS/TP-blue)
![badge-controller](https://img.shields.io/badge/controller-KMC%20BAC--5901C-orange)
![badge-function](https://img.shields.io/badge/función-calibración-purple)
![badge-version](https://img.shields.io/badge/version-2.0.0-blue)

## 📖 Descripción General

El **Controlador 2** del Cuarto de Pruebas se especializa en **gestión de calibración avanzada** y **funciones de soporte operativo** para el laboratorio de pruebas HVAC de INNES Aire. Actúa como sistema complementario del Controlador 1, proporcionando capacidades específicas de calibración de caudales, gestión de parámetros de corrección y control auxiliar de compuertas de bloqueo distribuidas.

Este controlador implementa **algoritmos de calibración híbrida KMC-Excel**, permitiendo ajustes precisos de multiplicadores y offsets para cada VAV del sistema, garantizando mediciones de caudal con precisión superior al ±2% en condiciones operativas normales.

### Arquitectura de Calibración

```plaintext
┌─────────────────────────────────────────────────────────────┐
│                   CONTROLADOR 2                            │
│               KMC BAC-5901C (DI: 10022)                    │
│                  MAC Address: 22                           │
└─────────────────┬───────────────────────────────────────────┘
                  │
                  ├── Módulo Calibración ──── Análisis estadístico
                  │                           Variables AV1-AV43
                  │
                  ├── Control Auxiliar ────── Compuertas bloqueo
                  │                           8 salidas binarias
                  │
                  └── Interfaz Excel ──────── Exportación datos
                                             Importación coeficientes
```

### Distribución Funcional

| **Función Principal** | **Componentes Gestionados** | **Precisión Objetivo** |
|---|---|---|
| **Calibración de caudales** | 15 VAVs con parámetros individuales | ±2% span |
| **Control auxiliar** | 8 compuertas de bloqueo remotas | ON/OFF confiable |
| **Análisis estadístico** | Variables de muestreo y tiempo | R² > 0.995 |
| **Interfaz de datos** | Exportación/importación Excel | Formato estandarizado |

## 🖧 Información del Controlador

### Hardware Principal

| **Componente** | **Especificación** | **Descripción** |
|---|---|---|
| **Controlador** | KMC BAC-5901C | Controlador especializado en calibración |
| **Entradas/Salidas** | 8 UI / 8 UO | Configuración estándar |
| **Puerto de comunicación** | RS-485 | BACnet MS/TP nativo |
| **Alimentación** | 24 VAC/DC | Fuente de alimentación estándar |

### Módulo de Expansión

| **Componente** | **Especificación** | **Descripción** |
|---|---|---|
| **Módulo** | KMC CAN-5901 | Expansión para control auxiliar |
| **Entradas/Salidas** | 8 UI / 8 UO | Capacidad adicional |
| **Conectividad** | CAN Bus | Comunicación rápida |
| **Alimentación** | 24 VAC/DC | Fuente independiente |

### Configuración de Red

| **Parámetro** | **Valor** | **Descripción** |
|---|---|---|
| **Device Instance (DI)** | `10022` | Identificador único BACnet |
| **MAC Address** | `22` | Dirección física en red MS/TP |
| **Protocolo** | BACnet MS/TP | Protocolo de comunicación |
| **Velocidad** | 38,400 bps | Velocidad estándar |
| **Prioridad de comunicación** | Alta | Para funciones críticas de calibración |
| **Tiempo de respuesta típico** | < 50 ms | Optimizado para calibración |

## 📋 Variables de Calibración (AV1-AV43)

### Sistema de Calibración por Plenum

| **Plenum** | **VAV** | **Variables Principales** | **Función** |
|---|---|---|---|
| **P1** | VM (Mediana) | AV1, AV2, AV3 | Valor, Multiplicador, Offset |
| **P1** | VG (Grande) | AV5, AV6, AV7 | Valor, Multiplicador, Offset |
| **P2** | VM (Mediana) | AV10, AV11, AV12 | Valor, Multiplicador, Tiempo |
| **P3** | VG (Grande) | AV16, AV17 | Valor medición, Offset |
| **P4** | VG (Grande) | AV24, AV25 | Multiplicador, Offset |
| **P4** | VC (Chica) | AV28, AV29 | Multiplicador, Offset |
| **P5** | VC (Chica) | AV33, AV34 | Multiplicador, Offset |
| **P5** | VG (Grande) | AV37, AV38 | Multiplicador, Offset |
| **P6** | VG (Grande) | AV41, AV42, AV43 | Valor, Multiplicador, Offset |

### Variables de Control de Muestreo

| **Variable** | **Unidad** | **Función** | **Rango Típico** |
|---|---|---|---|
| **AV8** | *Adimensional* | Número de muestras para calibración | 10-100 |
| **AV9** | *Segundos* | Tiempo entre muestras | 1-10 s |
| **AV12** | *Segundos* | Tiempo máximo de muestreo | 60-600 s |
| **AV13** | *Segundos* | Tiempo mínimo de muestreo | 30-120 s |
| **AV14** | *Adimensional* | Factor multiplicador global | 0.5-2.0 |
| **AV15** | *Adimensional* | Offset global de calibración | -50 a +50 |

### Variables de Control de Apertura

| **Variable** | **Unidad** | **Función** | **Valor Típico** |
|---|---|---|---|
| **AV20** | *Porcentaje* | Apertura compuertas en alta | 80-100% |
| **AV21** | *Porcentaje* | Apertura compuertas en baja | 10-20% |
| **AV18** | *Adimensional* | Valor máximo del sistema | Configurable |
| **AV19** | *Adimensional* | Valor mínimo del sistema | Configurable |

## 🔄 Programa Principal: PRG1_CALIBRACION

### Descripción Técnica Detallada

El **PRG1_CALIBRACION** implementa un sistema avanzado de calibración de caudales que combina **adquisición automatizada de datos** en el controlador KMC con **análisis estadístico robusto** en Excel externo.

**Funcionalidades principales:**
- **Gestión de sesiones de calibración** con parámetros configurables
- **Control automatizado de aperturas** de compuertas para puntos de calibración
- **Toma de muestras estadísticamente válidas** con control de tiempos
- **Cálculo en tiempo real** de multiplicadores y offsets
- **Validación de calidad** de datos con métricas de precisión

### Algoritmo de Calibración

#### 1. Fase de Inicialización
```plaintext
INICIO_CALIBRACION:
├── Validar comunicación con Controlador 1
├── Configurar parámetros de muestreo (AV8, AV9)
├── Establecer rangos de apertura (AV20, AV21)
├── Seleccionar VAV objetivo
└── Preparar variables de almacenamiento
```

#### 2. Fase de Muestreo
```plaintext
CICLO_MUESTREO:
├── FOR apertura = AV21 TO AV20 STEP configurable
│   ├── Comando apertura a Controlador 1
│   ├── Esperar estabilización (30-60s)
│   ├── FOR muestra = 1 TO AV8
│   │   ├── Leer caudal de referencia
│   │   ├── Leer caudal sistema
│   │   ├── Almacenar par (Q_ref, Q_sys)
│   │   └── Esperar AV9 segundos
│   │   └── NEXT muestra
│   └── NEXT apertura
└── Calcular estadísticas por punto
```

#### 3. Fase de Análisis
```plaintext
ANALISIS_ESTADISTICO:
├── Calcular regresión lineal: Q_real = a*Q_sistema + b
├── Evaluar coeficiente de correlación (R²)
├── Validar precisión (RMSE < 2% span)
├── Identificar puntos atípicos (outliers)
├── Generar coeficientes finales (a, b)
└── Actualizar variables AV correspondientes
```

### Interfaz Híbrida KMC-Excel

#### Proceso de Exportación
1. **Datos brutos completos** → Archivo Excel estructurado
2. **Metadatos de sesión** → Fecha, operador, condiciones
3. **Parámetros de calibración** → Configuración utilizada
4. **Resultados estadísticos** → R², RMSE, intervalos confianza

#### Proceso de Importación
1. **Coeficientes validados** ← Análisis Excel externo
2. **Aplicación selectiva** ← Solo VAVs aprobados
3. **Verificación de rangos** ← Límites de seguridad
4. **Confirmación operador** ← Botón "Guardar" requerido

## 📋 Puntos de Control Auxiliar

### Compuertas de Bloqueo Remotas

| **Punto** | **Descripción** | **Ubicación** | **Función** |
|---|---|---|---|
| **BO1** | P2_VG_COMPBLQ | Plenum 2 - VAV Grande | Bloqueo seguridad |
| **BO2** | P4_VM_COMPBLQ | Plenum 4 - VAV Mediana | Bloqueo seguridad |
| **BO3** | P4_VG_COMPBLQ | Plenum 4 - VAV Grande | Bloqueo seguridad |
| **BO4** | P4_VC_COMPBLQ | Plenum 4 - VAV Chica | Bloqueo seguridad |
| **BO5** | P5_VC_COMPBLQ | Plenum 5 - VAV Chica | Bloqueo seguridad |
| **BO6** | P5_VG_COMPBLQ | Plenum 5 - VAV Grande | Bloqueo seguridad |
| **BO7** | P6_VG_COMPBLQ | Plenum 6 - VAV Grande | Bloqueo seguridad |
| **BO8** | P6_VM_COMPBLQ | Plenum 6 - VAV Mediana | Bloqueo seguridad |

### Lógica de Bloqueo de Seguridad

**Estados operativos:**
- **ABIERTA** (1): Permite flujo de aire normal
- **CERRADA** (0): Bloquea flujo para seguridad/mantenimiento

**Condiciones de activación automática:**
- Pérdida de comunicación con Controlador 1
- Presión excesiva en plenum (>2.5" WC)
- Modo mantenimiento activado
- Falla del actuador principal VAV

**Secuencia de recuperación:**
1. Resolver condición de alarma
2. Confirmar condiciones seguras
3. Reset manual desde HMI
4. Verificación de operación normal

## ⚠️ Seguridad y Precauciones

### Seguridad en Calibración

🔬 **ADVERTENCIA - PRECISIÓN CRÍTICA**
- **NUNCA** modificar coeficientes de calibración sin validación completa
- Utilizar únicamente caudalímetros de referencia **certificados** (± 1% precisión)
- Documentar **todas** las sesiones de calibración en bitácora oficial
- Validar resultados con **mínimo 3 puntos** de verificación independientes

### Seguridad de Datos

💾 **CRÍTICO - INTEGRIDAD DE DATOS**
- Realizar **respaldo automático** antes de cada sesión de calibración
- Mantener **registro histórico** de todos los coeficientes aplicados
- **Confirmar manualmente** cada aplicación de nuevos parámetros
- Verificar **trazabilidad completa** desde datos brutos hasta implementación

### Seguridad Operativa

⚡ **PELIGRO - SISTEMA CRÍTICO**
- El Controlador 2 gestiona **funciones de seguridad** (compuertas de bloqueo)
- **Pérdida de comunicación** resulta en activación automática de bloqueos
- **SOLO personal autorizado** puede modificar parámetros de calibración
- Mantener **procedimientos de emergencia** actualizados y accesibles

### Procedimientos de Emergencia

🚨 **PARADA DE EMERGENCIA CALIBRACIÓN**
1. **Detener inmediatamente** cualquier proceso de calibración activo
2. **Cerrar compuertas de bloqueo** (BO1-BO8) en posición segura
3. **Retornar VAVs** a posición de reposo (20% apertura)
4. **Notificar** al Controlador 1 finalización de calibración
5. **Documentar incidente** en sistema de gestión de calidad

## 📚 Manual de Operación

### Preparación de Sesión de Calibración

#### Pre-requisitos del Sistema

1. **Verificaciones Técnicas**
   - Controlador 1 en operación normal
   - Comunicación BACnet estable (< 100ms respuesta)
   - Caudalímetro de referencia calibrado (certificado vigente)
   - Condiciones ambientales estables (±2°C, ±10% HR)

2. **Configuración de Parámetros**
   - **Número de muestras** (AV8): 50 recomendado para precisión óptima
   - **Intervalo de muestreo** (AV9): 2 segundos para estabilidad
   - **Rango de aperturas**: 20% mínimo, 90% máximo
   - **Puntos de calibración**: Mínimo 5 puntos distribuidos uniformemente

#### Ejecución de Calibración Estándar

1. **Selección de VAV**
   - Acceder a interfaz HMI del controlador
   - Seleccionar plenum y tipo de VAV
   - Confirmar estado operativo del VAV objetivo
   - Verificar ausencia de alarmas activas

2. **Configuración de Sesión**
   - Establecer identificación de operador
   - Registrar condiciones ambientales
   - Configurar parámetros de muestreo
   - Preparar archivo Excel de análisis

3. **Proceso Automatizado**
   - **Inicio**: Comando desde HMI principal
   - **Progreso**: Monitoreo en tiempo real de avance
   - **Duración típica**: 15-25 minutos por VAV
   - **Intervención**: Solo en caso de alarma o desviación

4. **Validación de Resultados**
   - **R² mínimo aceptable**: 0.995
   - **RMSE máximo**: 2% del span
   - **Distribución residuos**: Análisis visual en Excel
   - **Puntos atípicos**: < 5% del total de muestras

### Operación en Modo Manual

#### Calibración Punto por Punto

Para casos especiales o validación detallada:

1. **Configuración Manual**
   - Desactivar modo automático
   - Establecer apertura específica (AV20 o AV21)
   - Configurar toma de muestras individual
   - Activar registro manual de datos

2. **Toma de Datos**
   - Comando de apertura específica
   - Esperar estabilización (mínimo 60 segundos)
   - Registrar 20 muestras consecutivas cada 2 segundos
   - Calcular promedio y desviación estándar

3. **Análisis Inmediato**
   - Comparar con valor de referencia
   - Calcular error porcentual
   - Documentar condiciones específicas
   - Decidir aceptación o repetición

### Mantenimiento del Sistema de Calibración

#### Rutina Semanal
- **Verificar comunicación** con todos los puntos remotos
- **Probar secuencia** de compuertas de bloqueo (ciclo completo)
- **Validar precisión** con VAV de referencia conocida
- **Revisar logs** de sesiones de calibración

#### Rutina Mensual
- **Calibrar caudalímetro** de referencia con patrón trazable
- **Verificar configuración** de variables críticas (AV1-AV43)
- **Actualizar respaldos** de configuraciones
- **Generar reporte** de tendencias de calibración

#### Rutina Semestral
- **Calibración completa** del sistema de referencia
- **Validación cruzada** entre múltiples VAVs
- **Actualización de procedimientos** según resultados
- **Certificación de precisión** del sistema completo

## 🔧 Diagnóstico y Resolución de Problemas

### Problemas de Calibración

#### Error de Linealidad (R² < 0.995)

**Síntomas:**
- Coeficiente de correlación bajo
- Distribución errática de puntos
- Residuos con tendencia clara

**Causas Probables:**
- Inestabilidad en presión de suministro
- Interferencias de VAVs adyacentes  
- Sensor de referencia descalibrado
- Condiciones ambientales variables

**Solución Sistemática:**
1. **Verificar estabilidad** de presión estática (±0.05" WC)
2. **Aislar VAV** desactivando plenums adyacentes temporalmente
3. **Recalibrar sensor** de referencia con patrón certificado
4. **Repetir calibración** con condiciones controladas más estrictas

#### Deriva de Parámetros

**Síntomas:**
- Cambio gradual en multiplicadores/offsets
- Precisión decreciente en el tiempo
- Discrepancias entre calibraciones consecutivas

**Causas Probables:**
- Desgaste mecánico de actuadores
- Acumulación de suciedad en sensores
- Cambios en características del ducto
- Degradación de componentes electrónicos

**Solución Sistemática:**
1. **Análisis de tendencias** histórica de parámetros
2. **Inspección física** de actuadores y sensores
3. **Limpieza preventiva** de componentes críticos
4. **Recalibración completa** si deriva > 5% anual

### Problemas de Comunicación

#### Falla de Comunicación con Controlador 1

**Síntomas:**
- Timeout en comandos de apertura
- Variables remotas sin actualizar
- LED de comunicación intermitente

**Diagnóstico Rápido:**
- **Ping BACnet** al dispositivo 10021
- **Verificar carga** de red MS/TP
- **Revisar integridad** física de cable RS-485
- **Comprobar terminaciones** de red (120Ω)

**Procedimiento de Recuperación:**
1. **Reset suave** del controlador (comando BACnet)
2. **Verificar configuración** de red (MAC, velocidad)
3. **Revisar cable** de comunicaciones (A+, B-)
4. **Contact soporte técnico** si persiste > 15 minutos

### Códigos de Error Específicos

| **Código** | **Descripción** | **Prioridad** | **Acción Inmediata** |
|---|---|---|---|
| **CAL001** | Error de linealidad R² < 0.990 | Media | Repetir calibración con condiciones mejoradas |
| **CAL002** | Deriva excesiva (>10% referencia) | Alta | Validar sensor de referencia |
| **CAL003** | Timeout en estabilización | Baja | Aumentar tiempo de espera |
| **CAL004** | Saturación de sensor | Alta | Verificar rango de entrada |
| **COM001** | Pérdida comunicación Controlador 1 | Crítica | Activar procedimiento emergencia |

## 📊 Especificaciones del Sistema de Calibración

### Precisión y Exactitud

| **Parámetro** | **Especificación** | **Condiciones** |
|---|---|---|
| Precisión de calibración | ±2% span | Condiciones estables |
| Repetibilidad | ±1% span | Mismas condiciones |
| Linealidad mínima (R²) | 0.995 | Rango 20-90% apertura |
| Deriva máxima anual | <5% parámetros | Uso normal |
| Tiempo estabilización | 60±30 segundos | Por punto de calibración |
| Resolución de medición | 0.1 CFM | Caudales > 50 CFM |

### Capacidades Operativas

| **Característica** | **Especificación** |
|---|---|
| VAVs calibrables simultáneamente | 1 (secuencial automática) |
| Puntos de calibración por VAV | 5-10 configurables |
| Muestras por punto | 10-100 configurables |
| Duración sesión típica | 15-25 minutos/VAV |
| Sesiones diarias máximas | 20 (operación continua) |
| Almacenamiento de datos | 1 año histórico |

### Condiciones Ambientales de Operación

| **Parámetro** | **Rango Operativo** | **Rango Óptimo** |
|---|---|---|
| Temperatura ambiente | 15-35°C | 20-25°C |
| Humedad relativa | 10-80% RH | 40-60% RH |
| Presión estática estabilidad | ±0.1" WC | ±0.05" WC |
| Variación temperatura suministro | ±5°C | ±2°C |
| Tiempo operación continua | 8 horas máximo | 4 horas recomendado |

## 🔗 Documentación y Enlaces

### Procedimientos de Calibración
- [Manual de Calibración HVAC v2.1](../Documentación/Guías/Manual-Calibracion-HVAC-v2.1.pdf)
- [Protocolo Estadístico KMC-Excel](../Documentación/Guías/Protocolo-Estadistico-KMC-Excel.pdf)
- [Certificación de Sensores de Referencia](../Documentación/Certificados/Sensores-Referencia-2025.pdf)

### Análisis y Reportes
- [Plantilla Excel de Análisis](../Documentación/Plantillas/Plantilla-Analisis-Calibracion.xlsx)
- [Formato de Certificado de Calibración](../Documentación/Plantillas/Certificado-Calibracion.docx)
- [Reporte de Tendencias Históricas](../Documentación/Reportes/Tendencias-Calibracion-2024.pdf)

### Documentación Técnica Hardware
- [Manual KMC BAC-5901C](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/)
- [Configuración Avanzada Variables AV](../Documentación/Guías/Configuracion-Variables-AV.pdf)
- [Diagrama de Red Calibración](../Documentación/Diagramas/Red-BACnet-Calibracion.pdf)

### Procedimientos de Emergencia
- [Plan de Contingencia Calibración](../Documentación/Emergencia/Plan-Contingencia-Calibracion.pdf)
- [Contactos Soporte Técnico 24/7](../Documentación/Contactos/Soporte-Tecnico-24-7.pdf)

---

**Última actualización:** Septiembre 2025  
**Versión documento:** 2.0.0  
**Sistema de calibración certificado:** ISO 17025:2017  
**Elaborado por:** Charlie & Claude - Equipo INNES Aire  
**Próxima revisión:** Marzo 2026  
**Próxima calibración sistema:** Enero 2026