# 🏨 Sistema de Gestión de Hotel — **HotelMaster**

Administración de reservaciones, habitaciones, huéspedes y pagos.

---

## 📝 Descripción General

**HotelMaster** es un sistema completo para la gestión de un hotel pequeño o mediano.  
Permite controlar:

- Habitaciones y su estatus (libre, ocupada, mantenimiento)
- Reservaciones
- Registro de huéspedes
- Check-in / Check-out
- Cargos adicionales
- Pagos y facturación simple

El objetivo principal es digitalizar el flujo operativo diario del hotel, evitar errores y mejorar la eficiencia del personal.

---

## 🎯 Objetivos del Sistema

- Facilitar la administración diaria del hotel.
- Evitar sobre-reservaciones.
- Control total de huéspedes y habitaciones.
- Agilizar el proceso de check-in / check-out.
- Registrar pagos, cargos adicionales y estados de cuenta.
- Brindar una experiencia más organizada al personal.

---

## 📦 Alcance del Proyecto

### ✔ Incluye
- CRUD de **habitaciones**
- CRUD de **huéspedes**
- **Reservaciones** con validaciones
- **Check-in / Check-out**
- **Cargos extras** por estancia
- **Pagos**
- **Dashboard** de operación
- **Autenticación con JWT**
- Roles: **admin**, **recepcionista**

### ❌ No incluye (opcional)
- Múltiples hoteles / sucursales
- Integración con pasarelas de pago (Stripe, PayPal)
- Facturación avanzada

---

## 🧩 Módulos del Sistema

### 1. Habitaciones
- Tipos de habitación
- Estado actual: libre / ocupada / mantenimiento

### 2. Huéspedes
- Registro y administración de clientes

### 3. Reservaciones
- Fechas de entrada/salida
- Validación de disponibilidad
- Asignación de habitación

### 4. Check-in / Check-out
- Confirmación de entrada
- Cierre de estancia y cargos finales

### 5. Pagos
- Métodos simples (efectivo, tarjeta, transferencia)
- Estado de cuenta de cada huésped

### 6. Cargos Extras
- Servicios consumidos
- Tarifas adicionales

### 7. Dashboard
- Ocupación del hotel
- Habitaciones disponibles
- Reservas del día
- Ingresos estimados

### 8. Autenticación y Roles
- Login con JWT  
- Roles: Admin / Recepcionista

---

## 👤 Historias de Usuario

### Recepcionista
> “Como recepcionista quiero registrar huéspedes para completar su reservación.”

### Administrador
> “Como administrador quiero revisar la disponibilidad de habitaciones fácilmente.”

> “Como administrador quiero ver las reservas del día para planear la operación.”

---

## 🗄 Modelo ER (Entidad–Relación)

Diagrama conceptual:

```
Habitaciones → Reservaciones → Huéspedes → Pagos
```


Relaciones sugeridas:

- Una **habitación** puede tener muchas **reservaciones**.
- Un **huésped** puede tener muchas **reservaciones**.
- Una **reservación** puede tener varios **pagos** y cargos extras.

---

## 🔧 Tecnologías Sugeridas

### Backend
- **Python FastAPI**
- **MySQL**
- SQLAlchemy
- JWT
- Pydantic

### Frontend
- **Angular**
- **Material UI**
- Angular Router
- HttpClient

## 🗂️ Estructura del Backend — HotelMaster (FastAPI + MySQL)

```plaintext
hotel-backend/
├── app/
│   ├── core/
│   │   ├── config.py              # Configuración general y variables de entorno
│   │   └── security.py            # Funciones JWT, autenticación y hashing
│
│   ├── db/
│   │   ├── session.py             # Conexión a MySQL con SQLAlchemy
│   │   └── base.py                # Import centralizado de modelos
│
│   ├── models/
│   │   ├── room.py                # Modelo Habitaciones
│   │   ├── guest.py               # Modelo Huéspedes
│   │   ├── reservation.py         # Modelo Reservaciones
│   │   ├── payment.py             # Modelo Pagos
│   │   └── charge.py              # Modelo Cargos Extras
│
│   ├── schemas/
│   │   ├── room.py                # Pydantic schemas - Habitaciones
│   │   ├── guest.py               # Pydantic schemas - Huéspedes
│   │   ├── reservation.py         # Pydantic schemas - Reservaciones
│   │   ├── payment.py             # Pydantic schemas - Pagos
│   │   └── charge.py              # Pydantic schemas - Cargos Extra
│
│   ├── crud/
│   │   ├── crud_room.py           # Operaciones CRUD para habitaciones
│   │   ├── crud_guest.py          # CRUD para huéspedes
│   │   ├── crud_reservation.py    # CRUD para reservaciones
│   │   ├── crud_payment.py        # CRUD para pagos
│   │   └── crud_charge.py         # CRUD para cargos adicionales
│
│   ├── api/
│   │   └── v1/
│   │       ├── auth.py            # Rutas de autenticación (JWT)
│   │       ├── rooms.py           # Rutas Habitaciones
│   │       ├── guests.py          # Rutas Huéspedes
│   │       ├── reservations.py    # Rutas Reservaciones
│   │       ├── payments.py        # Rutas Pagos
│   │       └── charges.py         # Rutas Cargos Extras
│
│   ├── services/
│   │   ├── reservation_service.py # Lógica de negocio: check-in / check-out
│   │   └── dashboard_service.py   # Servicios para estadísticas del dashboard
│
│   ├── utils/
│   │   ├── jwt_helper.py          # Funciones para generar y validar tokens JWT
│   │   └── responses.py           # Respuestas estándar (éxito / error)
│
│   ├── main.py                    # Punto de entrada FastAPI
│   └── __init__.py
│
├── alembic/                       # Migraciones (si se usa Alembic)
├── .env.example                   # Plantilla de variables de entorno
├── requirements.txt               # Dependencias del backend
└── README.md                      # Documentación del backend
```

