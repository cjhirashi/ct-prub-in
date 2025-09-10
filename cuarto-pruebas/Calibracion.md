# 🧩 CP - Operativo - Proceso de Calibración de Cajas VAV

## 🔷 A. Sistema KMC como Instrumento de Adquisición de Datos

### 1. Activación del Sistema de Calibración
- Se habilita el modo de calibración desde la interfaz gráfica del controlador
- Se selecciona el plenum y la caja VAV que se desea calibrar (lista desplegable)
- Al activar la caja seleccionada:
  - Se suministrará aire únicamente a esa caja
  - Todas las demás cajas se cierran (0% de apertura)
  - La caja activa queda disponible para control de apertura y toma de lecturas

### 2. Tablero General de Monitoreo de Cajas VAV

#### Visualización Completa del Sistema
**Tablero integral** que muestra información de **todas las cajas VAV del sistema**:

**Para cada caja VAV se visualiza**:
- **Presión diferencial (ΔP) del sensor** en tiempo real
- **Caudal calculado actual**: `Q_sistema = K_fábrica × √ΔP`
- **K de fábrica** (valor de referencia, no se modifica)
- **Multiplicador de corrección actual (a)**: (si existe calibración previa, valor por defecto = 1)
- **Offset de corrección actual (b)**: (si existe calibración previa, valor por defecto = 0)
- **Caudal corregido**: `Q_corregido = a × K_fábrica × √ΔP + b`
- **Porcentaje de apertura** de compuerta correspondiente
- **Estado operativo**: Activa/No activa (indicado con LED)

#### Estados de las Cajas VAV

**Caja VAV seleccionada para calibración**:
- Se resalta visualmente con **indicador luminoso LED** encendido
- Es la **única caja operativa** durante el proceso de calibración 
- **Única caja que responde** a comandos de apertura y muestreo
- **Única caja** cuyos datos se registran y procesan durante los ciclos de muestreo

**Cajas VAV no seleccionadas**:
- **Permanecen cerradas** (0% apertura) durante la calibración
- **LED apagado**, datos mostrados solo como referencia/monitoreo
- **No participan** en el proceso de muestreo

**Cambio de caja a calibrar**:
- Al seleccionar otra caja, el **LED se enciende** en la nueva caja seleccionada
- La caja anteriormente activa **LED se apaga** y se cierra automáticamente
- La nueva caja seleccionada se activa y queda lista para calibración

### 3. Configuración del Ciclo de Muestreo

**Parámetros persistentes** (se mantienen al cambiar de caja, hasta cerrar interfaz de calibración):
- **Porcentaje de apertura** fijo durante todo el ciclo
- **Número de muestras** (recomendado: 20-50 muestras)
- **Intervalo entre muestras** (recomendado: 10-30 segundos)

**Comportamiento de configuración**:
- Los valores se conservan aunque se cambie de caja VAV
- **No hay valores por defecto** que se restauren automáticamente
- Solo se resetean al cerrar/apagar la interfaz de calibración
- Deben modificarse manualmente según necesidad del punto de calibración

### 4. Ejecución del Ciclo de Muestreo

**El sistema KMC actúa como datalogger siguiendo esta secuencia**:

1. **Configuración inicial**: Mantener compuerta cerrada durante configuración del ciclo de muestreo
2. **Ajuste de apertura**: **Botón "Abrir Compuerta"** - abre compuerta al porcentaje definido para el punto de calibración
3. **Tiempo de estabilización**: El usuario espera la estabilización mientras observa valores en el panel de monitoreo
4. **Inicio del ciclo**: **Botón "Iniciar Muestreo"** - activa el ciclo cuando el usuario considere que el flujo está estable
5. **Registro de datos**: Para cada muestra registrar:
   - **ΔP instantáneo** (medido directamente del sensor, sin corrección)
   - **Q_sistema calculado** según ΔP instantáneo y K de fábrica
6. **Cálculos finales**: Al completar el ciclo, calcular y mostrar:
   - **ΔP**: promedio, máximo, mínimo
   - **Q_sistema**: promedio, máximo, mínimo (calculados desde los valores de ΔP correspondientes)
   - **Coeficiente de Variación (CV%)**: (Desviación Estándar / Media) × 100 *(Opcional - solo si los controles KMC lo permiten)*

