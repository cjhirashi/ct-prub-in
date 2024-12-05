# Sistema de Automatización de Aire Acondicionado - INNES Aire

Este repositorio contiene la documentación y configuraciones del sistema de automatización de aire acondicionado implementado en las **instalaciones de INNES Aire**, diseñado para garantizar la eficiencia energética, el confort térmico y la flexibilidad operativa.

## Descripción General

El sistema automatizado utiliza controladores **DDC de KMC** y dispositivos compatibles con **BACnet** para gestionar diversos subsistemas, incluyendo:
- **Unidades Manejadoras de Aire (UMA-01 y UMA-02)**: Encargadas de distribuir y acondicionar el aire en áreas clave como oficinas, el Cuarto de Pruebas y la Sala de Juntas principal.
- **Planta de Agua Helada (PAH)**: Provee agua helada a las UMA y a los Fan and Coil de las oficinas de ingeniería, garantizando el enfriamiento necesario para el control de temperatura.
- **Planta de Agua Fría (PAF)**: Entrega agua fría para el funcionamiento del sistema y la regulación de temperatura de las UMA.
- **Planta de Agua Caliente (PAC)**: Suministra agua caliente para el control de temperatura en las UMA y las Vigas Frías.
- **Sistemas de Vigas Frías**: Difusores de aire que realizan un pos-acondicionamiento adicional al aire suministrado por la UMA-01, permitiendo un control zonal preciso de la temperatura.
- **Cuarto de Pruebas**: Laboratorio especializado para pruebas de rendimiento en rejillas y difusores de aire, equipado con un sistema de plenums y VAVs para condiciones controladas.

## Dispositivos Integrados en la Red BACnet

### **Dispositivos por Protocolo BACnet MS/TP**

1. **CHILLER Agua Fría**
   - **Marca/Modelo**: ClimaFlex FLG Modbus-BACnet
   - **Dirección Interna (DI)**: 11
   - **Dirección MAC**: 11

2. **CHILLER Agua Helada**
   - **Marca/Modelo**: ClimaFlex FLG Modbus-BACnet
   - **Dirección Interna (DI)**: 12
   - **Dirección MAC**: 12

3. **PAH-PAF-PAC-UMA02**
   - **Marca/Modelo**: KMC BAC-5901C
   - **Dirección Interna (DI)**: 10002
   - **Dirección MAC**: 5

4. **UMA-01**
   - **Marca/Modelo**: KMC BAC-5901C
   - **Dirección Interna (DI)**: 10003
   - **Dirección MAC**: 6

5. **VIGAS FRIAS**
   - **Marca/Modelo**: KMC BAC-5901C
   - **Dirección Interna (DI)**: 10001
   - **Dirección MAC**: 4

6. **EV-AC**
   - **Marca/Modelo**: Belimo EV-APP-3-12-328
   - **Dirección Interna (DI)**: 10008
   - **Dirección MAC**: 8

7. **EV-AF**
   - **Marca/Modelo**: Belimo EV-APP-3-12-328
   - **Dirección Interna (DI)**: 10009
   - **Dirección MAC**: 9

8. **CUARTO PRUEBAS 1-1**
   - **Marca/Modelo**: KMC BAC-5901C
   - **Dirección Interna (DI)**: 10021
   - **Dirección MAC**: 21

9. **CUARTO PRUEBAS 1-2**
   - **Marca/Modelo**: KMC BAC-5901C
   - **Dirección Interna (DI)**: 10022
   - **Dirección MAC**: 22

10. **SPT3_CP**
    - **Marca/Modelo**: Veris Industries TWLPXXX4E4
    - **Dirección Interna (DI)**: 133023
    - **Dirección MAC**: 23

11. **SPT4_CP**
    - **Marca/Modelo**: Veris Industries TWLPXXX4E4
    - **Dirección Interna (DI)**: 133024
    - **Dirección MAC**: 24

12. **SPT1_CP**
    - **Marca/Modelo**: Veris Industries TWLPXXX4E4
    - **Dirección Interna (DI)**: 133025
    - **Dirección MAC**: 25

13. **SPT2_CP**
    - **Marca/Modelo**: Veris Industries TWLPXXX4E4
    - **Dirección Interna (DI)**: 133026
    - **Dirección MAC**: 26

### **Dispositivos por Protocolo BACnet IP**

1. **DISPLAY**
   - **Marca/Modelo**: Loytec LVIS
   - **Dirección Interna (DI)**: 10010
   - **Dirección IP**: 10.0.0.251
   - **Puerto**: 47808

## Estructura del Repositorio

```plaintext
📂 Sistema-Aire-INNES
├── 📂 Plantas-de-Agua
│   ├── 📂 PAH
│   │   └── README.md
│   ├── 📂 PAF
│   │   └── README.md
│   ├── 📂 PAC
│   │   └── README.md
│   └── 📂 UMA-02
│       └── README.md
├── 📂 UMA-01
│   └── README.md
├── 📂 Vigas-Frias
│   └── README.md
├── 📂 Cuarto-de-Pruebas
│   ├── 📂 Controlador-1
│   │   └── README.md
│   ├── 📂 Controlador-2
│   │   └── README.md
│   └── 📂 Sensores
│       └── README.md
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

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para más detalles.