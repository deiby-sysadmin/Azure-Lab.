# 03. Máquinas Virtuales en Azure

Este módulo documenta la creación, configuración y validación de una máquina virtual Linux en Azure, incluyendo red, discos, seguridad, acceso SSH y despliegue automático mediante cloud‑init.

---

## 1. Panel de máquinas virtuales
Vista inicial del portal donde se gestionan todas las máquinas virtuales.

![Panel de máquinas virtuales](./03-maquinas-virtuales/capturas/01-panel-maquinas-virtuales.png)

---

## 2. Crear una máquina virtual
Pantalla inicial del asistente para crear una nueva VM.

![Crear VM](./03-maquinas-virtuales/capturas/02-crear-vm.png)

---

## 3. Datos básicos de la VM
Configuración principal de la instancia:

- Nombre de la VM  
- Región  
- Zona de disponibilidad  
- Imagen: Ubuntu Server 24.04 LTS  
- Arquitectura x64  
- Tamaño Standard_B2ts_v2  
- Puertos públicos HTTP (80) y SSH (22)

![Datos básicos](./03-maquinas-virtuales/capturas/03-datos-basicos.png)

---

## 4. Configuración de discos
Disco del sistema operativo, tipo de almacenamiento y opciones avanzadas.

![Discos](./03-maquinas-virtuales/capturas/05-discos.png)

---

## 5. Configuración de red
Red virtual, subred, IP pública, NSG y puertos permitidos.

![Redes](./03-maquinas-virtuales/capturas/06-redes.png)

---

## 6. Script cloud-init
Script utilizado para instalar Nginx y desplegar una página web automáticamente.

```bash
#!/bin/bash
sudo su
apt-get -y update
apt-get -y install nginx
echo "<h1>Hola Mundo desde $(hostname)</h1>" > /var/www/html/index.html
```

![Cloud-init](./03-maquinas-virtuales/capturas/07-cloud-init.png)

---

## 7. Revisión y creación
Resumen final de la configuración antes del despliegue.

![Revisión y creación](./03-maquinas-virtuales/capturas/08-revision-creacion.png)

---

## 8. Implementación completada
Confirmación de que la máquina virtual fue creada correctamente.

![Implementación completada](./03-maquinas-virtuales/capturas/09-implementacion-completada.png)

---

## 9. Panel general de la VM
Información principal de la máquina virtual:

- IP pública  
- IP privada  
- Disco  
- Red  
- SO  
- Tamaño  
- Zona  

![Panel de la VM](./03-maquinas-virtuales/capturas/10-panel-vm.png)

---

## 10. Validación del servicio web
Acceso vía navegador a la página generada por cloud‑init.

![Hola Mundo](./03-maquinas-virtuales/capturas/11-web-hola-mundo.png)

---

## 11. Conexión SSH nativa
Comando SSH y validación del acceso remoto.

![SSH nativo](./03-maquinas-virtuales/capturas/12-ssh-nativo.png)

---

# Conclusión

Este módulo demuestra:

- Creación completa de una VM Linux  
- Configuración de red, discos y seguridad  
- Uso de claves SSH  
- Automatización con cloud‑init  
- Validación del servicio desplegado  
- Documentación profesional del proceso
