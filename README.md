# 🍰 Dulce Vida Web

Desarrollé por mi cuenta esta plataforma full stack para gestionar y vender productos de repostería. Un amigo me apoyó con un commit puntual.

Frontend: React + Vite | Backend: Spring Boot | Autenticación: JWT

<p align="center">
  <img src="https://img.shields.io/badge/Frontend-React-61DBFB?style=for-the-badge&logo=react" alt="React" />
  <img src="https://img.shields.io/badge/Backend-Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot" alt="Spring Boot" />
  <img src="https://img.shields.io/badge/Security-JWT-crimson?style=for-the-badge&logo=jsonwebtokens" alt="JWT" />
  <img src="https://img.shields.io/badge/Database-MySQL-4479A1?style=for-the-badge&logo=mysql" alt="MySQL" />
</p>

Resumen: Dulce Vida Web es una aplicación fullstack para una pastelería que incluye tienda pública, carrito de compras, gestión de usuarios y un panel administrativo para administrar productos, categorías y boletas/pedidos.

---

## ✨ Características principales

- Autenticación con JWT (Access + Refresh tokens).
- Roles: `USUARIO` / `CLIENTE` y `ADMINISTRADOR`.
- Catálogo de productos con imágenes, filtros y paginación.
- Carrito de compras y proceso de checkout (generación de boleta con IVA).
- Panel administrativo con CRUD para Productos, Categorías y Usuarios.
- Upload de imágenes (almacenamiento local por defecto).
- Tests: Vitest (frontend) y JUnit (backend).

---

## 🧭 Estructura del repositorio (actual)

Dulce-Vida-Web/
- backend/ — Spring Boot (API, seguridad, persistencia)  
- frontend/ — React + Vite (UI, context, rutas protegidas)  
- Requerimientos/ — documentación y colecciones (Postman, ERS, testing)  
- db/ — scripts SQL
- boletas_api.json — (archivo JSON en la raíz, utilidades/ejemplos)
- README.md — este archivo

---

## ⚙️ Tecnologías (recomendadas)

- Frontend: React, Vite, Axios, Vitest  
  - Node.js 20.x recomendado
- Backend: Spring Boot 3.x, Spring Security (JWT), Spring Data JPA, Hibernate, MySQL 8  
  - Java 21 (JDK) recomendado
- Herramientas: Maven (mvnw incluido), OpenSSL (generación de secretos)

---

## 🚀 Instalación y ejecución (local)

Requisitos
- Java JDK 21+
- Node.js 20+
- MySQL 8.x

1) Crear la base de datos:
```sql
CREATE DATABASE dulcevidadb CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

2) Backend — configuración y ejecución:
- Edita `backend/src/main/resources/application.properties` o usa variables de entorno:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/dulcevidadb?serverTimezone=UTC&useSSL=false
spring.datasource.username=root
spring.datasource.password=TU_CONTRASEÑA
```
- Variables de seguridad recomendadas:
```properties
app.security.jwt.secret=${JWT_SECRET_BASE64}
app.security.jwt.expiration-ms=3600000
app.security.bcrypt.strength=11
```
Generar secreto (Linux/macOS):
```bash
openssl rand -base64 48
```
- Ejecutar backend:
```bash
cd backend
# Linux/macOS
./mvnw spring-boot:run
# Windows
.\mvnw.cmd spring-boot:run
```
- Servidor por defecto: http://localhost:8080  
- Swagger UI (si está habilitado): http://localhost:8080/swagger-ui.html

3) Frontend — instalar y ejecutar:
```bash
cd frontend
npm install
npm run dev
```
- Frontend por defecto: http://localhost:5173

---

## 🧩 Tokens y storage (frontend)

- Tokens en localStorage (claves usadas por el frontend).
- Interceptor Axios para inyectar Authorization y manejar refresh tokens mediante `/auth/refresh`.

---

## 🧪 Tests

Frontend (Vitest):
```bash
cd frontend
npm test
```

Backend (JUnit / Maven):
```bash
cd backend
./mvnw test
```

---

## 🗃️ Scripts SQL y seed

- Scripts y seeds en `db/` y posiblemente en `backend/src/main/resources/db/`.
- Si `spring.jpa.hibernate.ddl-auto` está activado, Hibernate puede crear/actualizar tablas automáticamente; si prefieres control manual, ejecuta los scripts en `db/`.

---

## 🔐 Endpoints clave (resumen)

- POST /auth/login — autenticar (devuelve token + refreshToken)
- POST /auth/refresh — rota refresh token y devuelve nuevo par
- POST /auth/logout — revoca refresh token
- POST /api/usuarios/{id}/password — cambiar contraseña
- GET /api/boletas/mias — historial del usuario (paginado)
- GET /api/boletas/admin — historial global (admin)
- POST /api/cart/checkout — finaliza pedido y genera boleta (IVA 19%)

---

## 📦 Documentación y utilidades (rutas corregidas)

- Swagger UI: `/swagger-ui.html` (cuando el backend esté corriendo)
- Postman Collection / documentación: Requerimientos/ `postman_collection.json`
- ERS : Requerimientos/ `ERS-Ignacio-Silva.pdf`
- Archivo JSON en la raíz: `boletas_api.json`
- Scripts SQL: `db/`
---

## 🛠️ Contribuir

1. Haz fork del repositorio.  
2. Crea una rama descriptiva: `feature/mi-cambio` o `fix/bug`.  
3. Abre PR con descripción clara y tests si aplica.

---

## 📄 Licencia

Añade un archivo `LICENSE` si quieres publicar el proyecto con una licencia explícita (p. ej. MIT).

---

## ✉️ Autor

Ignacio Silva — desarrollador del proyecto — [@yvvvl](https://github.com/yvvvl)

Hecho con ❤️ y mucho ☕
