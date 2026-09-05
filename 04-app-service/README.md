# 04. App Service

Este módulo documenta la creación y despliegue de una **Azure Web App** en tier gratuito (Free F1) con Python 3.14 sobre Linux, como ejemplo de servicio PaaS para hospedar aplicaciones web sin gestionar infraestructura.

## Recursos desplegados

| Recurso | Tipo | Tier | Runtime | Coste |
|---|---|---|---|---|
| `demodeby-ezos89bk8plofu0` | Web App | Free F1 | Python 3.14 | 0 € |
| `ASP-demoappservice-9852` | App Service Plan | Free | Linux | 0 € |

**URL pública:** `https://demodeby-ezos89bk8plofu0.spancentral-01.azurewebsites.net`
**Región:** Spain Central
**Resource Group:** `demo_app_service`

---

## Pasos realizados

### 1. Arquitectura típica de Web App

Diagrama de referencia de la arquitectura de 3 niveles (balanceador, zonas de disponibilidad, Redis, SQL).

![Arquitectura típica de Web App de 3 niveles](./Imagenes/01-arquitectura-3-niveles.png)

### 2. Creación del Web App — Datos básicos

Asistente de creación con suscripción, grupo de recursos, nombre único global, runtime Python 3.14, sistema Linux y región Spain Central.

![Crear aplicación web — Datos básicos](./imagenes/02-crear-basicos.png)

### 3. Revisión y creación

Resumen final de validación antes del despliegue, con SKU Gratis y plan de App Service recién creado.

![Revisar y crear Web App](./imagenes/03-revisar-crear.png)

### 4. Implementación en curso

Notificación de Azure durante el despliegue de la aplicación web.

![Implementación en curso](./imagenes/04-implementacion.png)

### 5. Web App creada

Vista de la lista de App Services con la aplicación desplegada, mostrando su nombre y URL pública.

![App Services con Web App creada](./imagenes/05-app-creada.png)

### 6. Smoke test en el navegador

Acceso a la URL pública confirmando que la aplicación responde con la página por defecto de Azure.

![App funcionando en el navegador](./imagenes/06-app-funcionando-navegador.png)

---

## Conclusiones

- El tier **Free F1** permite practicar sin consumir créditos de Azure.
- El nombre de la Web App debe ser **globalmente único** dentro de azurewebsites.net.
- El plan y la Web App están acoplados por región y resource group.
- La página por defecto valida el despliegue antes de subir código propio.


