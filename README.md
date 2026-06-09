# PagoYa API

![Java](https://img.shields.io/badge/Java-21-007396?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-4.0.3-6DB33F?logo=springboot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-Auth-000000?logo=jsonwebtokens&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-Build-C71A36?logo=apachemaven&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-OpenAPI-85EA2D?logo=swagger&logoColor=black)

Plataforma fintech de pagos y billetera digital. API REST que gestiona usuarios,
cuentas, transferencias y pago de servicios.

**Autor:** Henry Antonio Mendoza Puerta

---

## Funcionalidades

- **Autenticación y seguridad** — registro, login, refresh token y logout con JWT.
- **Clientes** — gestión de los datos del cliente (perfil, DNI, teléfono).
- **Cuentas** — creación de cuentas, consulta de saldo y depósitos.
- **Transferencias** — transferencias entre cuentas con validación de saldo.
- **Pago de servicios (billing)** — pago de recibos a proveedores (luz, agua, telecom)
  y pagos recurrentes programados.
- **Reportes** — reportes de transferencias y pagos mediante funciones SQL.
- **Documentación interactiva** — Swagger UI / OpenAPI.

---

## Tecnologías

| Categoría | Tecnología |
|---|---|
| Lenguaje | Java 21 |
| Framework | Spring Boot 4.0.3 (Web, Data JPA, Security, Validation) |
| Base de datos | PostgreSQL 16 |
| Autenticación | JWT (jjwt 0.12.6) |
| Mapeo de DTOs | MapStruct 1.6.3 |
| Utilidades | Lombok |
| Documentación | springdoc-openapi (Swagger UI) |
| Build | Maven |
| Contenedores | Docker / Docker Compose |

---

## Requisitos

- Java 21
- Maven 3.9+
- Docker (para la base de datos)

---

## Comandos

### 1. Levantar la base de datos (PostgreSQL + pgAdmin)

```bash
docker compose up -d
```

- PostgreSQL → `localhost:55432`
- pgAdmin → `http://localhost:8082` (usuario: `admin@pagoya.com`, contraseña: `admin`)

### 2. Ejecutar la aplicación

```bash
mvn spring-boot:run
```

La API queda disponible en `http://localhost:8080`.

### 3. Compilar el proyecto

```bash
mvn clean package
```

### 4. Ejecutar los tests

```bash
mvn test
```

### 5. Levantar todo con Docker (build de la imagen)

```bash
docker build -t pagoya-api .
docker run -p 8080:8080 --env-file .env pagoya-api
```

---

## Documentación de la API

Con la aplicación corriendo:

- Swagger UI → `http://localhost:8080/swagger-ui.html`
- OpenAPI JSON → `http://localhost:8080/v3/api-docs`

---

## Usuarios de prueba

Sembrados automáticamente al iniciar (contraseña: `password123`):

| Email | Rol |
|---|---|
| `admin@pagoya.com` | ADMIN |
| `ana@pagoya.com` | CUSTOMER |
| `luis@pagoya.com` | CUSTOMER |

---

## Variables de entorno

Configurables mediante un archivo `.env` (no se sube al repositorio):

| Variable | Descripción |
|---|---|
| `SPRING_PROFILES_ACTIVE` | Perfil activo (`local` / `prod`) |
| `DB_URL` / `DB_USERNAME` / `DB_PASSWORD` | Conexión a la base de datos |
| `JWT_SECRET` | Secreto para firmar los JWT (mínimo 32 bytes) |
| `CORS_ALLOWED_ORIGINS` | Orígenes permitidos para CORS (separados por comas) |