**Nota importante**: Todo el proceso de calibración utiliza datos medidos y procesados **sin factores de corrección previos**, usando únicamente K de fábrica, independientemente de si existen calibraciones anteriores.

### 5. Panel de Resultados de Muestreo
**Ubicado junto al panel de monitoreo general**, mostrará los resultados del ciclo actual:

**Datos estadísticos del ciclo**:
- **ΔP del sensor**: promedio, mínimo y máximo
- **Q_sistema**: promedio, mínimo y máximo (calculados desde los valores de ΔP correspondientes)
- **CV%** para evaluación de estabilidad *(solo si controles KMC lo permiten)*
- **Campos claramente identificados** para copia manual del usuario

**Flujo de trabajo por punto**:
1. Configurar apertura del punto de calibración
2. Abrir compuerta con botón específico
3. Esperar estabilización observando panel de monitoreo
4. Iniciar ciclo de muestreo con botón específico
5. **Usuario copia manualmente** los datos generados a Excel
6. Ajustar siguiente apertura y repetir proceso

---

## 🔷 B. Medición Externa y Análisis Estadístico en Excel

### 1. Protocolo de Medición Externa Sincronizada
**Durante cada ciclo KMC**:
- Medición simultánea con caudalímetro de referencia calibrado
- Mismo intervalo de tiempo que el sistema KMC
- **Registro de**:
  - Q_real por muestra o promedio del ciclo
  - Condiciones ambientales (temperatura, presión barométrica)
  - Observaciones de estabilidad del flujo
  - CV% del ciclo para filtrado posterior *(si el equipo KMC lo permite)*

### 2. Compilación de Dataset en Excel
**Tabla consolidada por caja VAV**:

| Ciclo | %_Apertura | ΔP_prom | Q_sistema_prom | Q_real_prom | CV_% *(opcional)* | Fecha | Observaciones |
|-------|------------|---------|----------------|-------------|------------------|--------|---------------|
| 1     | 20%        | 0.12    | 95             | 92          | 1.8              | ...    | Estable       |
| 2     | 40%        | 0.35    | 185            | 190         | 2.1              | ...    | Estable       |
| 3     | 60%        | 0.65    | 260            | 268         | 1.9              | ...    | Estable       |
| ...   | ...        | ...     | ...            | ...         | ...              | ...    | ...           |
| 10    | 100%       | 1.15    | 345            | 358         | 2.3              | ...    | Estable       |

### 3. Análisis Estadístico Robusto en Excel

#### Evaluación de Calidad de Datos
- **Filtrado por CV%**: Descartar ciclos con CV > 5% *(solo si existen los datos de KMC)*
  - Alta variabilidad indica mediciones inestables
- **Evaluación de linealidad**: Gráfico de dispersión Q_real vs Q_sistema
  - **Sensores perfectamente calibrados** resultarían en: a = 1 y b = 0

#### Regresión Lineal
**Modelo**: `Q_real = a × Q_sistema + b`

**Cálculos estadísticos**:
- **Coeficientes**: a (multiplicador) y b (offset)
- **Métricas de calidad**: R², RMSE, error porcentual promedio
- **Intervalos de confianza** para los coeficientes
- **Análisis de residuos** para validación del modelo
- **Ventaja del método**: Múltiples puntos de apertura permiten mejor estimación estadística

---

## 🔷 C. Implementación en Sistema KMC y Validación

### 1. Ingreso de Parámetros de Calibración

**Interfaz de ingreso de parámetros**:
- **Campo Multiplicador (a)**: Valor calculado por regresión lineal
- **Campo Offset (b)**: Valor calculado por regresión lineal  
- **Botón "Guardar Calibración"**: Para formalizar los valores a y b en el sistema

**Comportamiento del sistema**:
- **Los valores a y b NO se formalizan** hasta activar "Guardar Calibración"
- Permite revisar y validar antes de confirmar cambios
- Ecuación implementada tras guardar: `Q_corregido = a × K_fábrica × √ΔP + b`

