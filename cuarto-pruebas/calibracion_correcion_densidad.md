# 🧪 CP - Operativo - Proceso de Calibración de Cajas VAV con Corrección por Densidad

## 🔷 A. Sistema KMC como Instrumento de Adquisición de Datos

### 1. Activación del Sistema de Calibración

**Aplicable a ambas pestañas:**

- Se habilita el modo de calibración desde la interfaz gráfica del controlador
- Se selecciona el **plenum** y la **caja VAV** que se desea trabajar (listas desplegables)
- **Importante**: La selección solo indica con cuál caja se trabajará. La apertura física NO se ejecuta hasta presionar **[ABRIR COMPUERTA]**
- Al presionar **[ABRIR COMPUERTA]**:
  - Se suministrará aire únicamente a esa caja (al % configurado)
  - Todas las demás cajas se cierran (0% de apertura)
  - Solo una caja puede estar abierta (>0%) a la vez

**Persistencia entre pestañas:**
- La caja seleccionada, el % de apertura configurado, y la posición física del damper se mantienen al cambiar entre pestañas
- Los cambios solo se ejecutan al presionar botones de acción, NO al cambiar de pestaña

---

### 2. Organización de la Interfaz de Calibración

La interfaz se divide en **DOS PESTAÑAS PRINCIPALES**:

---

## **PESTAÑA 1: MONITOREO Y ADQUISICIÓN DE DATOS**

### Propósito
Instrumento de medición tipo manómetro digital para ejecutar ciclos de muestreo y obtener datos para análisis en Excel. Proceso caja por caja. **NO modifica valores de calibración** (a, b).

---

### Panel de Monitoreo en Tiempo Real

**UNA FILA** para la caja seleccionada con valores instantáneos actualizados continuamente:

| ΔP [inH2O] | T [°F] | A(T,Alt) | Q_corregido [CFM] | Q_sistema [CFM] | % Apertura |
|------------|--------|----------|-------------------|-----------------|------------|
| X.XXX      | XX.X   | X.XXXX   | XXX.X             | XXX.X           | XX.X       |

**Variables:**
- **ΔP**: Presión diferencial del sensor
- **T**: Temperatura (sensada o manual según disponibilidad)
- **A(T,Alt)**: Factor de densidad instantáneo
- **Q_corregido**: K_fábrica × A × √ΔP
- **Q_sistema**: a × Q_corregido + b (usa valores guardados de calibración)
- **% Apertura**: Posición actual del damper

**Parámetros de contexto visibles:**
- Caja VAV activa, Altitud (editable), K_fábrica, a actual, b actual (solo lectura)

---

### Configuración del Ciclo de Muestreo

**Parámetros persistentes** (se mantienen al cambiar de caja):

| Parámetro | Rango recomendado |
|-----------|-------------------|
| % Apertura objetivo | 0 - 100% |
| Número de muestras (N) | 20 - 50 |
| Intervalo (Δt) | 10 - 30 seg |

**Modo de Temperatura:**
- **○ INSTANTÁNEA**: Lee T_i con cada muestra, calcula Q_corregido_i individual, luego promedia
- **○ CONSTANTE**: Usa T_fija definida al inicio, calcula Q_corregido_prom con ΔP_prom

---

### Controles y Ejecución

**Botones:**
1. **[ABRIR COMPUERTA]**: Cierra todas las demás cajas, abre la seleccionada al % configurado
2. **[INICIAR MUESTREO]**: Ejecuta N muestras con intervalo Δt
3. **[DETENER]**: Aborta ciclo si hay inestabilidad

**Flujo operativo:**
1. Configurar parámetros (%, N, Δt, Modo T)
2. Abrir compuerta y observar estabilización
3. Iniciar muestreo (registra ΔP, T, Q_corregido, Q_sistema)
4. Sistema calcula estadísticas al finalizar

**Cálculo según modo temperatura:**

- **INSTANTÁNEA**: Para cada muestra i, calcula Q_corregido_i = K × A_i × √ΔP_i. Al finalizar: Q_corregido_prom/min/max son promedio/mínimo/máximo de esos valores calculados.

- **CONSTANTE**: Registra ΔP_i. Al finalizar: calcula Q_corregido_prom/min/max = K × A_fija × √(ΔP_prom/min/max)

Luego: Q_sistema_prom/min/max = a × Q_corregido_prom/min/max + b

---

### Resultados del Ciclo

**Estadísticas mostradas:**

| Variable | Promedio | Mínimo | Máximo |
|----------|----------|--------|--------|
| ΔP [inH2O] | X.XXX | X.XXX | X.XXX |
| T [°F] | XX.X | XX.X* | XX.X* |
| Q_corregido [CFM] | XXX.X | XXX.X | XXX.X |
| Q_sistema [CFM] | XXX.X | XXX.X | XXX.X |

*Si T constante: min = max = prom = T_fija

**Propósito min/max:** Verificar estabilidad, detectar oscilaciones excesivas.

