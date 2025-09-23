# 🏢 Sistema de Automatización HVAC - INNES Aire

![Status](https://img.shields.io/badge/status-operativo-green)
![Protocol](https://img.shields.io/badge/protocol-BACnet-blue)
![Controllers](https://img.shields.io/badge/controladores-8-orange)
![Devices](https://img.shields.io/badge/dispositivos-14-purple)

> **Sistema integral de automatización** para acondicionamiento de aire, plantas de agua y laboratorio de pruebas especializadas, implementado en las instalaciones de **INNES Aire**.

---

## 🎯 **Visión General del Sistema**

### **Capacidades Principales**
- 🌡️ **Control de Clima**: Gestión automática de temperatura y calidad del aire
- ⚡ **Eficiencia Energética**: Optimización de consumo mediante algoritmos PI avanzados  
- 🔬 **Laboratorio Especializado**: Cuarto de pruebas para componentes HVAC
- 📊 **Monitoreo Integral**: Supervisión en tiempo real vía HMI centralizado

### **Infraestructura Técnica**
- **Red de Comunicación**: BACnet MS/TP e IP
- **Controladores**: 8 DDC KMC distribuidos estratégicamente
- **Protocolo Principal**: BACnet para interoperabilidad total
- **HMI**: Loytec LVIS para supervisión centralizada

---

## 🏗️ **Arquitectura del Sistema**

```
    🖥️ HMI Centralizado (LVIS)
         │
         │ BACnet/IP
         │
    🔄 Router BACnet (MS/TP ↔ IP)
         │
    ┌────┴────┬────────┬────────┬────────┐
    │         │        │        │        │
  UMA-01   UMA-02   Plantas   Vigas   Cuarto
    │         │        │        │      Pruebas
  6 DDC     5 DDC     11 DDC    4 DDC   21,22 DDC
```

---

## 🏭 **Subsistemas Principales**

<table>
<tr>
<td width="50%">

### **🌬️ Unidades Manejadoras**
- **[UMA-01](./UMA-01/README.md)** - Acondicionamiento principal
- **[UMA-02](./Plantas-de-Agua/UMA-02/README.md)** - Distribución secundaria

### **💧 Plantas de Agua**
- **[PAH](./Plantas-de-Agua/PAH/README.md)** - Agua Helada (7-12°C)
- **[PAF](./Plantas-de-Agua/PAF/README.md)** - Agua Fría (16-20°C)  
- **[PAC](./Plantas-de-Agua/PAC/README.md)** - Agua Caliente (40-50°C)

</td>
<td width="50%">

### **❄️ Control Zonal**
- **[Vigas Frías](./Vigas-Frias/README.md)** - 4 zonas independientes
- **Válvulas Belimo** - Control preciso de flujo

### **🧪 Laboratorio**
- **[Cuarto de Pruebas](./Cuarto-de-Pruebas/README.md)** - 15 VAVs + 7 Plenums
- **Calibración** - Sistemas de medición avanzados
- **I+D** - Desarrollo de componentes HVAC

</td>
</tr>
</table>

---

## 🖧 **Red de Controladores**

### **BACnet MS/TP Network**

| **Sistema** | **Controlador** | **Modelo** | **DI** | **MAC** | **Estado** |
|-------------|------------------|------------|--------|---------|------------|
| UMA-01 | Principal | KMC BAC-5901C | `10003` | `6` | 🟢 Operativo |
| Plantas de Agua | PAH-PAF-PAC-UMA02 | KMC BAC-5901C | `10002` | `5` | 🟢 Operativo |
| Vigas Frías | Control Zonal | KMC BAC-5901C | `10001` | `4` | 🟢 Operativo |
| Cuarto Pruebas | Controlador 1 | KMC BAC-5901C | `10021` | `21` | 🟢 Operativo |
| Cuarto Pruebas | Controlador 2 | KMC BAC-5901C | `10022` | `22` | 🟢 Operativo |

### **Dispositivos Especializados**

| **Dispositivo** | **Función** | **Protocolo** | **DI** | **MAC** |
|-----------------|-------------|---------------|--------|---------|
| Chiller Agua Helada | ClimaFlex FLG | Modbus-BACnet | `12` | `12` |
| Chiller Agua Fría | ClimaFlex FLG | Modbus-BACnet | `11` | `11` |
| EV-AC | Belimo Válvula | BACnet MS/TP | `10008` | `8` |
| EV-AF | Belimo Válvula | BACnet MS/TP | `10009` | `9` |

### **Sensores Independientes**
- **SPT1-4_CP**: 4x Sensores Veris temperatura (MAC 23-26)

### **HMI & Supervisión**

| **Equipo** | **Protocolo** | **IP** | **Puerto** | **Función** |
|------------|---------------|---------|-----------|------------|
| LVIS Display | BACnet/IP | `10.0.0.251` | `47808` | Supervisión Central |

---

## 📂 **Navegación del Repositorio**

```
📂 Sistema-Aire-INNES/
├── 📁 UMA-01/                    # Unidad Manejadora Principal
├── 📁 Plantas-de-Agua/           # PAH, PAF, PAC, UMA-02  
├── 📁 Vigas-Frias/               # Control Zonal (4 zonas)
├── 📁 Cuarto-de-Pruebas/         # Laboratorio (15 VAVs + 7 Plenums)
├── 📁 Documentación/             # Diagramas, Manuales, Guías
├── 📁 Recursos/                  # Imágenes, Videos, Referencias
└── 📄 README.md                  # Este archivo
```

### **🔗 Enlaces Rápidos**
- **[🚀 Guía de Inicio Rápido](./Documentación/Guías/inicio-rapido.md)**
- **[🔧 Manual de Mantenimiento](./Documentación/Manuales/mantenimiento.md)**
- **[⚡ Procedimientos de Emergencia](./Documentación/Guías/emergencias.md)**
- **[📊 Dashboard de Monitoreo](http://10.0.0.251:47808)** *(HMI LVIS)*

---

## 🎛️ **Puntos de Control Críticos**

### **Parámetros Operacionales**
| **Sistema** | **Setpoint** | **Rango Operación** | **Alarma** |
|-------------|--------------|-------------------|------------|
| PAH | 7°C | 5-12°C | <3°C / >15°C |
| PAF | 18°C | 16-22°C | <14°C / >25°C |
| PAC | 45°C | 40-55°C | <35°C / >60°C |
| Vigas Frías | 22°C | 20-26°C | <18°C / >28°C |

### **Estados del Sistema**
- 🟢 **Automático**: Control PI activo, sin intervención manual
- 🟡 **Manual**: Operación con setpoints fijos 
- 🔴 **Alarma**: Requiere intervención inmediata
- ⭕ **Mantenimiento**: Sistema fuera de servicio programado

---

## ⚠️ **Seguridad y Precauciones**

### **🚨 ANTES de cualquier intervención**
1. **Verificar estado del sistema** en HMI LVIS
2. **Desenergizar circuitos** en tablero correspondiente
3. **Colocar tarjeta LOTO** (Lock Out Tag Out)
4. **Verificar ausencia de tensión** con multímetro

### **🔧 Contactos de Emergencia**
- **Supervisor Técnico**: Ext. 101
- **Mantenimiento 24/7**: Ext. 911
- **Emergencias Eléctricas**: 📞 +52-XXX-XXX-XXXX

---

## 📈 **Estadísticas del Sistema**

<div align="center">

![Uptime](https://img.shields.io/badge/uptime-99.2%25-green)
![Efficiency](https://img.shields.io/badge/eficiencia-87%25-blue)
![Energy Save](https://img.shields.io/badge/ahorro_energético-23%25-orange)
![Devices Online](https://img.shields.io/badge/dispositivos_online-14/14-brightgreen)

</div>

---

## 🔄 **Última Actualización**

- **Fecha**: Septiembre 2025
- **Versión**: 2.0
- **Cambios**: Reestructuración completa de documentación
- **Responsable**: Equipo Técnico INNES

---

<div align="center">

**💡 Para soporte técnico o sugerencias, contacta al equipo de automatización**

[![Manual](https://img.shields.io/badge/📖-Manual_Completo-blue)](./Documentación/Manuales/)
[![Videos](https://img.shields.io/badge/🎥-Videos_Tutoriales-red)](./Recursos/Videos/)
[![FAQ](https://img.shields.io/badge/❓-FAQ-yellow)](./Documentación/Guías/faq.md)

</div>