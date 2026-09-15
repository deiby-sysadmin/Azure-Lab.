# 08. Microsoft Entra ID — Creación de usuarios

Este módulo documenta la creación de usuarios en **Microsoft Entra ID**, la asignación del rol de **Administrador global** y la validación del primer inicio de sesión con cambio de contraseña y registro de Microsoft Authenticator.

---

## Recursos creados

| Usuario | UPN | Rol | Departamento |
|---|---|---|---|
| `deiby pineda` | `deibypineda24gmail.onmicrosoft.com` | Administrador global | — |
| `Usuario Lab 01` | `usuario.lab01@deibypineda24gmail.onmicrosoft.com` | Administrador global | IT |
| `Test User` | `Test@deibypineda24gmail.onmicrosoft.com` | Miembro | — |

**Tenant:** deibypineda24gmail.onmicrosoft.com

---

## Concepto: Características de Microsoft Entra ID

Diapositiva introductoria que resume las 4 características principales de Entra ID: gestión de identidades y acceso (SSO, MFA), integración de aplicaciones, plataforma para desarrolladores y seguridad avanzada (Entra ID Protection).

![Características de Microsoft Entra ID](./capturas/18-teoria-entra-id.png)

---

## Pasos realizados

### 1. Acceso al servicio

Vista del menú lateral de **Microsoft Entra** en el Centro de administración, con el botón "Nuevo usuario" desplegado mostrando las opciones "Crear un usuario nuevo" e "Invitar usuario externo".

![Menú de usuarios](./capturas/01-menu-usuarios-nuevo.png)

Overview del Centro de administración de Microsoft Entra con el directorio predeterminado, métricas (1 usuario, 0 grupos) y la guía de implementación.

![Overview de Microsoft Entra ID](./capturas/02-overview-entra-id.png)

---

### 2. Creación del primer usuario (`Usuario Lab 01`)

Formulario de creación en la pestaña **Datos básicos** con el nombre principal `usuario.lab01@deibypineda24gmail.onmicrosoft.com` y nombre para mostrar `Usuario Lab 01`.

![Crear usuario — Datos básicos](./capturas/03-crear-usuario-basicos.png)

Pestaña **Propiedades** rellenada con Puesto `IT Support L2` y Departamento `IT`.

![Crear usuario — Propiedades](./capturas/04-crear-usuario-propiedades.png)

Pestaña **Tareas** con la asignación de roles del directorio (panel de **Administrador global**).

![Crear usuario — Tareas y roles](./capturas/05-crear-usuario-roles.png)

Pestaña **Revisar y crear** con el resumen completo: UPN, nombre para mostrar, propiedades y rol asignado.

![Revisar y crear usuario](./capturas/06-revisar-crear-usuario.png)

Lista de usuarios del directorio mostrando los dos usuarios existentes.

![Lista de usuarios](./capturas/07-usuarios-lista.png)

Perfil detallado del usuario recién creado, con su Id. de objeto, fecha de creación, pertenencia a grupos y rol asignado.

![Perfil del usuario](./capturas/08-perfil-usuario.png)

---

### 3. Validación del primer inicio de sesión

Para comprobar que el usuario estaba activo, se cerró la sesión del administrador principal y se inició sesión con el nuevo `usuario.lab01@deibypineda24gmail.onmicrosoft.com`.

Pantalla de Microsoft que pide el **nombre principal de usuario** (UPN).

![Iniciar sesión con usuario nuevo](./capturas/09-login-usuario-nuevo.png)

Pantalla para **escribir la contraseña** proporcionada en la creación.

![Escribir contraseña](./capturas/10-login-password.png)

Como era el primer inicio de sesión, el sistema pidió **actualizar la contraseña** por seguridad.

![Actualizar contraseña](./capturas/11-login-cambiar-password.png)

Tras el cambio, se solicitó la instalación de **Microsoft Authenticator** para registrar el segundo factor de autenticación (MFA).

![Instalar Microsoft Authenticator](./capturas/12-login-authenticator.png)

---

### 4. Creación de un segundo usuario desde el nuevo admin

Como el nuevo usuario ya tenía el rol de **Administrador global**, podía acceder a la administración de Entra ID.

Búsqueda del servicio Microsoft Entra ID desde la barra superior del portal (logueado ya como `usuario.lab01`).

![Búsqueda de Microsoft Entra ID](./capturas/13-busqueda-entra.png)

Vista de la lista de usuarios desde la sesión del nuevo administrador global.

![Lista de usuarios desde nuevo admin](./capturas/14-usuarios-lista-nuevo-admin.png)

Formulario de creación del usuario `Test User` con UPN `Test@deibypineda24gmail.onmicrosoft.com`.

![Crear usuario Test User](./capturas/15-crear-usuario-test.png)

Revisar y crear del nuevo usuario Test User.

![Revisar y crear Test User](./capturas/16-revisar-crear-test.png)

Lista final con los 3 usuarios del directorio: el administrador original, Test User y Usuario Lab 01.

![Lista final de usuarios](./capturas/17-usuarios-lista-final.png)

---

## Conclusiones

- En **Microsoft Entra ID** los usuarios internos se crean con UPN del tipo `usuario@dominio.onmicrosoft.com`.
- Asignar el rol de **Administrador global** da control total sobre el tenant, por lo que debe limitarse a cuentas de confianza.
- En el **primer inicio de sesión** el sistema fuerza el cambio de contraseña y, si hay directivas activas, pide registrar **Microsoft Authenticator** (MFA).
- Un usuario con permisos administrativos puede crear nuevos usuarios y administrarlos sin necesidad de la cuenta original.
- El **centro de administración de Microsoft Entra** (`entra.microsoft.com`) ofrece una experiencia simplificada frente al portal Azure clásico para tareas de identidad.

