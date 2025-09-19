# 🧪 Sistema: Cuarto de Pruebas - INNES Aire

![badge-status](https://img.shields.io/badge/status-operativo-green)
![badge-protocol](https://img.shields.io/badge/protocol-BACnet-blue)
![badge-license](https://img.shields.io/badge/license-MIT-orange)

El **Cuarto de Pruebas** es un laboratorio especializado implementado en INNES Aire para realizar **pruebas de rendimiento en rejillas, difusores de aire y cajas VAV**. Su diseño permite medir, ajustar y evaluar el flujo de aire, la presión y la eficiencia de estos componentes bajo condiciones controladas.

---

## 📖 Descripción General

El sistema está compuesto por:

* **7 Plenums**:

  * 6 plenums de **suministro** para la inyección de aire.
  * 1 plenum de **extracción** para mantener el balance de presión.
* **15 Cajas VAV**:

  * Cada caja VAV incluye:

    * **Sensor de caudal** para medir el flujo de aire.
    * **Actuador proporcional** para controlar la compuerta VAV.
    * **Actuador On/Off** para una compuerta de bloqueo.
* **Sensores**:

  * 4 Sensores de temperatura del cuarto (BACnet MS/TP), independientes a los controladores.
  * 1 Sensor de temperatura de suministro de aire.
  * Sensores de presión diferencial:

    * Plenum 1: 2 sensores para caída de presión.
    * Plenums 2, 4, 5, 6, 7: 1 sensor cada uno.
    * Plenum 3: No cuenta con sensor de presión diferencial.
  * 7 Sensores de velocidad de aire montados en un **árbol de pruebas**.
  * 1 Sensor móvil de velocidad de aire.

---

## 🖧 Controladores

El cuarto de pruebas se controla mediante **dos DDC KMC BAC-5901C** conectados en red BACnet MS/TP:

| Nombre             | Modelo        | Dirección Interna (DI) | MAC |
| ------------------ | ------------- | ---------------------- | --- |
| Cuarto Pruebas 1-1 | KMC BAC-5901C | 10021                  | 21  |
| Cuarto Pruebas 1-2 | KMC BAC-5901C | 10022                  | 22  |

Estos controladores administran el funcionamiento de las cajas VAV, plenums y sensores asociados.

---

## ⚙️ Funcionalidades Clave

1. **Pruebas de Rendimiento**:

   * Medición precisa de flujo, presión y temperatura en rejillas, difusores y cajas VAV.
   * Evaluación de la eficiencia de los componentes bajo condiciones simuladas.

2. **Calibración de Sensores**:

   * Verificación y ajuste de la precisión en caudales, presiones diferenciales y velocidades de aire.

3. **Control de Flujo**:

   * Activación individual de plenums.
   * Ajuste dinámico de VAVs según las necesidades de la prueba.

---

## 📋 Arquitectura de Pruebas (Vista Simplificada)

```plaintext
                 ┌─────────────────────────┐
                 │   Controlador 1 (DDC)   │
                 │   KMC BAC-5901C (10021) │
                 └───────────┬─────────────┘
                             │
                 ┌───────────┴─────────────┐
                 │   Plenums / VAVs        │
                 │   Sensores asociados    │
                 └─────────────────────────┘

                 ┌─────────────────────────┐
                 │   Controlador 2 (DDC)   │
                 │   KMC BAC-5901C (10022) │
                 └───────────┬─────────────┘
                             │
                 ┌───────────┴─────────────┐
                 │   Plenums / VAVs        │
                 │   Sensores asociados    │
                 └─────────────────────────┘
```

---

## 📂 Estructura del Directorio

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

---

## ⚠️ Seguridad y Precauciones

* Antes de manipular plenums y VAVs, **verificar desenergización** de actuadores.
* Los sensores móviles deben conectarse únicamente por personal autorizado.
* Uso obligatorio de **EPP**: guantes, gafas de seguridad, casco.
* Mantener calibración periódica de sensores para confiabilidad de las pruebas.

---

## 📚 Documentación Relacionada

* Manuales técnicos y guías operativas de los controladores y módulos de expansión.
* Diagramas eléctricos y de red disponibles en la carpeta `Documentación/Diagramas`.
* Protocolos de calibración disponibles en `Documentación/Guías`.

