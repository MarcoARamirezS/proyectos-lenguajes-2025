# 🛠️ Plataforma de Gestión de Taller Mecánico (AutoFix Manager)

Control de vehículos, clientes, servicios y órdenes de trabajo

## 📝 Descripción General

AutoFix Manager permite administrar un taller mecánico:

- Clientes  
- Vehículos  
- Servicios (cambios de aceite, frenos, afinación, etc.)  
- Órdenes de trabajo  
- Costos y estatus  

## 🎯 Objetivos

- Controlar trabajos asignados a vehículos.
- Dar seguimiento a servicios desde “recibido” hasta “entregado”.
- Organizar mecánicos y asignaciones.

## 📦 Alcance

### ✔ Incluye

- CRUD clientes  
- CRUD vehículos  
- Servicios  
- Órdenes de trabajo  
- Manejo de estatus  
- Historial de trabajos  
- JWT + roles (admin, mecánico, recepción)

### ❌ No incluye

- Facturación automática  
- Compras o inventarios de refacciones  

## 🧩 Módulos

- Clientes  
- Vehículos  
- Servicios  
- Órdenes de trabajo  
- Asignación de mecánicos  
- Pagos  
- Dashboard  

## 👤 Historias de Usuario

- “Como mecánico quiero ver las órdenes asignadas para trabajar en ellas.”  
- “Como recepcionista quiero registrar el vehículo de un cliente para comenzar una orden.”

## 📁 Estructura Backend — AutoFix Manage

```plaintext
autofix-backend/
├── src/
│   ├── config/
│   │   ├── env.ts                 # Variables de entorno
│   │   └── db.ts                  # Conexión a PostgreSQL
│   ├── models/
│   │   ├── client.model.ts        # Modelo Cliente
│   │   ├── vehicle.model.ts       # Modelo Vehículo
│   │   ├── service.model.ts       # Modelo Servicio
│   │   ├── workorder.model.ts     # Modelo Orden de Trabajo
│   │   └── applied_service.model.ts # Servicios aplicados a una orden
│   ├── repositories/
│   │   ├── client.repository.ts
│   │   ├── vehicle.repository.ts
│   │   ├── service.repository.ts
│   │   ├── workorder.repository.ts
│   │   └── applied_service.repository.ts
│   ├── services/
│   │   ├── client.service.ts
│   │   ├── vehicle.service.ts
│   │   ├── service.service.ts
│   │   ├── workorder.service.ts
│   │   └── mechanic.service.ts     # Asignación de mecánicos
│   ├── controllers/
│   │   ├── client.controller.ts
│   │   ├── vehicle.controller.ts
│   │   ├── service.controller.ts
│   │   ├── workorder.controller.ts
│   │   └── auth.controller.ts
│   ├── routes/
│   │   ├── client.routes.ts
│   │   ├── vehicle.routes.ts
│   │   ├── service.routes.ts
│   │   ├── workorder.routes.ts
│   │   └── auth.routes.ts
│   ├── middleware/
│   │   ├── auth.middleware.ts
│   │   └── role.middleware.ts
│   ├── utils/
│   │   ├── jwt.ts
│   │   └── errorHandler.ts
│   ├── app.ts
│   └── server.ts
├── prisma/                        # Si usas Prisma ORM
├── .env.example
└── README.md
```

## 📁 Estructura Frontend — AutoFix Manager

```plaintext
autofix-frontend/
├── src/
│   ├── api/
│   │   ├── http.ts                # Axios config
│   │   ├── auth.api.ts
│   │   ├── clients.api.ts
│   │   ├── vehicles.api.ts
│   │   ├── services.api.ts
│   │   └── workorders.api.ts
│   ├── store/
│   │   ├── auth.store.ts
│   │   ├── clients.store.ts
│   │   ├── vehicles.store.ts
│   │   ├── services.store.ts
│   │   └── workorders.store.ts
│   ├── router/
│   │   └── index.ts
│   ├── pages/
│   │   ├── LoginPage.vue
│   │   ├── DashboardPage.vue
│   │   ├── ClientsPage.vue
│   │   ├── VehiclesPage.vue
│   │   ├── ServicesPage.vue
│   │   ├── WorkOrdersPage.vue
│   │   └── WorkOrderDetailPage.vue
│   ├── components/
│   │   ├── clients/
│   │   │   └── ClientForm.vue
│   │   ├── vehicles/
│   │   │   └── VehicleForm.vue
│   │   ├── services/
│   │   │   └── ServiceForm.vue
│   │   ├── workorders/
│   │   │   ├── WorkOrderCard.vue
│   │   │   └── AppliedServiceForm.vue
│   │   └── ui/
│   │       ├── Button.vue
│   │       └── Modal.vue
│   ├── App.vue
│   └── main.ts
└── .env.example
```

