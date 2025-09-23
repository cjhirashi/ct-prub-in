# 🧪 Laboratorio de Pruebas HVAC - INNES Aire

![Status](https://img.shields.io/badge/status-operativo-green)
![Controllers](https://img.shields.io/badge/controladores-2-blue)
![VAVs](https://img.shields.io/badge/cajas_VAV-15-orange)
![Plenums](https://img.shields.io/badge/plenums-7-purple)
![Protocol](https://img.shields.io/badge/protocol-BACnet_MS/TP-blue)

> **Laboratorio especializado** para pruebas de rendimiento, calibración y desarrollo de componentes HVAC bajo condiciones controladas

---

## 🎯 **Propósito del Laboratorio**

### **Misión Principal**
El Cuarto de Pruebas es el **centro de I+D de INNES Aire** para:
- 🔬 **Pruebas de Rendimiento**: Evaluación de rejillas, difusores y componentes VAV
- ⚖️ **Calibración de Precisión**: Ajuste de sensores de flujo y presión diferencial  
- 📊 **Validación de Productos**: Verificación de especificaciones bajo normas
- 🛠️ **Desarrollo de Prototipos**: Testing de nuevas soluciones HVAC

### **Capacidades Técnicas**
- **Rango de Caudales**: 50-1500 CFM por VAV
- **Precisión de Medición**: ±2% en condiciones controladas
- **Control de Presión**: 0.1-2.5 inWC con resolución de 0.01 inWC
- **Velocidades de Aire**: 100-2000 FPM en 7 puntos simultáneos

---

## 🏗️ **Arquitectura del Sistema**

### **Distribución de Plenums y VAVs**

<table>
<tr>
<td width="50%">

#### **🌪️ Plenums de Suministro**
| **Plenum** | **VAVs** | **Función** | **DP Sensores** |
|------------|----------|-------------|-----------------|
| **P1** | 3 VAVs | Referencia/Calibración | ✅ 2 sensores |
| **P2** | 2 VAVs | Pruebas estándar | ✅ 1 sensor |
| **P3** | 1 VAV | Componente individual | ❌ Sin sensor |
| **P4** | 3 VAVs | Batería de pruebas | ✅ 1 sensor |
| **P5** | 2 VAVs | Evaluación comparativa | ✅ 1 sensor |
| **P6** | 2 VAVs | Validación final | ✅ 1 sensor |

</td>
<td width="50%">

#### **🔄 Sistema de Retorno**
| **Plenum** | **VAVs** | **Función** | **DP Sensores** |
|------------|----------|-------------|-----------------|
| **PR7** | 2 VAVs | Balance de presión | ✅ 1 sensor |

#### **📏 Tipos de VAV**
- **🔴 Chica (VC)**: 50-400 CFM
- **🟡 Mediana (VM)**: 200-800 CFM  
- **🟢 Grande (VG)**: 500-1500 CFM

</td>
</tr>
</table>

### **Distribución por Controlador**

```
🎛️ Controlador 1 (10021)          🎛️ Controlador 2 (10022)
├── P1: 3 VAVs (VM,VG,VC)          ├── Calibración Avanzada
├── P2: 2 VAVs (VM,VG)             ├── Presión Diferencial Remota
├── P3: 1 VAV (VG)                 ├── Algoritmos de Ajuste
├── P4: 3 VAVs (VM,VG,VC)          └── Validación de Datos
├── P5: 2 VAVs (VC,VG)
├── P6: 2 VAVs (VG,VM)
└── PR7: 2 VAVs (VC,VG)
```

---

## 🖧 **Red de Control**

### **Controladores DDC**

| **Controlador** | **Modelo** | **DI** | **MAC** | **I/O** | **Función Principal** |
|-----------------|------------|--------|---------|---------|----------------------|
| **CP-CTRL-1** | KMC BAC-5901C | `10021` | `21` | 24/24 | Control VAVs + Sensores |
| **CP-CTRL-2** | KMC BAC-5901C | `10022` | `22` | 24/24 | Calibración + Algoritmos |

### **Expansiones I/O**
- **2x KMC CAN-5901** por controlador (16 I/O adicionales c/u)
- **Total**: 48 entradas + 48 salidas por controlador

### **Sensores Independientes**
| **Sensor** | **Modelo** | **DI** | **MAC** | **Función** |
|------------|------------|--------|---------|-------------|
| SPT1_CP | Veris TWLPXXX4E4 | `133025` | `25` | Temperatura ambiente 1 |
| SPT2_CP | Veris TWLPXXX4E4 | `133026` | `26` | Temperatura ambiente 2 |
| SPT3_CP | Veris TWLPXXX4E4 | `133023` | `23` | Temperatura ambiente 3 |
| SPT4_CP | Veris TWLPXXX4E4 | `133024` | `24` | Temperatura ambiente 4 |

---

## ⚙️ **Sistemas de Medición**

### **🌡️ Sensores de Temperatura**
- **Ambiente**: 4 puntos independientes (18-28°C ±0.1°C)
- **Suministro**: 1 sensor principal (5-35°C ±0.2°C)

### **💨 Medición de Velocidad**
- **Árbol Fijo**: 7 sensores en formación (100-2000 FPM)
- **Sensor Móvil**: 1 unidad portable para validación
- **Precisión**: ±3% de lectura + 5 FPM

### **📊 Presión Diferencial**
- **P1**: 2 sensores (caída de presión + referencia)
- **P2,P4,P5,P6,PR7**: 1 sensor cada uno
- **Rango**: 0-2.5 inWC con precisión ±1%

---

## 🔧 **Programas de Control**

### **Controlador 1 (10021) - Operación Principal**

| **Programa** | **Función** | **Variables Clave** | **Ejecución** |
|--------------|-------------|-------------------|---------------|
| **PRG1_SENSORES** | Cálculo de caudales VAV | 15 VAVs + factores K | Continua |
| **PRG2_VAVS** | Control compuertas | Demandas + posiciones | 5 segundos |
| **PRG3_PLENUMS** | Gestión por plenum | Selector + límites | Continua |
| **PRG4_DEMANDA** | Algoritmo PI | 4 lazos de control | 1 segundo |
| **PRG5_UMA** | Sincronización UMA | Estados + puntos BACnet | 30 segundos |

### **Controlador 2 (10022) - Calibración Avanzada**

| **Programa** | **Función** | **Variables Clave** | **Ejecución** |
|--------------|-------------|-------------------|---------------|
| **PRG1_CALIBRACION** | Sistema híbrido KMC-Excel | Multiplicadores + offsets | Manual |

---

## 🧮 **Procedimientos de Calibración**

### **🔄 Metodología Híbrida (KMC + Excel)**

#### **Fase 1: Adquisición (Sistema KMC)**
1. **Selección de caja VAV** mediante interfaz HMI
2. **Configuración de apertura** (5 puntos: 20%, 40%, 60%, 80%, 100%)
3. **Muestreo automatizado** (5-20 muestras por punto)
4. **Estabilización** automática entre mediciones

#### **Fase 2: Análisis (Excel Externo)**
1. **Exportación de datos** completos del KMC
2. **Análisis estadístico** con regresión lineal
3. **Cálculo de coeficientes** (a = multiplicador, b = offset)
4. **Validación del modelo** (R² > 0.95 requerido)

#### **Fase 3: Implementación (KMC)**
1. **Carga de parámetros** finales: `Q_calibrado = a × Q_sistema + b`
2. **Pruebas de validación** operacional
3. **Documentación** de resultados

### **📈 Criterios de Aceptación**
- **Precisión**: Error < 5% en rango operacional
- **Linealidad**: R² > 0.95 en modelo de calibración
- **Repetibilidad**: CV < 3% entre ciclos de medición

---

## 🎛️ **Manual de Operación**

### **🚀 Inicio de Pruebas**

#### **Procedimiento Estándar**
1. **Verificar estado del sistema** en HMI principal
2. **Seleccionar plenum** objetivo (MSV1: 1-6)
3. **Activar sistema** de control (BV1: ON)
4. **Configurar setpoints** de caudal por VAV
5. **Monitorear estabilización** (2-5 minutos)

#### **Controles Principales**
- **PLENUM** (MSV1): Selector de plenum activo
- **SS_CP** (BV1): Activación sistema cuarto pruebas
- **Setpoints individuales**: VG_Q_SP, VM_Q_SP, VC_Q_SP

### **📊 Monitoreo en Tiempo Real**
- **Caudales actuales**: Lectura directa por VAV
- **Posiciones de compuertas**: 0-100% apertura
- **Presiones diferenciales**: Por plenum activo
- **Estados de compuertas de bloqueo**: Abiertas/Cerradas

### **⚠️ Límites de Seguridad**
- **Presión máxima**: 2.5 inWC (alarma a 2.3 inWC)
- **Velocidad máxima**: 2000 FPM (alarma a 1900 FPM)
- **Temperatura operación**: 15-35°C ambiente

---

## 📂 **Estructura de Documentación**

```
📂 Cuarto-de-Pruebas/
├── 📄 README.md                    # Este archivo (visión general)
├── 📁 Controlador-1/               # DDC 10021 - Control principal
│   ├── 📄 README.md                # Especificaciones técnicas
│   ├── 📁 PRG1_SENSORES/          # Cálculo de caudales
│   ├── 📁 PRG2_VAVS/              # Control de compuertas
│   ├── 📁 PRG3_PLENUMS/           # Gestión por plenum
│   ├── 📁 PRG4_DEMANDA/           # Algoritmos PI
│   └── 📁 PRG5_UMA/               # Sincronización UMA
├── 📁 Controlador-2/               # DDC 10022 - Calibración
│   ├── 📄 README.md                # Especificaciones técnicas
│   └── 📁 PRG1_CALIBRACION/       # Sistema híbrido
├── 📁 Sensores/                    # Especificaciones de sensores
├── 📁 Procedimientos/              # Guías operacionales
│   ├── 📄 calibracion-vav.md      # Procedimiento calibración
│   ├── 📄 operacion-diaria.md     # Rutinas operacionales
│   └── 📄 mantenimiento.md        # Rutinas de mantenimiento
├── 📁 Documentación/              # Recursos técnicos
│   ├── 📁 Diagramas/              # P&ID, esquemas eléctricos
│   ├── 📁 Manuales/               # Manuales de equipos
│   └── 📁 Especificaciones/       # Hojas técnicas
└── 📁 Datos/                      # Registros y bases de datos
    ├── 📁 Calibraciones/          # Histórico de calibraciones
    ├── 📁 Pruebas/                # Resultados de pruebas
    └── 📁 Reportes/               # Informes técnicos
```

---

## 🔗 **Enlaces Rápidos**

### **🎛️ Interfaces de Control**
- **[HMI Principal](http://10.0.0.251:47808)** - Supervisión centralizada LVIS
- **[Controlador 1](bacnet://10021)** - DDC principal (VAVs + Sensores)
- **[Controlador 2](bacnet://10022)** - DDC calibración avanzada

### **📋 Documentación Técnica**
- **[Manual de Calibración](./Procedimientos/calibracion-vav.md)** - Proceso completo
- **[Guía de Operación](./Procedimientos/operacion-diaria.md)** - Uso diario
- **[Especificaciones de VAVs](./Documentación/Especificaciones/vav-specs.md)** - Detalles técnicos
- **[Diagramas P&ID](./Documentación/Diagramas/)** - Esquemas del sistema

### **⚡ Procedimientos de Emergencia**
- **[Parada de Emergencia](./Procedimientos/emergencia.md#parada)** - Protocolo seguro
- **[Recuperación de Sistema](./Procedimientos/emergencia.md#recuperacion)** - Reinicio controlado
- **[Contactos 24/7](./Procedimientos/emergencia.md#contactos)** - Soporte técnico

---

## ⚠️ **Seguridad y Precauciones**

### **🚨 ANTES de cualquier intervención**
1. **Verificar estado en HMI** - Sistema en modo manual
2. **Parar todas las VAVs** - Cerrar compuertas de bloqueo
3. **Desenergizar controladores** - Interruptor en tablero principal
4. **Verificar ausencia de presión** - Manómetros en 0 inWC
5. **Colocar LOTO** - Procedimiento de bloqueo/etiquetado

### **🔧 EPP Obligatorio**
- **Gafas de seguridad** - Protección contra partículas
- **Guantes de trabajo** - Manipulación de componentes
- **Calzado antideslizante** - Seguridad en área de pruebas
- **Casco** - Si hay trabajo en alturas >2m

### **⚡ Riesgos Eléctricos**
- **Tensión de control**: 24 VAC/DC en todos los circuitos
- **Alimentación principal**: 120 VAC en actuadores
- **Tablero principal**: Identificado con etiquetas de seguridad
- **Contacto de emergencia**: Supervisor técnico Ext. 101

---

## 📊 **Indicadores de Rendimiento**

<div align="center">

![Precision](https://img.shields.io/badge/precisión_medición-±2%25-green)
![Uptime](https://img.shields.io/badge/disponibilidad-98.5%25-blue)
![Calibration](https://img.shields.io/badge/calibraciones_mes-12-orange)
![Tests](https://img.shields.io/badge/pruebas_completadas-156-purple)

</div>

### **📈 Estadísticas del Mes**
- **Pruebas realizadas**: 156 componentes evaluados
- **Calibraciones**: 12 VAVs recalibradas
- **Tiempo promedio de prueba**: 45 minutos por componente
- **Eficiencia operacional**: 92% del tiempo planificado

---

## 🔄 **Historial de Versiones**

| **Versión** | **Fecha** | **Cambios Principales** | **Responsable** |
|-------------|-----------|------------------------|-----------------|
| 2.1 | Sep 2025 | Reestructuración completa documentación | Equipo INNES |
| 2.0 | Ago 2025 | Sistema híbrido calibración KMC-Excel | C. Jiménez |
| 1.5 | Jul 2025 | Integración sensores Veris independientes | Equipo Técnico |
| 1.0 | Jun 2025 | Implementación inicial laboratorio | INNES Aire |

---

<div align="center">

**🧪 Laboratorio de Pruebas HVAC - INNES Aire**  
*Desarrollando el futuro de los sistemas de climatización*

[![Manual Operación](https://img.shields.io/badge/📖-Manual_Operación-blue)](./Procedimientos/operacion-diaria.md)
[![Especificaciones](https://img.shields.io/badge/📋-Especificaciones-green)](./Documentación/Especificaciones/)
[![Soporte 24/7](https://img.shields.io/badge/📞-Soporte_24/7-red)](./Procedimientos/emergencia.md#contactos)

</div>