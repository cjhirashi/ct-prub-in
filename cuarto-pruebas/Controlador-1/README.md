# SISTEMA DE CONTROL CUARTO DE PRUEBAS - CONTROLADOR 1

![badge-status](https://img.shields.io/badge/status-operativo-green)
![badge-protocol](https://img.shields.io/badge/protocol-BACnet%20MS/TP-blue)
![badge-controller](https://img.shields.io/badge/controller-KMC%20BAC--5901C-orange)
![badge-version](https://img.shields.io/badge/version-2.0.0-blue)

## 📖 Descripción General

El **Controlador 1** del Cuarto de Pruebas gestiona de forma integral **15 Cajas VAV** distribuidas en **7 Plenums** especializados, diseñado para realizar pruebas de rendimiento precisas en componentes de ventilación como rejillas, difusores y sistemas VAV bajo condiciones controladas.

Este sistema forma parte del laboratorio de pruebas de INNES Aire, proporcionando **medición, calibración y control dinámico** de flujos de aire con alta precisión para validación de componentes HVAC.

### Arquitectura del Sistema

```plaintext
┌─────────────────────────────────────────────────────────────┐
│                    CONTROLADOR 1                           │
│                KMC BAC-5901C (DI: 10021)                   │
│                   MAC Address: 21                          │
└─────────────────┬───────────────────────────────────────────┘
                  │
                  ├── Plenum 1 ──── VAV 1, VAV 2, VAV 3
                  ├── Plenum 2 ──── VAV 4, VAV 5
                  ├── Plenum 3 ──── VAV 6, VAV 7, VAV 8
                  ├── Plenum 4 ──── VAV 9, VAV 10
                  ├── Plenum 5 ──── VAV 11, VAV 12
                  ├── Plenum 6 ──── VAV 13, VAV 14
                  └── Plenum 7 ──── VAV 15
```

## 🖧 Información del Controlador

### Hardware Principal

| **Componente** | **Especificación** | **Descripción** |
|---|---|---|
| **Controlador** | KMC BAC-5901C | Controlador principal de propósito general |
| **Entradas/Salidas** | 8 UI / 8 UO | Entradas y salidas universales integradas |
| **Puerto de comunicación** | RS-485 | BACnet MS/TP nativo |
| **Alimentación** | 24 VAC/DC | Fuente de alimentación estándar HVAC |

### Módulo de Expansión

| **Componente** | **Especificación** | **Descripción** |
|---|---|---|
| **Módulo** | KMC CAN-5901 | Expansión de E/S adicional |
| **Entradas/Salidas** | 8 UI / 8 UO | Expansión de capacidad de control |
| **Conectividad** | CAN Bus | Comunicación con controlador principal |
| **Alimentación** | 24 VAC/DC | Fuente independiente requerida |

### Configuración de Red

| **Parámetro** | **Valor** | **Descripción** |
|---|---|---|
| **Device Instance (DI)** | `10021` | Identificador único BACnet |
| **MAC Address** | `21` | Dirección física en red MS/TP |
| **Protocolo** | BACnet MS/TP | Protocolo de comunicación |
| **Velocidad** | 38,400 bps | Velocidad estándar de comunicación |
| **Entradas Totales** | 16 | 8 controlador + 8 expansión |
| **Salidas Totales** | 16 | 8 controlador + 8 expansión |

## 📋 Lista de Puntos de Control

### Puntos de Entrada Analógica (AI)

| **Punto** | **Descripción** | **Unidad** | **Rango** | **Ubicación** |
|---|---|---|---|---|
| AI01 | Sensor caudal VAV-01 | CFM | 0-500 | Plenum 1 |
| AI02 | Sensor caudal VAV-02 | CFM | 0-500 | Plenum 1 |
| AI03 | Sensor caudal VAV-03 | CFM | 0-500 | Plenum 1 |
| AI04 | Sensor caudal VAV-04 | CFM | 0-300 | Plenum 2 |
| AI05 | Sensor caudal VAV-05 | CFM | 0-300 | Plenum 2 |
| AI06 | Sensor caudal VAV-06 | CFM | 0-400 | Plenum 3 |
| AI07 | Sensor caudal VAV-07 | CFM | 0-400 | Plenum 3 |
| AI08 | Sensor caudal VAV-08 | CFM | 0-400 | Plenum 3 |

### Puntos de Salida Analógica (AO)

| **Punto** | **Descripción** | **Unidad** | **Rango** | **Función** |
|---|---|---|---|---|
| AO01 | Control compuerta VAV-01 | % | 0-100 | Modulación proporcional |
| AO02 | Control compuerta VAV-02 | % | 0-100 | Modulación proporcional |
| AO03 | Control compuerta VAV-03 | % | 0-100 | Modulación proporcional |
| AO04 | Control compuerta VAV-04 | % | 0-100 | Modulación proporcional |
| AO05 | Control compuerta VAV-05 | % | 0-100 | Modulación proporcional |
| AO06 | Control compuerta VAV-06 | % | 0-100 | Modulación proporcional |
| AO07 | Control compuerta VAV-07 | % | 0-100 | Modulación proporcional |
| AO08 | Control compuerta VAV-08 | % | 0-100 | Modulación proporcional |

### Puntos Binarios de Entrada (BI)

| **Punto** | **Descripción** | **Estado** | **Función** |
|---|---|---|---|
| BI01 | Estado plenum 1 activo | ON/OFF | Confirmación operativa |
| BI02 | Estado plenum 2 activo | ON/OFF | Confirmación operativa |
| BI03 | Estado plenum 3 activo | ON/OFF | Confirmación operativa |
| BI04 | Alarma presión diferencial | ALARM/NORMAL | Protección sistema |

### Puntos Binarios de Salida (BO)

| **Punto** | **Descripción** | **Estado** | **Función** |
|---|---|---|---|
| BO01 | Activación plenum 1 | ON/OFF | Control maestro plenum |
| BO02 | Activación plenum 2 | ON/OFF | Control maestro plenum |
| BO03 | Activación plenum 3 | ON/OFF | Control maestro plenum |
| BO04 | Compuerta bloqueo VAV-01 | OPEN/CLOSE | Seguridad operativa |

## 🔄 Programas de Control

### PRG1_SENSORES
**Función:** Cálculo y ajuste de caudales de aire en VAVs múltiples

**Descripción técnica:** Programa especializado en el procesamiento de señales de sensores de presión diferencial para estimar flujos de aire reales. Implementa algoritmos de calibración dinámica que ajustan las mediciones brutas aplicando factores de corrección específicos para cada VAV, compensando variaciones en la instalación y características del ducto.

**Operación:**
- Lectura cíclica de sensores de presión diferencial
- Aplicación de ecuación de flujo: Q = K × √(ΔP)
- Corrección por factores de calibración específicos
- Actualización de valores en tiempo real cada 2 segundos

### PRG2_VAVS
**Función:** Control inteligente de compuertas VAV por demanda

**Descripción técnica:** Sistema de control distribuido que gestiona la apertura de compuertas VAV basado en demandas individuales de ventilación. Utiliza algoritmos PID para mantener setpoints de caudal con respuesta rápida y mínimo overshoot, incorporando compensación por presión estática del plenum.

**Operación:**
- Monitoreo continuo de demanda vs caudal actual
- Control PID con parámetros optimizados por VAV
- Limitación de velocidad de cambio para estabilidad
- Sincronización entre VAVs del mismo plenum

### PRG3_PLENUMS
**Función:** Gestión coordinada de presión y flujo en plenums

**Descripción técnica:** Programa maestro que coordina la operación de múltiples plenums manteniendo condiciones de presión estática óptimas. Implementa estrategias de control de presión diferencial que aseguran distribución uniforme de aire y previenen interacciones negativas entre plenums adyacentes.

**Operación:**
- Control de presión estática por plenum
- Balanceo automático de cargas entre plenums
- Gestión de transiciones suaves entre modos operativos
- Protección contra sobrepresión y vacío excesivo

### PRG4_DEMANDA
**Función:** Control PI de demanda global del sistema

**Descripción técnica:** Algoritmo de control proporcional-integral que gestiona la demanda total del sistema de pruebas. Optimiza la distribución de carga entre diferentes secciones, manteniendo eficiencia energética mientras asegura capacidad de respuesta para cambios rápidos en los requerimientos de prueba.

**Operación:**
- Cálculo de demanda agregada del sistema
- Implementación de control PI con anti-windup
- Distribución proporcional de carga por secciones
- Gestión de límites operativos dinámicos

### PRG5_UMA
**Función:** Interfaz de comunicación con UMA-01

**Descripción técnica:** Módulo de comunicación que actúa como puente entre el sistema de control del cuarto de pruebas y la Unidad de Manejo de Aire principal. Sincroniza datos de estado, transmite setpoints de temperatura y presión, y gestiona comandos de arranque/parada con prioridad específica (Nivel 7) para operación coordinada.

**Operación:**
- Sincronización de estado cada 5 segundos
- Transmisión de setpoints SAT y DP
- Control con prioridad 7 sobre comandos locales UMA
- Monitoreo de interlocks de seguridad

## ⚠️ Seguridad y Precauciones

### Seguridad Eléctrica

⚡ **PELIGRO - RIESGO ELÉCTRICO**
- Desenergizar completamente el controlador antes de realizar conexiones
- Verificar ausencia de voltaje con multímetro calibrado
- Usar EPP: guantes dieléctricos clase 0, gafas de seguridad
- **NUNCA** trabajar en equipos energizados sin autorización específica

### Seguridad Mecánica

🔧 **ADVERTENCIA - COMPONENTES MÓVILES**
- Verificar parada completa de actuadores antes del mantenimiento
- Bloquear compuertas en posición segura durante intervenciones
- Utilizar procedimientos de bloqueo/etiquetado (LOTO)
- Presión máxima de trabajo: 2" WC - no exceder límites operativos

### Seguridad del Sistema

⚠️ **PRECAUCIÓN - INTEGRIDAD DEL PROCESO**
- Validar calibración de sensores antes de pruebas críticas
- Mantener respaldo de configuraciones antes de modificaciones
- Verificar comunicación BACnet antes de operación automática
- Documentar todos los cambios en bitácora del sistema

### Procedimientos de Emergencia

🚨 **PARADA DE EMERGENCIA**
1. Presionar botón de parada de emergencia (si disponible)
2. Desenergizar controlador desde panel principal
3. Cerrar manualmente compuertas VAV críticas
4. Notificar a supervisor de mantenimiento
5. Documentar incidente según procedimiento INNES-HVAC-001

## 📚 Manual de Operación

### Arranque del Sistema

#### Secuencia de Arranque Normal

1. **Verificaciones Previas**
   - Confirmar alimentación 24 VDC estable
   - Verificar comunicación BACnet (LED verde parpadeante)
   - Revisar ausencia de alarmas activas
   - Validar posición de compuertas manuales

2. **Activación Secuencial**
   - Activar controlador principal (DI 10021)
   - Esperar inicialización completa (60 segundos)
   - Verificar comunicación con módulo de expansión
   - Activar programas de control secuencialmente

3. **Pruebas Funcionales**
   - Ejecutar prueba de movimiento de compuertas (10% apertura)
   - Verificar lectura de sensores de caudal (±5% tolerancia)
   - Confirmar respuesta de plenums individualmente
   - Validar comunicación con UMA-01

### Operación en Modo Prueba

#### Configuración de Prueba Individual

1. **Selección de VAV**
   - Acceder a interfaz HMI del controlador
   - Seleccionar VAV específico para prueba
   - Configurar setpoint de caudal deseado
   - Activar modo manual si requerido

2. **Ejecución de Prueba**
   - Iniciar secuencia desde interfaz principal
   - Monitorear estabilización (típico 30-60 segundos)
   - Registrar datos en intervalos de 10 segundos
   - Mantener condiciones estables por mínimo 5 minutos

3. **Finalización**
   - Retornar VAV a posición inicial
   - Desactivar plenum asociado
   - Guardar datos de prueba automáticamente
   - Generar reporte de resultados

### Calibración de Sensores

#### Procedimiento de Calibración de Caudal

1. **Preparación**
   - Instalar caudalímetro de referencia certificado
   - Configurar condiciones estables de presión
   - Registrar condiciones ambientales
   - Preparar hoja de calibración

2. **Proceso de Calibración**
   - Establecer 5 puntos de calibración (20%, 40%, 60%, 80%, 100%)
   - Tomar 10 muestras por punto durante 2 minutos
   - Calcular promedios y desviaciones estándar
   - Aplicar corrección lineal: Q_real = a × Q_sensor + b

3. **Validación**
   - Verificar linealidad (R² > 0.995)
   - Confirmar precisión (±2% en rango operativo)
   - Documentar certificado de calibración
   - Actualizar fecha en sistema

### Mantenimiento Preventivo

#### Rutina Semanal
- Inspección visual de conexiones eléctricas
- Verificación de comunicación BACnet
- Prueba funcional de compuertas (ciclo completo)
- Revisión de logs de alarmas y errores

#### Rutina Mensual
- Calibración de sensores críticos
- Limpieza de gabinetes de control
- Verificación de torques en terminales
- Respaldo de configuraciones de programas

#### Rutina Anual
- Calibración completa con equipo certificado
- Reemplazo preventivo de fusibles
- Verificación de aislamiento eléctrico
- Actualización de documentación técnica

## 🔧 Diagnóstico y Resolución de Problemas

### Problemas Comunes

#### Pérdida de Comunicación BACnet

**Síntomas:**
- LED de comunicación rojo o apagado
- Pérdida de datos en BMS
- Timeouts en comandos remotos

**Diagnóstico:**
- Verificar continuidad de cable RS-485
- Comprobar terminación de red (120Ω)
- Validar configuración de MAC address única
- Revisar velocidad de comunicación (38,400 bps)

**Solución:**
- Revisar conexiones A(+) y B(-) en terminal de comunicaciones
- Verificar alimentación de repetidores si existen
- Resetear controlador si persiste el problema
- Contactar soporte técnico si no se resuelve en 30 minutos

#### Error de Lectura de Sensor

**Síntomas:**
- Valores de caudal erróneos o congelados
- Alarma de sensor fuera de rango
- Desviación excesiva respecto a referencia

**Diagnóstico:**
- Verificar alimentación del sensor (24 VDC)
- Comprobar integridad de cable de señal
- Validar rango de entrada configurado
- Revisar calibración reciente

**Solución:**
- Reemplazar cable si hay daño visible
- Recalibrar sensor con equipo de referencia
- Verificar configuración de entrada analógica
- Documentar acción correctiva realizada

### Códigos de Alarma

| **Código** | **Descripción** | **Prioridad** | **Acción Requerida** |
|---|---|---|---|
| AL001 | Pérdida comunicación expansión | Alta | Verificar cable CAN Bus |
| AL002 | Sensor caudal fuera rango | Media | Calibrar o reemplazar sensor |
| AL003 | Compuerta VAV sin respuesta | Alta | Verificar actuador y cableado |
| AL004 | Presión plenum excesiva | Crítica | Parada inmediata - verificar bloqueos |
| AL005 | Falla alimentación módulo | Crítica | Verificar fuente 24 VDC |

## 📊 Especificaciones Técnicas

### Condiciones Operativas

| **Parámetro** | **Valor** | **Unidad** |
|---|---|---|
| Temperatura operativa | 0 a 60 | °C |
| Humedad relativa | 5 a 95 | % (sin condensación) |
| Altitud máxima | 2000 | metros |
| Grado de protección | IP30 | - |
| Alimentación nominal | 24 ±2 | VDC/VAC |
| Consumo máximo | 15 | W |
| Precisión entradas analógicas | ±0.25 | % span |
| Resolución salidas analógicas | 0.1 | % |

### Capacidades de Control

| **Característica** | **Especificación** |
|---|---|
| Número máximo VAVs | 15 unidades |
| Plenums gestionados | 7 unidades |
| Tiempo respuesta típico | < 2 segundos |
| Precisión control caudal | ±3% setpoint |
| Rango control compuertas | 0-100% |
| Frecuencia actualización datos | 2 Hz |

### Comunicaciones

| **Protocolo** | **BACnet MS/TP** |
|---|---|
| Velocidad estándar | 38,400 bps |
| Máxima distancia | 1200 metros |
| Número máximo nodos | 127 |
| Tiempo respuesta típico | < 100 ms |
| Objetos BACnet soportados | AI, AO, BI, BO, AV, BV, MSV |

## 🔗 Enlaces y Documentación Relacionada

### Documentación Técnica
- [Manual KMC BAC-5901C](https://www.kmccontrols.com/product/controller-general-purpose-bacnet-aac-clock-mstp/)
- [Guía instalación CAN-5901](https://www.kmccontrols.com/product/expansion-io-module-8-ui-8-uo/)
- [Configuración BACnet MS/TP](../Documentación/Guías/BACnet-MSTP-Setup.pdf)

### Procedimientos Operativos
- [Manual de calibración de sensores](../Documentación/Guías/Calibracion-Sensores.pdf)
- [Protocolo de pruebas VAV](../Documentación/Guías/Protocolo-Pruebas-VAV.pdf)
- [Guía de diagnóstico](../Documentación/Guías/Diagnostico-Troubleshooting.pdf)

### Esquemas y Diagramas
- [Diagrama eléctrico controlador](../Documentación/Diagramas/Controlador1-Electrico.dwg)
- [Diagrama de red BACnet](../Documentación/Diagramas/Red-BACnet-CuartoPruebas.pdf)
- [Layout plenums y VAVs](../Documentación/Diagramas/Layout-Plenums-VAVs.pdf)

---

**Última actualización:** Septiembre 2025  
**Versión documento:** 2.0.0  
**Elaborado por:** Charlie & Claude - Equipo INNES Aire  
**Próxima revisión:** Marzo 2026