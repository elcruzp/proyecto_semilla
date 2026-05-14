# **Historias de Usuario — Semilla**

## HU: Empresas / Restaurantes

### **HU-01 — Registro de empresa**

**Como** empresa o restaurante,
**quiero** registrarme en la plataforma,
**para** poder publicar donaciones de alimentos disponibles.

#### Criterios de aceptación
* El usuario debe poder ingresar:
  - correo
  - contraseña
  - nombre de la empresa
  - dirección
  - teléfono
* El sistema debe validar que el correo no exista previamente.
* La contraseña debe almacenarse cifrada.
* El usuario debe quedar registrado con el rol DONOR.

---

### **HU-02 — Inicio de sesión**

**Como** empresa o restaurante,
**quiero** iniciar sesión en la plataforma,
**para** acceder a mis publicaciones y gestionar donaciones.

#### Criterios de aceptación
* El usuario debe ingresar correo y contraseña.
* El sistema debe validar las credenciales.
* El sistema debe generar un token de autenticación JWT.
* El usuario debe acceder a su panel principal.

---

### **HU-03 — Publicar donación**

**Como** empresa o restaurante,
**quiero** publicar una donación de alimentos,
**para** que las fundaciones puedan visualizarla y solicitarla.


#### Criterios de aceptación
* La publicación debe permitir:
  * descripción
  * tipo de alimento
  * cantidad
  * fecha de vencimiento
  * dirección
  * imagen
* La donación debe registrarse con estado ACTIVA.
* La publicación debe quedar asociada al usuario autenticado.

---

### **HU-04 — Gestionar solicitudes**

**Como** empresa o restaurante,
**quiero** visualizar y responder solicitudes de donación,
**para** decidir qué fundación recibirá los alimentos.

#### Criterios de aceptación
* El sistema debe mostrar las solicitudes recibidas.
* El usuario debe poder:

  * aceptar solicitudes
  * rechazar solicitudes
* Al aceptar una solicitud:

  * la solicitud cambia a ACEPTADA
  * la donación cambia a SOLICITADA

---

## Fundaciones

### **HU-05 — Registro de fundación**

**Como** fundación,
**quiero** registrarme en la plataforma,
**para** poder solicitar donaciones disponibles.

#### Criterios de aceptación
* El usuario debe ingresar:

  * correo
  * contraseña
  * nombre de la fundación
  * dirección
  * teléfono
* El sistema debe validar correos duplicados.
* La contraseña debe almacenarse cifrada.
* El usuario debe registrarse con rol FOUNDATION.

---

### **HU-06 — Visualizar donaciones**

**Como** fundación,
**quiero** visualizar las donaciones disponibles,
**para** identificar alimentos que puedan beneficiar a mi comunidad.

#### Criterios de aceptación
* El sistema debe listar únicamente donaciones ACTIVAS.
* Cada publicación debe mostrar:

  * descripción
  * cantidad
  * dirección
  * fecha de vencimiento
  * imagen
* La información debe visualizarse de forma clara y organizada.

---

### **HU-07 — Solicitar donación**

**Como** fundación,
**quiero** solicitar una donación disponible,
**para** coordinar la recolección de alimentos.

#### Criterios de aceptación
* La fundación debe poder enviar solicitudes sobre donaciones ACTIVAS.
* La solicitud debe quedar asociada:

  * a la fundación
  * a la donación
* La solicitud debe registrarse con estado PENDIENTE.

---

### **HU-08 — Gestionar perfil**

#### Historia de usuario

**Como** usuario de la plataforma,
**quiero** editar mi información de perfil,
**para** mantener actualizados mis datos de contacto.

### Criterios de aceptación
* El usuario debe poder editar:

  * nombre
  * dirección
  * teléfono
* El sistema debe guardar los cambios correctamente.
* Solo el usuario autenticado puede modificar su perfil.