## 🗄 Modelo ER

Cliente → Vehículo → OrdenTrabajo → ServiciosAplicados

## 🔧 Tecnologías sugeridas

**Backend:** Node.js + TypeScript + PostgreSQL  
**Frontend:** Vue 3 + Tailwind  

# 📄 Entregables Finales — AutoFix Manager

## ✅ 1. Backend Completo (Node.js + TypeScript + PostgreSQL)

Debe incluir:

- API REST modularizada  
- Arquitectura por capas:  
  **Routes → Controllers → Services → Repositories → DB**  
- Autenticación y autorización con JWT  
- Manejo de roles: **admin, mecánico, recepción**  
- Validaciones con Zod u otra librería  
- Seguridad básica (CORS, Helmet opcional, sanitización)  
- Archivo `.env.example`  
- Scripts de inicio y documentación de instalación  
- Migraciones SQL (Prisma o manuales)

📦 **Módulos obligatorios del backend:**

- CRUD clientes  
- CRUD vehículos  
- CRUD servicios  
- CRUD órdenes de trabajo  
- Servicios aplicados  
- Asignación de mecánicos  
- Cambio de estatus (recibido → proceso → finalizado → entregado)  
- Dashboard con estadísticas básicas  


---

## 🎨 2. Frontend Completo (Vue 3 + TailwindCSS)

SPA funcional conectada al backend.

Debe incluir:

- Manejo de sesión (login, logout)  
- Guards de rutas protegidas  
- Consumo de todas las APIs  
- Dashboard profesional  
- Módulos completos:
  - Clientes  
  - Vehículos  
  - Servicios  
  - Órdenes de trabajo  
  - Asignación de mecánicos  
- Interfaz moderna y responsive con TailwindCSS  

📌 **Requisitos del frontend:**

- Componentes UI reutilizables  
- Loaders, notificaciones, alerts  
- Validaciones visuales  


---

## 🗄 3. Base de Datos (SQL)

Archivo requerido: `database_schema.sql`

Debe incluir:

- Tablas:  
  - clients  
  - vehicles  
  - services  
  - work_orders  
  - applied_services  
  - users (roles incluidos)  
  - mechanics (opcional según diseño)  
- Llaves foráneas y relaciones  
- Índices sugeridos  
- Archivo opcional de seeds  


---

## 📊 4. Dashboard Profesional

Debe mostrar:

- Órdenes activas  
- Vehículos actualmente en taller  
- Servicios más solicitados  
- Ingresos simples  
- Estatus del taller (donut, barras o cards)  


---

## 🎥 5. Video Demostrativo (3–7 min)

El video debe mostrar:

1. Login y roles  
2. Registro de cliente  
3. Registro de vehículo  
4. Creación de orden de trabajo  
5. Asignación de servicios y mecánico  
6. Avance de estatus  
7. Dashboard  
8. Rutas protegidas funcionando  

Formato: **YouTube (oculto), Google Drive o MP4**  


---

## 🧪 6. Colección Postman Completa

Archivo requerido: `postman_collection.json`

Debe incluir carpetas:

- Auth (login)  
- Clientes (CRUD)  
- Vehículos (CRUD)  
- Servicios (CRUD)  
- Órdenes de trabajo (CRUD)  
- Servicios aplicados  
- Rutas protegidas por token  

Cada endpoint debe tener ejemplos de:

- Request  
- Response  
- Headers con JWT  


---

## 📐 7. Diagramas Requeridos

Todos en formato PNG o Mermaid:

- Diagrama Entidad–Relación (ER)
- Arquitectura del backend  
- Arquitectura del frontend  
- Flujo JWT  
- Flujo completo de una orden de trabajo  


---

## 🎨 10. Diseño UI (Opcional pero recomendado)

**Prototipo sugerido en Figma:**  
https://www.figma.com/community/file/1182900041400460320

→ [HOME](./../README.md)