# 06. Redes Virtuales en Azure

Este módulo documenta la creación y configuración de una **Azure Virtual Network (VNet)**, sus subredes y la aplicación de un **Network Security Group (NSG)** con una regla de entrada SSH, como base para conectar recursos de Azure de forma segura.

---

## Recursos desplegados

| Recurso | Tipo | Detalle | Coste |
|---|---|---|---|
| `vnet-lab-deiby` | Virtual Network | Espacio `10.0.0.0/16` | 0 € |
| `default` | Subnet | `10.0.0.0/24` | 0 € |
| `defaultA` | Subnet | `10.0.1.0/24` | 0 € |
| `NGS1` | Network Security Group | Regla SSH entrada | 0 € |

**Región:** Spain Central
**Resource Group:** `demo_redes`

---

## Conceptos teóricos

### Azure Virtual Network

Diagrama introductorio que explica qué es una VNet: una red privada aislada en la nube que permite conectar recursos de Azure de forma segura, crear subredes, aplicar filtros de seguridad y gestionar bloques de IP privadas.

![Concepto de Azure Virtual Network](./capturas/21-teoria-vnet.png)

### Subredes (Subnets)

Explica cómo particionar una VNet en subredes públicas (accesibles desde Internet) y privadas (aisladas), donde cada subred debe tener un intervalo CIDR único dentro del espacio de direcciones.

![Subredes públicas y privadas](./capturas/20-teoria-subredes.png)

### VNet Peering (Emparejamiento)

Diagrama que muestra cómo conectar dos VNet de forma privada, sin pasar por Internet. Las VNets no deben tener CIDR superpuestos y la conexión **no es transitiva**.

![Concepto de VNet Peering](./capturas/22-teoria-vnet-peering.png)

---

## Pasos realizados

### 1. Acceso al servicio

Búsqueda del servicio Red Virtual en los favoritos del portal.

![Servicio Red Virtual en favoritos](./capturas/01-servicio-red-virtual.png)

Panel inicial de Redes Virtuales, sin recursos creados todavía.

![Panel de Redes Virtuales vacío](./capturas/02-panel-redes-vacio.png)

---

### 2. Creación de la VNet

Asistente de creación con nombre `vnet-lab-deiby`, resource group `demo_redes` y región Spain Central.

![Crear VNet — Datos básicos](./capturas/03-crear-vnet-basicos.png)

Configuración del espacio de direcciones `10.0.0.0/16` y la subnet `default` con rango `10.0.0.0/24`.

![Crear VNet — Espacio de direcciones](./capturas/04-crear-vnet-espacio.png)

Resumen final de validación antes del despliegue, con Bastion y Firewall deshabilitados.

![Crear VNet — Revisar y crear](./capturas/05-crear-vnet-revisar.png)

Confirmación de que la implementación se completó correctamente.

![Implementación completada](./capturas/06-implementacion-completada.png)

---

### 3. Validación de la VNet

Overview del recurso ya creado, mostrando el espacio de direcciones, número de subredes y servidores DNS.

![Overview de la VNet](./capturas/07-vnet-overview.png)

Vista detallada del espacio de direcciones de la VNet.

![Espacio de direcciones de la VNet](./capturas/08-vnet-espacio.png)

---

### 4. Creación de subred adicional

Formulario para agregar la subred `defaultA` con rango `10.0.1.0/24`, marcada como subred privada.

![Agregar subred defaultA](./capturas/09-agregar-subred.png)

Lista de subredes de la VNet, ahora con `default` y `defaultA`.

![Lista de subredes](./capturas/10-lista-subredes.png)

---

### 5. Creación del Network Security Group

Búsqueda del servicio "Grupo de seguridad de red" desde el portal.

![Buscar NSG](./capturas/11-buscar-nsg.png)

Asistente de creación del NSG llamado `NGS1`, en el resource group `demo_redes` y región Spain Central.

![Crear NSG — Datos básicos](./capturas/12-crear-nsg-basicos.png)

Confirmación de que la implementación del NSG está en curso.

![NSG implementándose](./capturas/13-nsg-implementacion.png)

---

### 6. Asociación del NSG a las subredes

Vista del blade "Subredes" del NSG recién creado, sin asociaciones todavía.

![NGS1 — Subredes sin asociar](./capturas/14-nsg-subred-menu.png)

Formulario para asociar el NSG a la subred `default` de la VNet.

![Asociar subred al NSG](./capturas/15-asociar-subred.png)

Listado de subredes ya asociadas al NSG: `default` y `defaultA`.

![NSG con subredes asociadas](./capturas/16-nsg-subredes-asociadas.png)

---

### 7. Regla de seguridad SSH

Vista del menú lateral del NSG con las opciones "Reglas de seguridad de entrada" y "Reglas de seguridad de salida".

![Menú de reglas del NSG](./capturas/17-nsg-menu-reglas.png)

Formulario para crear la regla de entrada: origen `10.0.0.0/24`, servicio SSH, puerto destino 22, protocolo TCP, acción Permitir, prioridad 100.

![Regla SSH — Formulario](./capturas/18-regla-ssh-formulario.png)

Regla `Allow-SSH-Subnet-Only` creada y visible en la lista de reglas de entrada.

![Regla SSH creada](./capturas/19-regla-ssh-creada.png)

---

## Conclusiones

- Las **VNet son gratuitas** en Azure; solo los recursos asociados (Bastion, VPN Gateway) tienen coste.
- El espacio de direcciones y las subredes deben planificarse con CIDR que no se superpongan.
- Los **NSG** filtran tráfico a nivel de subred o NIC y se evalúan por orden de prioridad.
- La regla creada permite SSH solo desde la subred interna `10.0.0.0/24`, lo que reduce la superficie de ataque desde Internet.
- **VNet Peering** conecta VNets de forma privada y rápida, pero requiere peering explícito entre cada par (no es transitivo).

