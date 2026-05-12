# **Semilla — Plataforma de Donaciones Alimentarias**

## Descripción del proyecto

Este proyecto consiste en el desarrollo de una plataforma web enfocada en la gestión de donaciones alimentarias para ser un "puente" entre las empresas o restaurantes que decidan donar y entre las fundaciones que soliciten las donaciones.  
La aplicación busca reducir el desperdicio de alimentos permitiendo que establecimientos publiquen productos o comidas disponibles para donar, mientras que las fundaciones pueden visualizar y solicitar dichas donaciones para posteriormente recogerlas.

El sistema está planteado inicialmente como un MVP (Minimum Viable Product), priorizando funcionalidades esenciales, facilidad de uso, buena experiencia visual y una arquitectura sencilla pero escalable.

  
## Objetivo principal

Facilitar la conexión entre donadores y fundaciones mediante una plataforma centralizada, moderna y accesible.


## Tecnologías utilizadas

| Área | Tecnologías |
|-----------|-------------|
| **Frontend** | HTML5, CSS3, TypeScript, React, Vite, TailwindCSS |
| **Backend** | Node.js, NestJS, TypeScript |
| **Base de datos** | PostgreSQL, Prisma ORM |
| **Seguridad** | JWT Authentication, bcrypt |
| **Infraestructura** | Docker, Docker Compose, AWS EC2 |


## Funcionalidades principales del MVP

### Empresas / Restaurantes

* Registro e inicio de sesión
* Publicar donaciones
* Adjuntar imágenes
* Definir ubicación y cantidad disponible
* Gestionar estado de las donaciones

### Fundaciones

* Registro e inicio de sesión
* Visualización de donaciones disponibles
* Solicitud de donaciones
* Contacto con el donador


## Arquitectura general

El sistema utiliza una arquitectura cliente-servidor compuesta por:

```text
Frontend (React)
       ↓
Backend API REST (NestJS)
       ↓
Base de datos PostgreSQL
```

---

# **ADRs — Architectural Decision Records**

## ADR 001 — Arquitectura Cliente-Servidor

### **Estado:**
Aceptado  

### **Contexto:** 
El proyecto requiere separar claramente la interfaz visual, la lógica de negocio y el almacenamiento de datos. 

### **Decisión:** 
Se decidió implementar una arquitectura cliente-servidor compuesta por un frontend independiente en React y un backend API REST desarrollado con NestJS.
 
### **Justificación:**
Esta arquitectura permite:
* Separar responsabilidades
* Facilitar mantenimiento
* Escalar componentes individualmente
* Permitir futuras aplicaciones móviles consumiendo la misma API

Además, es una arquitectura ampliamente utilizada en aplicaciones web modernas.

---

## ADR 002 — Uso de React para el Frontend

### **Estado:**
Aceptado

### **Contexto:**
Era necesario seleccionar una tecnología frontend moderna que permitiera construir interfaces dinámicas y reutilizables.

### **Decisión:**
Se decidió utilizar React junto con TypeScript.

### **Justificación:**
React facilita:

* Creación de componentes reutilizables
* Navegación dinámica
* Mejor experiencia de usuario
* Escalabilidad del frontend

TypeScript aporta:

* Tipado estático
* Menor cantidad de errores
* Mejor mantenimiento del código

La combinación es ampliamente utilizada en entornos profesionales y educativos.

---

## ADR 003 — Implementación de Vite

### **Estado:**
Aceptado

### **Contexto:**
El proyecto requería una herramienta ligera y rápida para el entorno de desarrollo frontend.

### **Decisión:**
Se decidió utilizar Vite como herramienta de construcción y ejecución del frontend.

### **Justificación:**
Vite ofrece:

* Inicio rápido del servidor local
* Compilación optimizada
* Configuración sencilla
* Excelente integración con React y TypeScript

Esto mejora la experiencia de desarrollo y reduce tiempos de compilación.

---

## ADR 004 — Uso de Node.js y NestJS en el Backend

### **Estado:**
Aceptado

### **Contexto:**
El backend debía ser escalable, organizado y mantener una arquitectura clara que facilitara el crecimiento del proyecto a futuro.

### **Decisión:**
Se decidió utilizar Node.js junto con NestJS como framework principal para el desarrollo del backend.

### **Justificación:**
NestJS proporciona:

* Arquitectura modular y escalable
* Integración nativa con TypeScript
* Mejor organización del código
* Separación clara de responsabilidades
* Facilidad para implementar buenas prácticas
* Compatibilidad con APIs REST modernas