**Usuario copia manualmente a Excel:** Ciclo, %Apertura, estadísticas de ΔP/T/Q_corregido/Q_sistema, Modo_T, Fecha, Observaciones. **Importante:** También registrar Q_patrón del caudalímetro externo.

---

### Características de PESTAÑA 1

**Incluye:** Monitoreo continuo, ciclos de muestreo, estadísticas, configuración flexible.

**NO incluye:** Guardado automático, exportación automática, modificación de a/b, historial.

---

## **PESTAÑA 2: PARÁMETROS DE CALIBRACIÓN**

### Propósito
Asignar y gestionar valores de calibración (a, b) para todas las cajas VAV del sistema.

---

### Tabla de Todas las Cajas

**Una fila por caja**, mostrando valores instantáneos y parámetros editables:

| Caja | ΔP | Q_corregido | a | b | Q_sistema | % Apertura | Estado |
|------|----|----|---|---|----|----|--------|
| VAV-101 | X.XXX | XXX.X | **1.0245** | **-8.3** | XXX.X | 35.0 | ON |
| VAV-102 | X.XXX | XXX.X | **1.0000** | **0.0** | XXX.X | 0.0 | OFF |
| VAV-103 | X.XXX | XXX.X | **1.0180** | **-5.2** | XXX.X | 0.0 | OFF |

**Columnas editables:** a, b (en negrita)  
**Solo lectura:** ΔP, Q_corregido, Q_sistema, %Apertura, Estado  
**Estado:** ON (abierta >0%) / OFF (cerrada 0%)

---

### Panel de Control

**Selección y apertura** (misma lógica que PESTAÑA 1):
- Dropdowns: Plenum, Caja VAV
- Campo: % Apertura objetivo
- Botón: **[ABRIR COMPUERTA]** - cierra todas las demás, abre la seleccionada

---

### Edición de a y b

**Características:**
- Editar **cualquier caja** sin necesidad de activarla
- Editar múltiples cajas antes de guardar
- Valores editados **se mantienen mientras se está en la pestaña**
- **Se pierden** si se sale sin guardar (vuelven a valores previos)

**Validación:** a (0.5-2.0), b (-500 a 500 CFM). Alertas si fuera de rango.

---

### Botones de Gestión

**[GUARDAR]**
- Persiste todos los a, b de la tabla
- Campos vacíos o inválidos → a=1.0, b=0.0
- Efecto inmediato en todo el sistema (ambas pestañas)

**[RESET]**
- Restaura valores previos (últimos guardados)
- NO guarda, solo revierte visualización

**[DEFAULT]**
- Asigna a=1.0, b=0.0 a TODAS las cajas
- NO guarda, solo modifica visualización

---

### Características de PESTAÑA 2

**Incluye:** Visualización de todas las cajas, edición simultánea de a/b, control de apertura, monitoreo instantáneo.

**NO incluye:** Ciclos de muestreo, configuración N/Δt, estadísticas, exportación de datos.

---

## **LÓGICA COMPARTIDA ENTRE PESTAÑAS**

### Sincronización Automática

| Elemento | Sincronizado | Cuándo cambia |
|----------|--------------|---------------|
| Plenum/Caja seleccionada | ✓ | Al cambiar dropdown |
| % Apertura (campo) | ✓ | Al editar campo |
| Posición física damper | ✓ | Solo al presionar [ABRIR COMPUERTA] |
| Estado ON/OFF cajas | ✓ | Solo al presionar [ABRIR COMPUERTA] |
| Valores a, b vigentes | ✓ | Solo al presionar [GUARDAR] en PESTAÑA 2 |

**Regla clave:** Cambiar entre pestañas NO mueve compuertas ni pierde configuración.

### Ecuaciones de Referencia

**Factores de densidad:**
```
F_H = 1.00114 × exp(0.000036978 × Altitud[ft])  (constante del sitio)
F_T = 0.00188703 × T[°F] + 0.86799              (variable)
A(T,Altitud) = √(F_H × F_T)
```

**Caudales:**
```
Q_corregido = K_fábrica × A(T,Altitud) × √ΔP
Q_sistema = a × Q_corregido + b
```

**Defaults:** a=1.0, b=0.0 → Q_sistema = Q_corregido

---

## 🔷 B. Medición Externa y Análisis Estadístico en Excel

### 1. Protocolo de Medición Sincronizada
Durante cada ciclo de PESTAÑA 1, medir simultáneamente con **caudalímetro patrón calibrado**. Registrar Q_patrón, condiciones ambientales, observaciones.

### 2. Dataset en Excel

**Tabla por caja VAV:**

| Ciclo | %Apertura | ΔP_prom | T_prom | Q_corregido_prom | Q_patrón | Modo_T | CV%* | Fecha | Obs |
|-------|-----------|---------|--------|------------------|----------|--------|------|-------|-----|
| 1 | 20% | 0.12 | 72.5 | 95.2 | 92.1 | CONST | 1.8 | ... | Estable |
| 2 | 40% | 0.35 | 73.1 | 186.3 | 190.5 | CONST | 2.1 | ... | Estable |

*CV% si disponible desde sistema KMC

