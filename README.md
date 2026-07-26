# utn-config-server

Servidor de configuracion centralizada para la arquitectura de microservicios del proyecto.

## Objetivo

- Exponer configuraciones externas para los servicios via Spring Cloud Config.
- Leer propiedades desde un repositorio Git.
- Evitar duplicar configuracion en cada microservicio.

## Stack

- Java 21
- Spring Boot 3.4.0
- Spring Cloud Config Server
- Maven Wrapper (`mvnw.cmd`)

## Configuracion actual

Archivo: `src/main/resources/application.yaml`

- `spring.application.name: config-server`
- `server.port: 8888`
- `spring.cloud.config.server.git.uri: https://github.com/gastonsbonanno/utn-config-repo`
- `spring.cloud.config.server.git.default-label: main`
- `spring.cloud.config.server.git.search-paths: configs`
- `spring.cloud.config.server.git.clone-on-start: true`

## Requisitos

- Java 21
- Acceso de red al repositorio Git de configuracion

## Ejecucion local

```powershell
.\mvnw.cmd spring-boot:run
```

## Paso a paso de arranque

> Asegurarse de tener instalado y corriendo Docker Desktop antes de levantar la base de datos.

1. Ir a la carpeta `utn-config-server` y levantar la base de datos con Docker Compose:

   ```powershell
   docker-compose up -d
   ```

2. Levantar el `config-server`.
3. Levantar el `eureka-server`.
4. Levantar `utn-product-service`.
5. Levantar `utn-customer-service`.

> Orden recomendado: primero `docker-compose up` en `utn-config-server`, luego `config-server`, luego `eureka-server`, luego `product-service` y por ultimo `customer-service`.