Aunque inicialmente se contempló Express.js por su simplicidad, se optó por NestJS debido a que el proyecto puede crecer progresivamente y requerir una estructura más mantenible a largo plazo.

Además, NestJS utiliza internamente Express, por lo que mantiene el ecosistema de Node.js mientras añade una arquitectura más robusta y organizada.

---

## ADR 005 — Uso de PostgreSQL como Base de Datos

### **Estado:**
Aceptado

### **Contexto:**
El sistema requiere manejar relaciones entre usuarios, donaciones y solicitudes.

### **Decisión:**
Se decidió utilizar PostgreSQL como sistema gestor de base de datos relacional.

### **Justificación:**
PostgreSQL ofrece:

* Seguridad
* Estabilidad
* Buen manejo de relaciones
* Escalabilidad
* Compatibilidad con Prisma ORM

Además, es software libre y ampliamente utilizado en entornos profesionales.

---

## ADR 006 — Uso de Prisma ORM

### **Estado:**
Aceptado

### **Contexto:**
Era necesario simplificar la interacción entre el backend y la base de datos.

### **Decisión:**
Se decidió implementar Prisma ORM.

### **Justificación:**
Prisma permite:

* Consultas más legibles
* Tipado automático con TypeScript
* Reducción de errores
* Mejor mantenimiento del código
* Gestión sencilla de migraciones

También mejora la productividad del equipo durante el desarrollo.

---

## ADR 007 — Autenticación y Seguridad

### **Estado:**
Aceptado

### **Contexto:**
El sistema requiere autenticación segura y control de acceso por roles.

### **Decisión:**
Se decidió utilizar JWT para autenticación y bcrypt para cifrado de contraseñas.

### **Justificación:**
#### JWT permite:

* Manejo de sesiones sin estado
* Autenticación mediante tokens
* Escalabilidad
* Fácil integración frontend-backend

#### bcrypt permite:

* Cifrar contraseñas de forma segura
* Evitar almacenamiento de contraseñas en texto plano
* Mejorar la seguridad general de la aplicación

---

## ADR 008 — Roles de Usuario

### **Estado:**
Aceptado

### **Contexto:**
La plataforma requiere distintos tipos de usuarios con funcionalidades diferentes.

### **Decisión:**
Se implementarán dos roles principales:

* Empresa/Restaurante
* Fundación

### **Justificación:**
#### Empresa/Restaurante

Puede:

* Publicar donaciones
* Gestionar disponibilidad
* Administrar publicaciones

#### Fundación

Puede:

* Visualizar donaciones
* Solicitar alimentos
* Coordinar recolección

La separación por roles mejora:

* Organización del sistema
* Seguridad
* Experiencia de usuario

---

## ADR 009 — Dockerización del Proyecto

### **Estado:**
Aceptado

### **Contexto:**
El despliegue debía ser consistente y fácil de replicar entre distintos entornos.

### **Decisión:**
Se decidió utilizar Docker y Docker Compose.

### **Justificación:**
Docker permite:

* Portabilidad
* Consistencia entre entornos
* Fácil despliegue
* Separación de servicios

Docker Compose facilita la ejecución conjunta de:

* Frontend
* Backend
* Base de datos

mediante un solo comando.

---

## ADR 010 — Despliegue en AWS EC2

### **Estado:**
Aceptado

### **Contexto:**
El proyecto necesita un despliegue funcional en la nube con bajo costo operativo.

### **Decisión:**

Se decidió utilizar AWS EC2 como infraestructura principal.

### **Justificación:**
AWS EC2 ofrece:

* Bajo costo utilizando Free Tier
* Flexibilidad
* Fácil administración
* Compatibilidad con Docker

Se descartaron servicios más complejos debido a que el proyecto corresponde a un MVP académico y no requiere arquitectura distribuida.

---

# **Estructura inicial del proyecto**

```text
/frontend
/backend
/docker
README.md
docker-compose.yml
```

---

## Posibles mejoras futuras:
* Sistema de notificaciones
* Geolocalización avanzada
* Chat interno
* Panel administrativo
* Historial de donaciones
* Aplicación móvil
* Métricas y estadísticas

---

## Integrantes:
* Juan Camilo Cruz Pardo
* Daniel Steven Fontalvo Matiz

---

## Estado actual del proyecto:
En desarrollo — MVP inicial.