## 🖥️ Estructura del Frontend — HotelMaster (Angular + Material)

```plaintext
hotel-frontend/
└── src/app/
    ├── core/
    │   ├── guards/
    │   │   └── auth.guard.ts              # Bloquea rutas sin token
    │   ├── interceptors/
    │   │   └── token.interceptor.ts       # Agrega JWT a cada petición HTTP
    │   └── services/
    │       ├── auth.service.ts            # Login, logout y sesión
    │       ├── rooms.service.ts           # API de habitaciones
    │       ├── guests.service.ts          # API de huéspedes
    │       ├── reservations.service.ts    # API de reservaciones
    │       ├── payments.service.ts        # API de pagos
    │       └── charges.service.ts         # API de cargos extras

    ├── pages/
    │   ├── login/
    │   │   └── login.component.ts
    │   ├── dashboard/
    │   │   └── dashboard.component.ts
    │   ├── rooms/
    │   │   └── rooms.component.ts
    │   ├── guests/
    │   │   └── guests.component.ts
    │   ├── reservations/
    │   │   ├── reservation-list.component.ts
    │   │   └── reservation-form.component.ts
    │   ├── checkin/
    │   │   └── checkin.component.ts
    │   ├── checkout/
    │   │   └── checkout.component.ts
    │   ├── payments/
    │   │   └── payments.component.ts
    │   └── charges/
    │       └── charges.component.ts

    ├── shared/
    │   ├── layout/
    │   │   ├── sidebar/
    │   │   │   └── sidebar.component.ts
    │   │   └── navbar/
    │   │       └── navbar.component.ts
    │   └── components/
    │       ├── card/
    │       ├── table/
    │       ├── modal/
    │       └── ui/

    ├── app-routing.module.ts              # Rutas principales del sistema
    ├── app.component.ts                    # Componente raíz
    └── app.module.ts                       # Módulo principal Angular

└── main.ts                                 # Punto de entrada de la aplicación
```

## 📄 Modelo ER Sugerido
```plaintext
erDiagram

    ROOM ||--|{ RESERVATION : "incluida_en"
    GUEST ||--|{ RESERVATION : "realiza"
    RESERVATION ||--|{ PAYMENT : "tiene"
    RESERVATION ||--|{ CHARGE : "genera"

    ROOM {
        int id
        string number
        string type
        string status
        float price
    }

    GUEST {
        int id
        string name
        string phone
        string email
    }

    RESERVATION {
        int id
        int roomId
        int guestId
        datetime checkinDate
        datetime checkoutDate
        string status
    }

    PAYMENT {
        int id
        int reservationId
        float amount
        datetime date
        string method
    }

    CHARGE {
        int id
        int reservationId
        string description
        float amount
    }
```

## 📄 Entregables Finales

### ✔ Backend completo
- API REST funcional  
- Controladores, modelos y rutas  
- Autenticación con JWT  
- Validaciones  
- Scripts SQL

### ✔ Frontend SPA (Angular)
- Páginas protegidas  
- Dashboard  
- Gestión visual de habitaciones y reservaciones  

### ✔ Base de Datos SQL
- Tablas para habitaciones, huéspedes, reservaciones, pagos, cargos extras

### ✔ Documentación
- Manual técnico  
- Manual de usuario  
- Instructivo de instalación  

### ✔ Colección Postman
- Endpoints de autenticación  
- CRUD completos  
- Reservaciones y check-in/check-out  

### ✔ Video Demostrativo
- Funcionamiento general del sistema  
- Duración sugerida: **3–6 minutos**  

---

→ [HOME](./../README.md)