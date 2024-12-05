# SubSistema: Cuarto de Pruebas - INNES Aire

El **Cuarto de Pruebas** es un laboratorio especializado implementado en INNES Aire para realizar pruebas de rendimiento en rejillas, difusores de aire y cajas VAV. Su diseño permite medir, ajustar y evaluar el flujo de aire, la presión y la eficiencia de estos componentes bajo condiciones controladas.

## Descripción General

El subsistema está compuesto por:
- **7 Plenums**:
  - **6 plenums de suministro** para la inyección de aire.
  - **1 plenum de extracción** para mantener el balance de presión.
- **15 Cajas VAV**:
  - Cada caja VAV incluye:
    - **Sensor de caudal** para medir el flujo de aire.
    - **Actuador proporcional** para controlar la compuerta VAV.
    - **Actuador On/Off** para una compuerta de bloqueo.
- **Sensores**:
  - **4 Sensores de temperatura del cuarto** (BACnet MS/TP), independientes a los controladores.
  - **1 Sensor de temperatura de suministro de aire**.
  - **Sensores de presión diferencial**:
    - Plenum 1: 2 sensores para medir la caída de presión.
    - Plenums 2, 4, 5, 6, 7: 1 sensor cada uno.
    - Plenum 3: No cuenta con sensor de presión diferencial.
  - **7 Sensores de velocidad de aire** montados en un árbol de pruebas.
  - **1 Sensor móvil de velocidad de aire**.

## Funcionalidades Clave

1. **Pruebas de Rendimiento**:
   - Realiza mediciones precisas de flujo, presión y temperatura en rejillas, difusores y cajas VAV.
   - Evalúa la eficiencia de los componentes bajo condiciones simuladas.
2. **Calibración de Sensores**:
   - Garantiza la precisión en la medición de caudales, presiones diferenciales y velocidades de aire.
3. **Control de Flujo**:
   - Permite la activación individual de plenums y un ajuste dinámico de las VAVs según las necesidades específicas de las pruebas.

## Estructura del Directorio

```plaintext
📂 Cuarto-de-Pruebas
├── 📂 Controlador-1
│   └── README.md
├── 📂 Controlador-2
│   └── README.md
├── 📂 Sensores
│   └── README.md
├── 📂 Documentación
│   ├── Diagramas/
│   ├── Manuales/
│   └── Guías/
└── README.md
```

## Documentación Relacionada

- Manuales técnicos y guías operativas de los controladores y módulos de expansión.
- Diagramas y esquemas eléctricos disponibles en la carpeta `Documentación/Diagramas`.
