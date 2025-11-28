# ⚙️ CP – Operativo – Proceso de Medición de Área Efectiva en Rejillas

## 🔷 A. Sistema KMC como Instrumento de Adquisición de Datos

### 1. Activación del Sistema de Prueba
- Habilitar **modo de prueba Área Efectiva** desde la interfaz gráfica (botón ON/OFF superior).
- Seleccionar **plenum** y cajas disponibles (Grande, Mediana, Chica).
- Configurar **Caudal objetivo (CFM)**:
  - Valor mínimo por defecto según tamaño.
  - Permite ingresar otro valor dentro del rango operativo.
- Botón ON/OFF para activar/desactivar cada caja.
- **Caudal Total**: suma automática de los caudales activos.

**Persistencia entre pestañas:** parámetros se mantienen al cambiar de pestaña.

### 2. Organización de la Interfaz
La interfaz se divide en **dos pestañas principales**:

#### Pestaña 1: Monitoreo y Adquisición de Datos
**Propósito:** Ejecutar ciclos de muestreo y obtener datos para análisis.

**Fuente de lectura de velocidad:**  
La velocidad en FPM se obtiene mediante un **transductor de velocidad dedicado**, instalado para realizar estas mediciones de forma precisa durante el muestreo.

**Panel de Monitoreo:**
```
Velocidad [FPM] | Caudal [CFM] | Promedio | Máximo | Mínimo
XXX.X           | XXX.X        | XXX.X    | XXX.X  | XXX.X
```

**Parámetros de muestreo:**
- Número de muestras (N)
- Intervalo entre muestras (Δt)
- Grupo/Ciclo (identificador)

**Botones:**
- `[INICIAR MUESTREO]` → Comienza ciclo.
- `[DETENER MUESTREO]` → Aborta ciclo.
- `[GUARDAR GRUPO]` → Persiste resultados en pestaña 2.
- `[RESET]` → Limpia variables y registros.

**Flujo operativo:**
1. Activar modo de prueba.
2. Seleccionar plenum y cajas.
3. Configurar caudales, N, Δt y Grupo.
4. Iniciar muestreo.
5. Revisar estadísticas.
6. Guardar grupo.
7. Repetir con diferentes caudales.

#### Pestaña 2: Resumen de Resultados
**Propósito:** Mostrar resultados y calcular área efectiva.

**Tabla de Resultados:**
```
Grupo | Q_n [CFM] | V_n [FPM] | A_n [ft²] | % Desv.
1     | XXX.X     | XXX.X     | X.XXX     | X.XX%
...
```

**Variables calculadas:**
- $A_n = \frac{Q_n}{V_n}$
- $D_n = |1 - \frac{A_n}{PROM\_AREA}|$
- $PROM\_\text{AREA} = \frac{\sum A_n}{	\text{Número de ciclos válidos}}$

---

## 🔷 B. Medición Externa y Análisis Estadístico en Excel
- Registrar simultáneamente en Excel:
```
Grupo | Caudal objetivo | Q_n | V_n | A_n | PROM_AREA | % Desv. | Fecha | Obs
```
- Validar estabilidad (min/max cercanos).
- Comparar con valores patrón si aplica.


---

## ✅ Checklist del Proceso Completo
**Fase 1: Adquisición de Datos (Pestaña 1)**
- Activar modo de prueba.
- Seleccionar plenum y cajas.
- Configurar parámetros.
- Iniciar muestreo.
- Guardar grupo.

**Fase 2: Resumen (Pestaña 2)**
- Validar cálculos.
- Revisar desviaciones.

**Fase 3: Validación**
- Comparar con medición externa.

**Fase 4: Documentación**
- Guardar dataset y análisis.

---

## 🔧 Consideraciones Técnicas
- Persistencia entre pestañas.
- `[RESET]` borra datos y vuelve a valores por defecto.
- Manejo de errores:
  - Sensor fuera de rango → El usuario observa las lecturas de caudal y compara con los rangos de operación definidos para dicha caja VAV.
  - Ciclo incompleto → no calcular PROM_AREA.
