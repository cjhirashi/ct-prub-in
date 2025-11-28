# ⚙️ CP – Operativo – Proceso de Medición de Tiro en Cuarto de Pruebas

## 🔷 A. Sistema KMC como Instrumento de Adquisición de Datos

### 1. Activación del Sistema de Prueba
- Habilitar **modo de prueba Tiro** desde la interfaz gráfica (botón ON/OFF superior).
- Seleccionar **plenum** y cajas VAV disponibles (Grande, Mediana, Chica).
- Configurar **Caudal objetivo (CFM)**:
  - Valor mínimo por defecto según tamaño.
  - Permite ingresar otro valor dentro del rango operativo.
- Botón ON/OFF para activar/desactivar cada caja.
- **Caudal Total**: suma automática de los caudales activos.

**Persistencia:** parámetros se mantienen mientras la prueba está activa.

### 2. Organización de la Interfaz
Esta prueba consta de **una sola pestaña**, que incluye:
- **Panel de Control** (lado izquierdo):
  - Selección de plenum.
  - SetPoints de caudal por caja.
  - Parámetros de muestreo: número de muestras (N), intervalo (Δt), grupo.
  - Botones: `[INICIO]`, `[DETENER]`, `[RESET]`.
- **Panel de Monitoreo** (zona central):
  - Árbol de transductores con 8 posiciones.
  - Lecturas en tiempo real: velocidad (FPM) por altura.
  - Estadísticas: promedio, máximo, mínimo.

**Nota adicional:** En la interfaz solo se muestra el **número del transductor** y sus valores de velocidad (FPM). No se visualizan altura ni coordenadas en el controlador.

**Importante:** Los transductores deben comenzar a dar lecturas **desde el momento en que se activa la prueba**, incluso antes de iniciar el muestreo, para permitir al usuario ajustar la posición y altura según lo que sensan. Una vez que los transductores están en la posición correcta y el caudal se estabiliza, el usuario decide iniciar el ciclo de muestreo.

### Flujo operativo:
1. Activar modo de prueba.
2. Seleccionar plenum y cajas.
3. Configurar caudales, N, Δt y Grupo.
4. Esperar estabilización de caudal.
5. Ajustar posición y altura de transductores según lecturas en tiempo real.
6. Iniciar muestreo.
7. Monitorear lecturas en tiempo real.
8. Finalizar ciclo y revisar estadísticas.

---

## 🔷 B. Medición Externa y Análisis Estadístico en Excel
- Registrar simultáneamente en Excel:
```
Grupo | Caudal objetivo | Velocidad por altura (FPM) | Promedio | Máximo | Mínimo | Altura transductor | Coordenadas árbol | Fecha | Obs
```
**Importante:** En el archivo Excel se debe registrar la **altura del transductor** y las **coordenadas de posición del árbol** junto con las lecturas de velocidad, para permitir análisis posteriores.

- Validar estabilidad (sin oscilaciones).
- Posteriormente, extrapolar perfil de velocidad en plano transversal (definición futura).

---

## 🔷 C. Implementación y Validación en Sistema KMC
- Ejecutar ciclos completos.
- Validar consistencia de lecturas entre grupos.
- Documentar resultados y respaldar externamente.

---

## ✅ Checklist del Proceso Completo
**Fase 1: Configuración**
- Activar modo de prueba.
- Seleccionar plenum y cajas.
- Configurar caudales y parámetros de muestreo.

**Fase 2: Ejecución**
- Esperar estabilización.
- Ajustar posición y altura de transductores.
- Iniciar muestreo.
- Monitorear lecturas.

**Fase 3: Validación**
- Revisar promedio, máximo y mínimo.
- Confirmar datos válidos.

**Fase 4: Documentación**
- Guardar dataset y análisis en Excel.

---

## 🔧 Consideraciones Técnicas
- Persistencia de parámetros mientras la prueba está activa.
- `[RESET]` borra datos y vuelve a valores por defecto.
- Manejo de errores:
  - Sensor fuera de rango → alerta en tiempo real.
  - Ciclo incompleto → no calcular estadísticas.

**Nota:** Aunque la interfaz no muestra altura ni coordenadas, estos datos son obligatorios en el registro externo (Excel). Además, las lecturas previas al muestreo son críticas para posicionar correctamente los transductores.
