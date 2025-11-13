# 🎓 Sistema de Gestión Escolar (Mini-SICE)

**Proyecto Fullstack — Backend y Frontend en repos separados**  
**Tecnologías:** FastAPI + Python + MySQL + React + Material UI  
**Equipo máximo:** 4 integrantes

---

## 📌 Descripción General

Este proyecto consiste en un **Sistema de Gestión Escolar**, inspirado en plataformas como **SICE**.  
El sistema permitirá administrar:

- alumnos  
- profesores  
- materias  
- calificaciones  
- reportes académicos

Está dirigido a escuelas pequeñas que actualmente almacenan su información en:

- hojas de cálculo  
- libretas  
- documentos no estandarizados  

Esto provoca errores, pérdida de datos e inconsistencia.  
**El objetivo principal es centralizar y digitalizar la información escolar.**

---

## 🎯 Objetivos del Sistema

- Registrar alumnos, profesores y materias.  
- Capturar y consultar calificaciones.  
- Facilitar la administración escolar.  
- Proveer reportes académicos.  
- Manejar roles de acceso: **Admin** y **Profesor**.

---

## 📦 Alcance del Proyecto

### ✔ Incluye
- CRUD Alumnos  
- CRUD Profesores  
- CRUD Materias  
- Asignación alumno → materia  
- Registro de calificaciones  
- Consulta de boletas y reportes  
- Autenticación JWT  
- Interfaz completa SPA

### ❌ No incluye (opcional)
- Kardex oficial  
- Módulo administrativo (pagos/adeudos)  
- Edición de perfil por alumnos/profesores (solo Admin gestiona)

---

## 🧩 Módulos del Sistema

### 1. Autenticación
- Login  
- JWT  
- Roles: `admin`, `profesor`

### 2. Alumnos (CRUD)
- Datos generales  
- Asignación a materias  

### 3. Profesores (CRUD)
- Información básica  
- Materias impartidas  

### 4. Materias (CRUD)
- Nombre  
- Profesor asignado  

### 5. Calificaciones
- Captura por materia  
- Reporte por alumno  
- Reporte por materia  

### 6. Reportes
- Boleta individual  
- Estadísticas académicas  
- Calificaciones por materia  

### 7. Dashboard
- Total de alumnos  
- Total de profesores  
- Total materias  
- Indicadores rápidos  

---

## 👤 Historias de Usuario

### 🧑‍🏫 Profesor
- "Como profesor quiero capturar calificaciones para actualizar el desempeño del alumno."
- "Como profesor quiero ver la lista de alumnos inscritos en mis materias."

### 🧑‍💼 Administrador
- "Como administrador quiero registrar alumnos para que sean parte del sistema escolar."
- "Como administrador quiero asignar materias a los profesores."
- "Como administrador quiero generar reportes académicos rápidamente."

---

## 🛠 Tecnologías del Proyecto

### 🔙 Backend
- Python  
- FastAPI  
- MySQL  
- SQLAlchemy  
- JWT  
- Pydantic (Schemas)

### 🎨 Frontend
- React  
- Vite  
- Material UI  
- Axios  
- React Router  
- Context API o Zustand

---

## 📁 Estructura del Backend — Mini-SICE (FastAPI)

El backend sigue una arquitectura modular basada en **FastAPI + SQLAlchemy**, organizada por capas:

