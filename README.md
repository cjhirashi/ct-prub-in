# 🌬️ Sistema de Automatización de Aire Acondicionado - INNES Aire

![badge-status](https://img.shields.io/badge/status-en%20uso-green)
![badge-protocol](https://img.shields.io/badge/protocol-BACnet-blue)
![badge-license](https://img.shields.io/badge/license-MIT-orange)

Este repositorio contiene la **documentación y configuraciones** del sistema de automatización de aire acondicionado implementado en las **instalaciones de INNES Aire**, diseñado para garantizar:

* ✅ **Eficiencia energética**
* ✅ **Confort térmico**
* ✅ **Flexibilidad operativa**

---

## 📖 Descripción General

El sistema automatizado utiliza **controladores DDC KMC** y dispositivos compatibles con **BACnet MS/TP e IP**, gestionando los siguientes subsistemas principales:

* **Unidades Manejadoras de Aire (UMA-01 y UMA-02)** → distribución y acondicionamiento de aire.
* **Planta de Agua Helada (PAH)** → provee agua helada a UMA y fan & coils.
* **Planta de Agua Fría (PAF)** → suministro de agua fría para regulación térmica.
* **Planta de Agua Caliente (PAC)** → suministro de agua caliente para UMA y vigas frías.
* **Sistemas de Vigas Frías** → pos-acondicionamiento y control zonal preciso.
* **Cuarto de Pruebas** → laboratorio especializado con plenums y VAVs.

---

## 🖧 Arquitectura de Comunicación

```plaintext
            ┌───────────────┐
            │   BACnet/IP   │
            │   (LVIS HMI)  │
            └───────┬───────┘
                    │
            ┌───────┴─────────┐
            │   Router BACnet │
            │  (MS/TP ↔ IP)   │
            └───────┬─────────┘
         ┌──────────┴──────────┐
         │ Controladores DDC   │
         │ (UMA, Plantas, CP)  │
         └──────────┬──────────┘
             Sensores & Actuadores
```

---

## 🔌 Dispositivos Integrados

### **📡 BACnet MS/TP**

| Equipo              | Marca/Modelo                | Dirección Interna | MAC |
| ------------------- | --------------------------- | ----------------- | --- |
| Chiller Agua Fría   | ClimaFlex FLG Modbus-BACnet | 11                | 11  |
| Chiller Agua Helada | ClimaFlex FLG Modbus-BACnet | 12                | 12  |
| PAH-PAF-PAC-UMA02   | KMC BAC-5901C               | 10002             | 5   |
| UMA-01              | KMC BAC-5901C               | 10003             | 6   |
| Vigas Frías         | KMC BAC-5901C               | 10001             | 4   |
| EV-AC               | Belimo EV-APP-3-12-328      | 10008             | 8   |
| EV-AF               | Belimo EV-APP-3-12-328      | 10009             | 9   |
| Cuarto Pruebas 1-1  | KMC BAC-5901C               | 10021             | 21  |
| Cuarto Pruebas 1-2  | KMC BAC-5901C               | 10022             | 22  |
| SPT3\_CP            | Veris TWLPXXX4E4            | 133023            | 23  |
| SPT4\_CP            | Veris TWLPXXX4E4            | 133024            | 24  |
| SPT1\_CP            | Veris TWLPXXX4E4            | 133025            | 25  |
| SPT2\_CP            | Veris TWLPXXX4E4            | 133026            | 26  |

### **🌐 BACnet/IP**

| Equipo  | Marca/Modelo | Dirección Interna | Dirección IP | Puerto |
| ------- | ------------ | ----------------- | ------------ | ------ |
| DISPLAY | Loytec LVIS  | 10010             | 10.0.0.251   | 47808  |

---

## 📂 Estructura del Repositorio

```plaintext
📂 Sistema-Aire-INNES
├── 📂 Plantas-de-Agua
│   ├── 📂 PAH
│   ├── 📂 PAF
│   ├── 📂 PAC
│   └── 📂 UMA-02
├── 📂 UMA-01
├── 📂 Vigas-Frias
├── 📂 Cuarto-de-Pruebas
│   ├── 📂 Controlador-1
│   ├── 📂 Controlador-2
│   └── 📂 Sensores
├── 📂 Documentación
│   ├── 📂 Diagramas
│   ├── 📂 Manuales
│   └── 📂 Guías
├── 📂 Recursos
│   ├── 📂 Imágenes
│   ├── 📂 Videos
│   └── 📂 Referencias
└── README.md
```

---

## ⚠️ Seguridad y Precauciones

* Antes de intervenir en tableros eléctricos, asegúrese de **desenergizar** los circuitos.
* Revise siempre las presiones y temperaturas de operación antes de realizar maniobras.
* Utilice **EPP (equipo de protección personal)** apropiado: guantes dieléctricos, gafas, calzado de seguridad.
* Siga lineamientos de **norma NOM-001-SEDE** y **ASHRAE** en instalaciones.

---

## 📜 Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo [LICENSE](./LICENSE) para más detalles.
