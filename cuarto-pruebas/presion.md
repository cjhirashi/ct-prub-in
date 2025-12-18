# CP – Operativo – Proceso de **Caída de presión** (Cuarto de Pruebas)

## 🔷 A. Sistema KMC como Instrumento de Adquisición de Datos

### 1) Activación del Sistema de Prueba
- **Modo de prueba:** Habilitar **“Caída de presión”** desde el **botón Arranque** (ON/OFF).
- **Selección de elemento bajo prueba:**  
  - **Plenum**: seleccionar **un plenum activo** (p. ej., PL‑1, PL‑2, PL‑4, PL‑5, PL‑6, PL‑R7).  
  - **Regla de exclusión:** **solo un plenum** puede estar activo por ciclo. Los demás **no se sensan** ni participan.
- **SetPoints de caudal:**  
  - Tres **setpoints** disponibles por tamaño (**Grande**, **Mediana**, **Chica**), cada uno con **valor en CFM** y **switch ON/OFF**.  
  - **Caudal total** mostrado como **suma** de los setpoints **activos**.
- **Parámetros de muestreo:**  
  - **Número de muestras (N)** y **intervalo de muestreo (Δt)** en segundos.  
  - **Botón “Muest.” (Iniciar muestreo)** separa la fase de estabilización de la fase de adquisición.

**Persistencia de sesión:**  
- Mientras **Arranque = ON** la configuración **permanece** (plenum seleccionado, setpoints, N y Δt).  
- **Reset** vuelve a valores por defecto y **limpia variables** de resultados.

---

### 2) Organización de la Interfaz
**Una sola pestaña** con dos zonas principales:

**a) Panel de Control (izquierda)**  
- Arranque (ON/OFF).  
- **Plenum** (selector).  
- **SetPoints** por tamaño (valor CFM + switch ON/OFF).  
- **Caudal total** (CFM).  
- **Muestras:** N, Δt, **Muest.** (Iniciar), **Activ.**/**Inicio**, **Reset**.

**b) Zona de Monitoreo (centro e inferior)**  
- Ducto con los **plenums** gráficos.  
- **Indicadores de estado** solo para el **plenum activo**.  
- **Tabla de resultados**:
  - **DP-A** y **DP-B**: **PROMEDIO**, **MÁXIMO**, **MÍNIMO**, **T REAL**.  
  - **Caudal**: **PROMEDIO**, **MÁXIMO**, **MÍNIMO**.

> **Nota:** Antes de iniciar el muestreo, el operador utiliza lecturas **instantáneas** para **verificar estabilización**.

---

### 3) Flujo Operativo
1. **Arranque = ON**, seleccionar **plenum** bajo prueba.  
2. Configurar **setpoints** (CFM) por tamaño.  
3. Ajustar **N** y **Δt**.  
4. **Esperar estabilización** observando lecturas instantáneas.  
5. Presionar **Muest.** → Inicia el ciclo con **N** muestras separadas por **Δt**.  
6. Durante el ciclo: registrar **DP-A**, **DP-B** y **Caudal**; actualizar **PROMEDIO**, **MÁXIMO**, **MÍNIMO**; mostrar **T REAL**.  
7. Al completar **N** muestras, **finaliza** el ciclo y se publican estadísticas.  
8. Operador **anota** en Excel si requiere análisis profundo.

---

## 🔷 B. Medición Externa y Análisis en Excel
- **Dataset mínimo:** Plenum activo, setpoints, N, Δt, estadísticas (prom, máx, mín) para DP-A, DP-B, Caudal.  
- **Usos en Excel:** Verificación de estabilidad, curvas ΔP vs CFM, comparaciones entre plenums.

---

## 🔷 C. Implementación y Validación
- **Un plenum activo por ciclo**.  
- **Publicación** de estadísticas en tiempo real.  
- **Sin persistencia histórica**: datos solo para visualización en sesión.  
- **Reset** limpia variables y vuelve a defaults.

---

## ✅ Checklist
- [ ] Arranque = ON  
- [ ] Seleccionar plenum activo  
- [ ] Configurar setpoints  
- [ ] Definir N y Δt  
- [ ] Observar estabilización  
- [ ] Iniciar muestreo  
- [ ] Revisar estadísticas  
- [ ] Reset o repetir ciclo

---

## 🔧 Consideraciones Técnicas
- Sensar solo el plenum activo.  
- Estadísticas simples en controlador; análisis avanzado en Excel.  
- No guardar registros permanentes (limitación hardware).  
- Reset protege memoria y prepara siguiente ciclo.
