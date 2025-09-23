# 📊 Especificaciones de Caudales VAV - Cuarto de Pruebas INNES

![Status](https://img.shields.io/badge/documento-vigente-green)
![VAVs](https://img.shields.io/badge/VAVs_totales-15-blue)
![Plenums](https://img.shields.io/badge/plenums-7-orange)
![Revision](https://img.shields.io/badge/revisión-2.0-purple)

> **Documento de referencia técnica** con rangos operacionales, límites de seguridad y caudales de ajuste para todas las VAVs del sistema

---

## 📋 **Información del Documento**

| **Parámetro** | **Valor** | **Observaciones** |
|---------------|-----------|-------------------|
| **Fecha creación** | Septiembre 2025 | Basado en PRG3_PLENUMS v1.5.0 |
| **Responsable técnico** | Carlos Jiménez Hirashi | @cjhirashi |
| **Sistema origen** | Controlador 10021 | Constantes internas programa |
| **Última actualización** | 27/MAR/2025 | Sincronizada con código operativo |

---

## 🎯 **Resumen Ejecutivo por Tipo de VAV**

### **Rangos Generales de Operación**

| **Tipo VAV** | **Rango Típico (CFM)** | **Aplicación** | **Cantidad en Sistema** |
|--------------|------------------------|----------------|-------------------------|
| **🔴 Chica (VC)** | 75 - 300 | Pruebas componentes pequeños | 5 VAVs |
| **🟡 Mediana (VM)** | 275 - 850 | Pruebas componentes estándar | 4 VAVs |
| **🟢 Grande (VG)** | 575 - 4000 | Pruebas componentes grandes | 6 VAVs |

### **Distribución por Plenum**
- **Total VAVs**: 15 unidades distribuidas en 7 plenums
- **Plenum con mayor capacidad**: P5 (hasta 4300 CFM combinado)
- **Plenum de referencia**: P1 (3 VAVs, ideal para calibración)
- **Plenum de retorno**: PR7 (balance del sistema)

---

## 🏭 **Especificaciones por Plenum**

### **PLENUM 1 - Referencia y Calibración**
*3 VAVs - Configuración completa para pruebas estándar*

| **VAV** | **Tipo** | **Caudal Mínimo** | **Caudal Máximo** | **Rango Operativo** | **Observaciones** |
|---------|----------|-------------------|-------------------|---------------------|-------------------|
| **P1_VM** | Mediana | **350 CFM** | **850 CFM** | 500 CFM | VAV principal calibración |
| **P1_VG** | Grande | **1100 CFM** | **3000 CFM** | 1900 CFM | Pruebas componentes grandes |
| **P1_VC** | Chica | **75 CFM** | **200 CFM** | 125 CFM | Pruebas precisión baja |

**Caudal Total P1**: 1525 - 4050 CFM  
**Aplicación**: Plenum de referencia para calibración de sensores

---

### **PLENUM 2 - Configuración Estándar**
*2 VAVs - Pruebas comparativas*

| **VAV** | **Tipo** | **Caudal Mínimo** | **Caudal Máximo** | **Rango Operativo** | **Observaciones** |
|---------|----------|-------------------|-------------------|---------------------|-------------------|
| **P2_VM** | Mediana | **275 CFM** | **650 CFM** | 375 CFM | Reducido vs P1_VM |
| **P2_VG** | Grande | **850 CFM** | **2000 CFM** | 1150 CFM | Reducido vs P1_VG |

**Caudal Total P2**: 1125 - 2650 CFM  
**Aplicación**: Pruebas con menores caudales, validación cruzada

---

### **PLENUM 3 - Configuración Simple**
*1 VAV - Pruebas individuales*

| **VAV** | **Tipo** | **Caudal Mínimo** | **Caudal Máximo** | **Rango Operativo** | **Observaciones** |
|---------|----------|-------------------|-------------------|---------------------|-------------------|
| **P3_VG** | Grande | **575 CFM** | **1350 CFM** | 775 CFM | Rango intermedio |

**Caudal Total P3**: 575 - 1350 CFM  
**Aplicación**: Pruebas de componente único, análisis individual

---

### **PLENUM 4 - Configuración Completa**
*3 VAVs - Batería de pruebas*

| **VAV** | **Tipo** | **Caudal Mínimo** | **Caudal Máximo** | **Rango Operativo** | **Observaciones** |
|---------|----------|-------------------|-------------------|---------------------|-------------------|
| **P4_VM** | Mediana | **350 CFM** | **850 CFM** | 500 CFM | Igual a P1_VM |
| **P4_VG** | Grande | **1100 CFM** | **3000 CFM** | 1900 CFM | Igual a P1_VG |
| **P4_VC** | Chica | **75 CFM** | **200 CFM** | 125 CFM | Igual a P1_VC |

**Caudal Total P4**: 1525 - 4050 CFM  
**Aplicación**: Réplica de P1 para validación y pruebas paralelas

---

### **PLENUM 5 - Alta Capacidad**
*2 VAVs - Pruebas de máximo rendimiento*

| **VAV** | **Tipo** | **Caudal Mínimo** | **Caudal Máximo** | **Rango Operativo** | **Observaciones** |
|---------|----------|-------------------|-------------------|---------------------|-------------------|
| **P5_VG** | Grande | **1500 CFM** | **4000 CFM** | 2500 CFM | **Máxima capacidad** |
| **P5_VC** | Chica | **125 CFM** | **300 CFM** | 175 CFM | Ampliada vs otras VC |

**Caudal Total P5**: 1625 - 4300 CFM  
**Aplicación**: Pruebas de alta demanda, componentes industriales

---

### **PLENUM 6 - Configuración Estándar**
*2 VAVs - Pruebas finales*

| **VAV** | **Tipo** | **Caudal Mínimo** | **Caudal Máximo** | **Rango Operativo** | **Observaciones** |
|---------|----------|-------------------|-------------------|---------------------|-------------------|
| **P6_VM** | Mediana | **350 CFM** | **850 CFM** | 500 CFM | Estándar mediana |
| **P6_VG** | Grande | **1100 CFM** | **3000 CFM** | 1900 CFM | Estándar grande |

**Caudal Total P6**: 1450 - 3850 CFM  
**Aplicación**: Pruebas de validación final, verificación QC

---

### **PLENUM R7 - Retorno y Balance**
*2 VAVs - Control de presión sistema*

| **VAV** | **Tipo** | **Caudal Mínimo** | **Caudal Máximo** | **Rango Operativo** | **Observaciones** |
|---------|----------|-------------------|-------------------|---------------------|-------------------|
| **PR7_VG** | Grande | **1100 CFM** | **3000 CFM** | 1900 CFM | Balance principal |
| **PR7_VC** | Chica | **75 CFM** | **200 CFM** | 125 CFM | Control fino presión |

**Caudal Total PR7**: 1175 - 3200 CFM  
**Aplicación**: Mantenimiento balance presión, extracción controlada

---

## 📈 **Análisis Técnico del Sistema**

### **Capacidades Máximas por Plenum**

| **Plenum** | **Caudal Máximo** | **VAVs** | **Configuración** | **Uso Típico** |
|------------|-------------------|----------|-------------------|----------------|
| **P5** | 4300 CFM | 2 | VG + VC ampliada | Pruebas alta demanda |
| **P1** | 4050 CFM | 3 | VG + VM + VC | Calibración/referencia |
| **P4** | 4050 CFM | 3 | VG + VM + VC | Validación P1 |
| **P6** | 3850 CFM | 2 | VG + VM | Pruebas finales |
| **PR7** | 3200 CFM | 2 | VG + VC | Balance sistema |
| **P2** | 2650 CFM | 2 | VG + VM reducidos | Caudales menores |
| **P3** | 1350 CFM | 1 | VG individual | Pruebas unitarias |

### **Distribución de Rangos Operativos**

#### **VAVs Chicas (VC) - 5 unidades**
- **Rango estándar**: 75-200 CFM (4 VAVs)
- **Rango ampliado**: 125-300 CFM (1 VAV en P5)
- **Aplicación**: Componentes pequeños, control fino

#### **VAVs Medianas (VM) - 4 unidades**
- **Rango estándar**: 350-850 CFM (3 VAVs)
- **Rango reducido**: 275-650 CFM (1 VAV en P2)
- **Aplicación**: Componentes estándar industria

#### **VAVs Grandes (VG) - 6 unidades**
- **Rango alto**: 1100-3000 CFM (4 VAVs)
- **Rango máximo**: 1500-4000 CFM (1 VAV en P5)
- **Rango intermedio**: 575-1350 CFM (1 VAV en P3)
- **Rango medio**: 850-2000 CFM (1 VAV en P2)

---

## ⚙️ **Configuraciones de Prueba Recomendadas**

### **Configuración 1: Calibración Inicial**
- **Plenum activo**: P1
- **VAVs en uso**: P1_VM (50%), P1_VG (40%), P1_VC (60%)
- **Caudal objetivo**: 1200 + 525 + 120 = 1845 CFM
- **Propósito**: Establecer línea base calibración

### **Configuración 2: Prueba de Capacidad**
- **Plenum activo**: P5
- **VAVs en uso**: P5_VG (80%), P5_VC (70%)
- **Caudal objetivo**: 3200 + 210 = 3410 CFM
- **Propósito**: Verificar máxima capacidad sistema

### **Configuración 3: Prueba de Precisión**
- **Plenum activo**: P3
- **VAVs en uso**: P3_VG (30%)
- **Caudal objetivo**: 575-800 CFM
- **Propósito**: Mediciones precisión alta

### **Configuración 4: Validación Cruzada**
- **Plenums activos**: P1 vs P4 (secuencial)
- **VAVs en uso**: Configuración idéntica
- **Caudal objetivo**: Mismo setpoint ambos
- **Propósito**: Verificar consistencia entre plenums

---

## 🔧 **Procedimientos de Ajuste**

### **Secuencia de Configuración de Caudales**

#### **Paso 1: Verificación de Límites**
```
VG_Q_SP = MIN(MAX(VG_Q_SP, VG_MIN), VG_MAX)
VM_Q_SP = MIN(MAX(VM_Q_SP, VM_MIN), VM_MAX)  
VC_Q_SP = MIN(MAX(VC_Q_SP, VC_MIN), VC_MAX)
```

#### **Paso 2: Selección de Plenum**
- **PLENUM** (MSV1): Selector 1-6
- **Límites automáticos**: Sistema asigna MIN/MAX según plenum
- **Variables activas**: VG_Q, VM_Q, VC_Q actualizadas

#### **Paso 3: Control de Setpoints**
- **Entrada operador**: AV107-AV111 (setpoints)
- **Limitación automática**: Programa PRG3 aplica límites
- **Escritura validada**: Valores limitados escritos @prioridad 8

### **Puntos de Control Críticos**

| **Variable** | **Punto BACnet** | **Función** | **Acceso** |
|--------------|------------------|-------------|------------|
| **VG_Q_SP** | AV107 | Setpoint VAV Grande | R/W @8 |
| **VM_Q_SP** | AV108 | Setpoint VAV Mediana | R/W @8 |
| **VC_Q_SP** | AV109 | Setpoint VAV Chica | R/W @8 |
| **VG_MIN** | AV112 | Límite mínimo dinámico | Solo lectura |
| **VG_MAX** | AV113 | Límite máximo dinámico | Solo lectura |
| **PLENUM** | MSV1 | Selector plenum activo | R/W |

---

## ⚠️ **Límites de Seguridad y Alarmas**

### **Alarmas por Exceso de Rango**

#### **VAVs Chicas (VC)**
- **Alarma baja**: < 50 CFM 
- **Límite mínimo**: 75-125 CFM (según plenum)
- **Límite máximo**: 200-300 CFM (según plenum)
- **Alarma alta**: > 350 CFM

#### **VAVs Medianas (VM)**
- **Alarma baja**: < 200 CFM
- **Límite mínimo**: 275-350 CFM (según plenum)
- **Límite máximo**: 650-850 CFM (según plenum)
- **Alarma alta**: > 950 CFM

#### **VAVs Grandes (VG)**
- **Alarma baja**: < 400 CFM
- **Límite mínimo**: 575-1500 CFM (según plenum)
- **Límite máximo**: 1350-4000 CFM (según plenum)  
- **Alarma alta**: > 4500 CFM

### **Protecciones del Sistema**
- **Limitación automática**: Setpoints mantenidos dentro de MIN/MAX
- **Validación de escritura**: Solo valores válidos @prioridad 8
- **Anti-bloqueo**: Activación forzada VAV si todas inactivas
- **Balance de retorno**: PR7 compensa automáticamente

---

## 📊 **Tablas de Referencia Rápida**

### **Caudales Mínimos por Plenum (CFM)**

| **VAV** | **P1** | **P2** | **P3** | **P4** | **P5** | **P6** | **PR7** |
|---------|--------|--------|--------|--------|--------|--------|---------|
| **VC** | 75 | - | - | 75 | 125 | - | 75 |
| **VM** | 350 | 275 | - | 350 | - | 350 | - |
| **VG** | 1100 | 850 | 575 | 1100 | 1500 | 1100 | 1100 |

### **Caudales Máximos por Plenum (CFM)**

| **VAV** | **P1** | **P2** | **P3** | **P4** | **P5** | **P6** | **PR7** |
|---------|--------|--------|--------|--------|--------|--------|---------|
| **VC** | 200 | - | - | 200 | 300 | - | 200 |
| **VM** | 850 | 650 | - | 850 | - | 850 | - |
| **VG** | 3000 | 2000 | 1350 | 3000 | 4000 | 3000 | 3000 |

### **Rangos Operativos por Plenum (CFM)**

| **VAV** | **P1** | **P2** | **P3** | **P4** | **P5** | **P6** | **PR7** |
|---------|--------|--------|--------|--------|--------|--------|---------|
| **VC** | 125 | - | - | 125 | 175 | - | 125 |
| **VM** | 500 | 375 | - | 500 | - | 500 | - |
| **VG** | 1900 | 1150 | 775 | 1900 | 2500 | 1900 | 1900 |

---

## 🔗 **Referencias Técnicas**

### **Documentos Relacionados**
- **[Lista Puntos Controlador 1](./puntos-controlador-1.md)** - Variables BACnet completas
- **[PRG3 Documentación](./Controlador-1/PRG3/README.md)** - Lógica programa plenums
- **[Procedimientos Calibración](./Procedimientos/calibracion-vav.md)** - Uso de caudales
- **[Manual Operación Diaria](./Procedimientos/operacion-diaria.md)** - Configuraciones típicas

### **Código Fuente**
- **Archivo**: `PRG3_PLENUMS.txt`
- **Controlador**: DDC 10021
- **Versión**: 1.5.0
- **Autor**: Carlos Jiménez Hirashi (@cjhirashi)

### **Historial de Cambios**
- **v2.0** (Sep 2025): Documentación completa especificaciones
- **v1.5** (Mar 2025): Actualización límites P5, ajustes precisión
- **v1.0** (Inicio): Implementación inicial sistema

---

<div align="center">

**📊 Especificaciones de Caudales VAV - INNES Aire**  
*Documento técnico de referencia para ajustes y configuración operacional*

[![Código Fuente](https://img.shields.io/badge/📄-PRG3_PLENUMS-blue)](./Controlador-1/PRG3/)
[![Manual Operación](https://img.shields.io/badge/📖-Manual_Operación-green)](./Procedimientos/operacion-diaria.md)
[![Soporte Técnico](https://img.shields.io/badge/📞-Soporte_24/7-red)](../README.md#contactos-emergencia)

</div>