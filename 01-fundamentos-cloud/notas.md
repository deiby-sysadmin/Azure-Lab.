# Fundamentos de Cloud y Azure

## ☁️ ¿Qué es el Cloud Computing?
El cloud computing permite consumir recursos de TI (máquinas virtuales, redes, almacenamiento, identidades) como servicios bajo demanda.  
La clave es que no gestionas la infraestructura física, solo administras lo que usas.

## 🔵 ¿Qué es Microsoft Azure?
Azure es la plataforma cloud de Microsoft que ofrece servicios de computación, redes, almacenamiento, seguridad e identidad.  
Mi enfoque en este curso es aprender los servicios esenciales para un rol de Sysadmin.

## 🛡️ Modelo de Responsabilidad Compartida
En Azure, la seguridad se divide entre Microsoft y el cliente:

- **Microsoft**: seguridad física, hardware, red global, hipervisores, disponibilidad.
- **Cliente (yo)**: configuración de máquinas virtuales, puertos, identidades, roles, redes, backups.

### Ejemplo práctico
Si creo una VM:
- Microsoft asegura el datacenter y la infraestructura.
- Yo debo asegurar:
  - puertos abiertos  
  - NSG  
  - contraseñas  
  - actualizaciones  
  - acceso remoto  

Este modelo es clave para entender qué debo administrar como Sysadmin en Azure.

## 🎯 Objetivo de este módulo
Comprender la base conceptual antes de crear recursos reales, para aplicar buenas prácticas desde el primer laboratorio.