- **core/** → Configuración, seguridad y settings  
- **db/** → Conexión y base de datos  
- **models/** → Modelos ORM (SQLAlchemy)  
- **schemas/** → Validación y DTOs (Pydantic)  
- **crud/** → Acceso a datos (CRUD)  
- **api/v1/** → Rutas versionadas  
- **main.py** → Punto de entrada

---

```plaintext
school-backend/
├── app/
│   ├── core/
│   │   ├── config.py             # Configuración del proyecto (env, settings)
│   │   └── security.py           # JWT, hashing, autenticación
│   ├── db/
│   │   ├── session.py            # Sesión de SQLAlchemy
│   │   └── base.py               # Declarative Base
│   ├── models/
│   │   ├── student.py            # Modelo Alumno
│   │   ├── teacher.py            # Modelo Profesor
│   │   ├── subject.py            # Modelo Materia
│   │   └── grade.py              # Modelo Calificación
│   ├── schemas/
│   │   ├── student.py            # Schemas Alumno (Pydantic)
│   │   ├── teacher.py            # Schemas Profesor
│   │   ├── subject.py            # Schemas Materia
│   │   └── grade.py              # Schemas Calificación
│   ├── crud/
│   │   ├── crud_student.py       # CRUD Alumno
│   │   ├── crud_teacher.py       # CRUD Profesor
│   │   ├── crud_subject.py       # CRUD Materia
│   │   └── crud_grade.py         # CRUD Calificaciones
│   ├── api/
│   │   └── v1/
│   │       ├── auth.py           # Login, JWT
│   │       ├── students.py       # Endpoints alumnos
│   │       ├── teachers.py       # Endpoints profesores
│   │       ├── subjects.py       # Endpoints materias
│   │       └── grades.py         # Endpoints calificaciones
│   └── main.py                   # Punto de entrada FastAPI
├── .env.example                  # Variables de entorno
└── README.md
```

## 📁 Estructura del Frontend — Mini-SICE (React + Material UI)

```plaintext
school-frontend/
├── src/
│   ├── api/
│   │   ├── http.ts                 # Configuración global de Axios
│   │   ├── students.api.ts         # CRUD de alumnos
│   │   └── grades.api.ts           # CRUD de calificaciones
│   ├── context/
│   │   └── AuthContext.tsx         # Manejo de autenticación (login/logout/user/token)
│   ├── routes/
│   │   └── AppRoutes.tsx           # Definición de rutas públicas y protegidas
│   ├── pages/
│   │   ├── LoginPage.tsx           # Inicio de sesión
│   │   ├── DashboardPage.tsx       # Panel principal con estadísticas
│   │   ├── StudentsPage.tsx        # Gestión de alumnos
│   │   ├── TeachersPage.tsx        # Gestión de profesores
│   │   ├── SubjectsPage.tsx        # Gestión de materias
│   │   └── GradesPage.tsx          # Captura y consulta de calificaciones
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Sidebar.tsx         # Menú lateral de navegación
│   │   │   └── Topbar.tsx          # Barra superior
│   │   ├── students/
│   │   │   └── StudentForm.tsx     # Formulario para crear/editar estudiantes
│   │   ├── teachers/               # (componentes adicionales para profesores)
│   │   └── subjects/               # (componentes adicionales para materias)
│   ├── App.tsx                     # Componente raíz del frontend
│   └── main.tsx                    # Punto de entrada de React
└── .env.example                    # Variables de entorno (URL backend, etc.)
```

## 📘 Modelo ER — Mini-SICE (Sugerido)

```plaintext
erDiagram

    STUDENT ||--|{ GRADE : "obtiene"
    TEACHER ||--|{ SUBJECT : "imparte"
    SUBJECT ||--|{ GRADE : "evalúa"

    STUDENT {
        int id
        string first_name
        string last_name
        date birthdate
        string email
    }

    TEACHER {
        int id
        string name
        string email
    }

    SUBJECT {
        int id
        string name
        int teacherId
    }

    GRADE {
        int id
        int studentId
        int subjectId
        float score
    }
```

## 📄 Entregables Finales

Cada equipo debe entregar **todos** los siguientes elementos para completar el proyecto Mini-SICE:

### 🖥 Backend completo
- API con FastAPI
- JWT + roles
- CRUD para alumnos, profesores, materias y calificaciones
- Documentación de endpoints
- Archivo `.env.example`

### 💻 Frontend completo
- SPA con React + Material UI
- Rutas públicas y protegidas
- Dashboard
- Formularios y tablas por módulo
- Consumo del backend con Axios

### 🗄 Tablas SQL
- Exportación completa de la base de datos (`schema.sql`)
- Datos mínimos de prueba (`seed.sql` opcional)

### 🛠 Manual técnico
Incluye:
- Instalación backend
- Instalación frontend
- Dependencias
- Variables de entorno
- Arquitectura del proyecto
- Colección Postman

### 📘 Manual de usuario
Incluye:
- Capturas de pantalla del sistema
- Flujo completo (login → dashboard → módulos)
- Instrucciones para usar cada módulo (alumnos, materias, calificaciones, reportes)

### 🎬 Video demostrativo (3–5 minutos)
Debe mostrar:
- Inicio de sesión
- CRUD de alumnos
- CRUD de profesores
- CRUD de materias
- Captura y consulta de calificaciones
- Dashboard y navegación
- Protección de rutas

---

## 📊 Diagramas requeridos

### 📘 Diagrama ER (Entidad–Relación)
Debe incluir:
- STUDENT
- TEACHER
- SUBJECT
- GRADE
- Relaciones 1–N

### 🏛 Diagrama de Arquitectura
Debe mostrar:
- Frontend (React)
- Backend (FastAPI)
- Base de datos (MySQL)
- Flujo petición/respuesta
- Validación JWT

### 🔐 Diagrama de Flujo de Autenticación
Debe mostrar:
1. Login  
2. Validación de credenciales  
3. Generación de token  
4. Acceso a rutas protegidas  
5. Expiración o logout  

---

## 🎨 Figma recomendado

UI Escolar moderna:
👉 https://www.figma.com/community/file/1219642652767985298/school-management-admin-dashboard-ui


→ [HOME](./../README.md)