**Nota**: K_fábrica permanece inalterado como parte integral del cálculo.

### 2. Validación Operacional

**Pruebas de verificación**:
- Seleccionar 2-3 aperturas diferentes para validación
- Comparar Q_corregido del sistema vs medición con caudalímetro de referencia
- **Criterio de aceptación**: Error < 5% en rango de operación normal
- Documentar resultados de validación

### 3. Documentación y Respaldo

#### Archivo Excel de Calibración (Externo al KMC)
- **Datos originales completos** de todos los ciclos de muestreo
- **Análisis estadístico detallado** con gráficos y métricas
- **Coeficientes del modelo lineal** (a, b) con intervalos de confianza
- **Métricas de calidad**: R², RMSE, CV% por ciclo *(si disponible)*
- **Datos de validación operacional** con **reporte de intervalos de mejor comportamiento** y mayor precisión para consideración del operador

#### Sistema KMC (Solo Datos Esenciales)
- **Multiplicador (a)** y **offset (b)** por caja VAV
- **K_fábrica** (permanece inalterado como parte integral del sistema)
- **Fecha de última calibración**

---

## 📊 Ventajas del Enfoque Híbrido KMC-Excel

### ✅ Fortalezas del Sistema KMC
- **Adquisición automatizada** de datos con control preciso de compuertas
- **Interfaz familiar** para operadores del sistema
- **Cálculos en tiempo real** simples y confiables
- **Persistencia de configuración** durante sesión de calibración
- **Estabilidad operacional** del sistema de control

### ✅ Fortalezas del Análisis en Excel  
- **Análisis estadístico robusto** con herramientas avanzadas
- **Flexibilidad** para diferentes modelos y validaciones
- **Documentación completa** para auditorías y trazabilidad
- **Herramientas gráficas** para evaluación visual de calidad de datos
- **Identificación de rangos óptimos** de operación con mayor precisión

### ⚖️ Simplicidad y Precisión del Resultado Final
- **Solo 2 parámetros por caja**: a (multiplicador) y b (offset)
- **Ecuación única**: `Q_calibrado = a × Q_sistema + b`
- **Máxima precisión**: Modelo lineal completo que incluye offset
- **Control de cambios**: Los valores no se formalizan hasta confirmar con botón "Guardar"
- **Implementación simple**: Mínima modificación al sistema KMC existente

---

## 🔧 Consideraciones Técnicas Adicionales

### Comportamiento de Reseteo del Sistema

**Durante la sesión activa de calibración**:
- **Todos los parámetros son modificables** por el usuario en cualquier momento:
  - Caja seleccionada
  - Porcentaje de apertura
  - Número de muestras
  - Intervalo de muestreo
- **Los valores se mantienen** hasta modificación manual del usuario
- **Sin cambios automáticos** al ejecutar ciclos o cambiar operaciones

**Al cerrar la interfaz de calibración**:
- **Se asignan valores por defecto** a todos los parámetros de configuración:
  - Caja seleccionada, número de muestras, intervalo de muestreo, apertura
- **Se preservan**: Valores a y b que hayan sido guardados con el botón "Guardar Calibración"

**Al desenergizar los controles KMC** (corte de energía):
- **Reseteo completo del sistema** por cuestiones técnicas
- **Todos los parámetros vuelven a valores por defecto**: incluidos a = 1, b = 0
- **Se pierden todas las calibraciones** guardadas previamente
- **Requiere recalibración completa** del sistema tras restablecimiento de energía

### Persistencia de Datos
- **Durante la sesión activa**: Los parámetros de configuración se mantienen al cambiar de caja
- **Valores de calibración**: Solo se formalizan y persisten al usar "Guardar Calibración"
- **Respaldo recomendado**: Mantener registro externo en Excel de todos los valores a y b

### Funcionalidades Opcionales
- **Cálculo de CV%** sujeto a capacidades del sistema KMC
- **Validación en tiempo real** de estabilidad de flujo
- **Alertas** por mediciones fuera de rango esperado
