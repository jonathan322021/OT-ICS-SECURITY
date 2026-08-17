# 🏭 Laboratorio OT/ICS - Seguridad Industrial con Pruebas de Penetración

## 📌 Descripción del Proyecto

Este laboratorio implementa una arquitectura de **Zonas y Conductos** basada en **ISA/IEC 62443** con un enfoque práctico de **pruebas de seguridad ofensivas y defensivas**. Incluye una máquina **Kali Linux** para realizar pruebas de penetración controladas en el entorno OT.

**Objetivos:**
- ✅ Segmentar redes IT/OT con pfSense
- ✅ Aplicar principio de Mínimo Privilegio
- ✅ Realizar pruebas de seguridad con Kali Linux
- ✅ Establecer línea base de tráfico OT
- ✅ Detectar y responder a amenazas

---

## 🏗️ Arquitectura del Laboratorio

### Topología de Red

![Topología Actualizada](capturas/topologia-actualizada.png)

### Segmentación de Redes

| Zona | Subred | Componentes | Función |
|------|--------|-------------|---------|
| **Zona IT (LAN)** | 192.168.10.0/24 | Windows Admin, IT Server | Administración y monitoreo |
| **Zona OT (Industrial)** | 192.168.20.0/24 | Kali Linux, OT Server, HMI, PLC | Seguridad ofensiva y control industrial |
| **DMZ** | Interfaces em1/em2 | pfSense | Firewall segmentador |

### Componentes del Laboratorio

| Componente | IP | Sistema | Función |
|------------|-----|---------|---------|
| **pfSense** | 192.168.10.1 (LAN) / 192.168.20.1 (OT) | pfSense | Firewall y enrutador |
| **Windows Admin** | 192.168.10.100 | Windows 10/11 | Administración y monitoreo |
| **Kali Linux** | 192.168.20.10 | Kali Linux | Pruebas de penetración OT |
| **OT Server** | 192.168.20.10 | Ubuntu Server | Servidor de aplicaciones OT |
| **HMI** | 192.168.20.20 | Windows/Linux | Interfaz Hombre-Máquina |
| **PLC** | 192.168.20.30 | OpenPLC | Controlador Lógico Programable |
| **IT Server** | 192.168.10.10 | Ubuntu/Windows | Servidor de respaldo |

> **Nota:** Kali Linux y OT Server comparten la misma IP (192.168.20.10) en el diagrama. En la práctica, deben tener IPs diferentes o ejecutarse en momentos distintos.

---

## 🔒 Reglas de Firewall

### Matriz de Comunicación

| Origen | Destino | Protocolo | Puerto | Estado | Propósito |
|--------|---------|-----------|--------|--------|-----------|
| Windows Admin (10.100) | OT Server (20.10) | TCP | 22 | ✅ **Allowed** | Administración SSH |
| Kali Linux (20.10) | OT Server (20.10) | TCP | 22, 80, 443 | ✅ **Allowed** | Pruebas de seguridad |
| Kali Linux (20.10) | HMI (20.20) | TCP | 502 | ⚠️ **Test** | Escaneo Modbus |
| Kali Linux (20.10) | PLC (20.30) | TCP | 502 | ⚠️ **Test** | Fuzzing Modbus |
| LAN (10.0/24) | OT (20.0/24) | Any | Any | 🚫 **Blocked** | Bloqueo general |
| OT (20.0/24) | LAN (10.0/24) | Any | Any | 🚫 **Blocked** | Prevención exfiltración |

---

## 🎯 Escenarios de Pruebas con Kali Linux

### Escenario 1: Escaneo de Red Industrial
```bash
# Desde Kali Linux
nmap -sS -p 502 192.168.20.0/24
# Identificar dispositivos Modbus en la red OT
