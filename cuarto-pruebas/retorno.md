# ⚙️ CP – Operativo – Proceso de **Retorno** (Cuarto de Pruebas)

> **Propósito.** Definir la **lógica de operación** de la prueba **Retorno**. Este documento describe **cómo funciona** (flujo, interfaz, ejecución y validación) **sin** prescribir nombres de variables, tags ni detalles de implementación.

---

## 🔷 A. Sistema KMC como Instrumento de Adquisición de Datos

### 1) Activación del modo de prueba
- Habilitar **modo de prueba Retorno** mediante un control **ON/OFF**.
- Seleccionar el **elemento de retorno** a evaluar según la instalación disponible.
- Configurar **parámetros de muestreo**:
  - **Número de muestras (N)**.
  - **Intervalo entre muestras (Δt)** en segundos.
  - **Identificador de grupo/ciclo** (para trazabilidad externa).
- **Persistencia de sesión:** mientras el modo esté **ON**, la selección y los parámetros se conservan. Se restablecen con **`RESET`**.

### 2) Organización de la interfaz
- **Una sola pestaña** con dos zonas:

  **a) Panel de Control**
  - Controles: **ON/OFF**, selección del elemento de retorno, **N**, **Δt**, **Grupo**.
  - Botones de acción: **`[INICIAR MUESTREO]`**, **`[DETENER]`**, **`[RESET]`**.

  **b) Panel de Monitoreo**
  - **Lecturas instantáneas** (en tiempo real) de las **magnitudes relevantes** de la prueba de Retorno, visibles **antes** y **durante** el ciclo para permitir **estabilización**.
  - **Estado del ciclo**: muestra actual (**i/N**), **tiempo restante** y **estado** (IDLE / ARMED / SAMPLING / COMPLETE).
  - **Estadísticos del ciclo** (publicados al finalizar): **Promedio**, **Máximo**, **Mínimo**.  
    - **CV%** (coeficiente de variación) es **opcional** y depende de las capacidades del controlador.

> **Nota (alcance de las lecturas).** La prueba “Retorno” utiliza **dos lecturas clave** provenientes de la instalación (por ejemplo, una **magnitud local de retorno** y una **referencia del caudal del sistema**). Este documento no fija su origen ni nomenclatura; se definen fuera de la lógica.

### 3) Configuración del ciclo de muestreo
- Ajustar **N** y **Δt** de acuerdo con el nivel de estabilidad esperado.
- Confirmar **Grupo/Ciclo** para el registro externo.
- Verificar que las **lecturas instantáneas** se encuentren en rangos válidos **antes** de iniciar.

### 4) Ejecución del ciclo de muestreo
1. Con el modo **ON**, utilizar las **lecturas instantáneas** para **estabilizar** la condición de prueba (sin registro aún).
2. Presionar **`[INICIAR MUESTREO]`** → el sistema ejecuta **N** capturas, separadas por **Δt**.
3. Durante el ciclo, se actualiza el **progreso** (muestra i/N) y el **tiempo restante**.
4. Al completar **N** muestras, el ciclo **finaliza automáticamente** y pasa a **estado COMPLETE**.  
   - **`[DETENER]`** aborta el ciclo (un ciclo abortado se considera **incompleto**).

### 5) Resultados del ciclo
- Publicar en la interfaz, por cada **magnitud relevante**:
  - **Promedio**, **Máximo**, **Mínimo** del ciclo.  
  - **CV%** (si el equipo lo permite).
- Los resultados del ciclo son **visuales** y **no implican** persistencia histórica interna (el histórico se gestiona externamente).

---

## 🔷 B. Medición Externa y Análisis en Excel

### 1) Protocolo de registro externo
- Registrar para **cada ciclo**:
  - **Ciclo/Grupo**, **N**, **Δt**, **Fecha/Hora**, **Observaciones**.
  - **Estadísticos** (Promedio, Máximo, Mínimo; **CV%** si está disponible) de las magnitudes utilizadas en la prueba de Retorno.
- (Opcionales) **Condiciones de entorno** relevantes para análisis (p. ej., temperatura ambiente, presión barométrica, altitud, modo de tratamiento de temperatura si aplica).

### 2) Estructura mínima del dataset
```
Ciclo/Grupo | N | Δt [s] | Fecha/Hora | Magnitud_Retorno: Prom | Máx | Mín | CV%* | Magnitud_Referencia: Prom | Máx | Mín | CV%* | Observaciones
(* CV% opcional, sujeto a disponibilidad)
```

### 3) Reglas de calidad de datos
- **Ciclo completo**: sólo analizar ciclos que hayan alcanzado **N** muestras.
- **Estabilidad**: descartar o marcar ciclos con variabilidad excesiva (p. ej., CV% por encima de un umbral operativo definido por el equipo).
- **Consistencia**: comparar ciclos consecutivos en condiciones similares para detectar desviaciones.

### 4) Análisis sugerido
- Comparación de **estadísticos** entre ciclos (tendencias, repetibilidad).
- (Si procede) Relación entre la **magnitud local de retorno** y la **referencia del caudal del sistema (caudalimetro)** para validaciones.

---

## 🔷 C. Implementación y Validación en el Sistema

### 1) Reglas de operación
- **Un solo ciclo activo** por sesión de Retorno.
- **Lecturas instantáneas** disponibles durante la fase de **estabilización** (previa al muestreo).
- **Sin dependencias** de setpoints por tamaño: la lógica de Retorno se centra en lectura y estadísticos del ciclo.

### 2) Validación operacional
- Ejecutar **2–3 ciclos** en condiciones definidas y comparar estadísticos para verificar **consistencia**.
- Si existe comparación con **patrón/objetivo**, el **criterio de aceptación** (p. ej., error máximo permitido) se define **fuera de esta lógica**.

### 3) Documentación y respaldo
- **Interfaz**: mostrar únicamente los resultados del **ciclo actual**.
- **Histórico**: mantener en **Excel** el dataset de ciclos y el análisis asociado.

---

## ✅ Checklist del Proceso
- [ ] **ON** modo Retorno  
- [ ] Definir **N** y **Δt**  
- [ ] Asignar **Grupo/Ciclo**  
- [ ] Verificar **estabilización** con lecturas instantáneas  
- [ ] **Iniciar muestreo** (ejecutar **N** a **Δt**)  
- [ ] Revisar **Prom/Máx/Mín** *(+ **CV%** si está disponible)*  
- [ ] **Registrar** en Excel / **`RESET`** para preparar el siguiente ciclo

---

## 🛠️ Consideraciones Técnicas

**Persistencia.**  
- Mientras el modo esté **ON**, la configuración permanece. **`RESET`** limpia estadísticas y devuelve parámetros a valores por defecto.

**Manejo de errores.**  
- **Ciclo incompleto** (interrumpido) → no publicar ni utilizar estadísticas del ciclo.  
- **Lecturas fuera de rango** → notificar al operador y evitar el cálculo de resultados hasta que se restablezcan condiciones válidas.

**Corrección por densidad (opcional).**  
- Si la operación lo requiere, la **compensación por temperatura/altitud** puede aplicarse **fuera** de esta lógica (por ejemplo, para análisis en Excel o como configuración global del sistema). La **secuencia** y la **interfaz** de esta lógica **no** dependen de dicha corrección.


**Ámbito del documento.**  
- Esta lógica **no** define nombres de variables, tags, ecuaciones internas ni fuentes exactas de las lecturas; dichos aspectos se **especifican e implementan por separado** al momento de traducir la lógica al código del controlador.