**Q_corregido_prom ya incluye corrección por densidad.** Este es el valor para regresión.

### 3. Regresión Lineal

**Modelo:** Q_patrón = a × Q_corregido + b

**Procedimiento:**
1. Filtrar por calidad: descartar ciclos con CV% > 5%
2. Usar mínimo 3-5 puntos de apertura distribuidos
3. Ajuste por mínimos cuadrados → obtener a, b
4. Validar: R², RMSE, residuos
5. Gráfico: Q_corregido vs Q_patrón + recta ajustada

**Salida:** Coeficientes a, b con métricas de confianza para ingresar en PESTAÑA 2.

---

## 🔷 C. Implementación y Validación en Sistema KMC

### 1. Ingreso de Parámetros (PESTAÑA 2)

1. Abrir PESTAÑA 2
2. Editar campos a, b de cada caja según análisis de Excel
3. Presionar **[GUARDAR]** para persistir
4. Sistema aplica inmediatamente: Q_sistema = a × Q_corregido + b

**K_fábrica permanece inmutable.**

### 2. Validación Operacional (PESTAÑA 1)

**Pruebas:**
1. Seleccionar 2-3 aperturas diferentes (baja, media, alta)
2. Ejecutar ciclo de muestreo en cada punto
3. Comparar Q_sistema vs caudalímetro patrón
4. **Criterio:** Error < 5% en rango operativo

**Si no cumple:**
- Revisar calidad de datos (CV% alto)
- Verificar rango de calibración (suficientes puntos)
- Repetir análisis con dataset depurado

### 3. Documentación

**Excel (externo):**
- Dataset completo con Q_corregido, Q_patrón
- Análisis de regresión (a, b, R², RMSE)
- Evidencia de validación

**Sistema KMC:**
- Valores a, b por caja (persistentes)
- K_fábrica, Altitud, F_H
- Fecha de calibración

---

## 📊 Ventajas del Enfoque

### Corrección por Densidad
- Compensa altitud y temperatura → mayor precisión
- Mantiene K_fábrica como referencia inmutable
- Factor A(T,Alt) aplicado en tiempo real

### Flexibilidad Operacional
- Modo CONSTANTE: rápido, asume T estable
- Modo INSTANTÁNEA: preciso, captura variaciones térmicas

### Simplicidad
- Solo 2 parámetros por caja: a, b
- Ecuación única: Q_sistema = a × Q_corregido + b
- Interfaz en dos pestañas con propósitos claros

---

## 🔧 Consideraciones Técnicas

### Persistencia
- **Durante sesión:** Parámetros de muestreo persisten al cambiar de caja
- **Al cerrar interfaz:** Parámetros se resetean a defaults si es que no se guardaron
- **Pérdida de energía:** Valores a, b se pierden si no hay memoria no volátil (recomendado implementar EEPROM)
- **Respaldo:** Mantener Excel con todos los valores a, b y fechas

### Manejo de Errores
- Sensor T falla → cambiar a modo MANUAL
- Factor A fuera de rango → alertar, verificar Altitud/T
- ΔP fuera de rango del sensor → error crítico

### Inicialización
- Al arrancar: calcular F_H una vez (constante sitio)
- Cargar valores a, b desde memoria (si existen)
- Defaults: a=1.0, b=0.0

---

## ✅ Checklist del Proceso Completo

### Fase 1: Adquisición de Datos (PESTAÑA 1)
- [ ] Seleccionar plenum y caja VAV
- [ ] Configurar: %Apertura, N, Δt, Modo T
- [ ] Abrir compuerta, observar estabilización
- [ ] Iniciar muestreo
- [ ] Revisar estadísticas (verificar CV% bajo, min/max estables)
- [ ] Copiar datos a Excel (incluir Q_patrón del caudalímetro externo)
- [ ] Repetir con 3-5 aperturas diferentes

### Fase 2: Análisis Externo (EXCEL)
- [ ] Compilar dataset completo
- [ ] Filtrar por calidad (CV% < 5%)
- [ ] Regresión lineal: Q_patrón vs Q_corregido
- [ ] Obtener a, b con R² > 0.95 (recomendado)
- [ ] Validar análisis de residuos

### Fase 3: Implementación (PESTAÑA 2)
- [ ] Ingresar valores a, b en tabla
- [ ] Revisar Q_sistema calculado (vista previa)
- [ ] Presionar [GUARDAR]
- [ ] Confirmar guardado exitoso

### Fase 4: Validación (PESTAÑA 1)
- [ ] Ejecutar ciclos en 2-3 aperturas
- [ ] Comparar Q_sistema vs Q_patrón
- [ ] Verificar error < 5% en todos los puntos
- [ ] Si cumple: calibración completa ✓
- [ ] Si no cumple: revisar y repetir desde Fase 2

### Documentación Final
- [ ] Guardar Excel con dataset y análisis
- [ ] Verificar persistencia de a, b en sistema
- [ ] Registrar fecha de calibración
- [ ] Respaldar valores externamente

---

**Fin del documento – Proceso de Calibración de Cajas VAV con Corrección por Densidad**
