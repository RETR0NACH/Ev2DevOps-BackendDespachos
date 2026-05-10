# 🚚 Backend Despachos - Innovatech Chile

![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=java&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-Cloud-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

## 📖 Descripción del Microservicio

Este repositorio contiene el microservicio de **Despachos**, el componente encargado de la gestión, seguimiento y cierre de la logística de entrega para Innovatech Chile. Diseñado para operar de forma independiente, este servicio se integra con la capa de persistencia para garantizar la trazabilidad de cada paquete desde su salida del almacén hasta la entrega final.

A nivel de infraestructura, opera en la **Capa de Aplicación (App Tier)** sobre una instancia privada en AWS, coexistiendo de forma aislada con otros microservicios mediante el uso de puertos diferenciados y redes virtuales.

---

## 🚀 Stack Tecnológico

### Backend & Datos

- **Lenguaje:** Java 17.
- **Framework:** Spring Boot con Spring Data JPA.
- **Puerto de Servicio:** 8081 (Configurado para evitar colisiones en despliegues side-by-side).
- **Persistencia:** Hibernate / MySQL 8.0.

### Infraestructura & DevOps

- **Contenerización:** Docker (Imagen base Alpine para reducción de superficie de ataque).
- **CI/CD:** GitHub Actions (Automatización total del ciclo de vida).
- **Despliegue:** Inmutable mediante Amazon ECR y AWS Systems Manager (SSM).
- **Persistencia Volátil:** Configurada para soportar **Named Volumes** de Docker, asegurando la integridad de logs y datos temporales.

---

## 🛠️ Entregables Técnicos y Seguridad

1. **Dockerfile de Producción:**
   - Implementación de **Multi-stage build** para optimizar el almacenamiento en ECR.
   - Ejecución segura bajo un usuario **Non-root**, limitando los permisos del proceso Java dentro del contenedor.
2. **Pipeline CI/CD Robusto:**
   - Manejo seguro de credenciales mediante **GitHub Secrets**.
   - Despliegue automatizado hacia EC2 que garantiza que cada actualización genere una nueva imagen etiquetada, permitiendo _rollbacks_ inmediatos si es necesario.
3. **Externalización (12-Factor App):**
   - El servicio consume variables de entorno para su conexión a la base de datos, permitiendo que el mismo binario funcione en Dev, Test y Prod sin cambios en el código.

---

## ⚙️ Configuración del Entorno (Environment)

El microservicio utiliza las siguientes variables de entorno clave, inyectadas de forma segura durante el despliegue:

| Variable                | Propósito                        | Valor Sugerido                                  |
| :---------------------- | :------------------------------- | :---------------------------------------------- |
| `SPRING_DATASOURCE_URL` | Conexión JDBC a la base de datos | `jdbc:mysql://${DB_ENDPOINT}:3306/tienda_db...` |
| `DB_USERNAME`           | Usuario de base de datos         | Definido en Secrets                             |
| `DB_PASSWORD`           | Contraseña de base de datos      | Definido en Secrets                             |

---

## 💻 Ejecución y Pruebas

### Local (Docker Compose)

Para levantar este servicio junto con el ecosistema completo:

```bash
docker compose up -d
```
El servicio estará disponible en http://localhost:8081.

---

## Endpoints Principales
Listado de Despachos: GET /api/v1/despachos.

Documentación Interactiva: GET /swagger-ui.html.

## 🌿 Metodología de Trabajo
Este repositorio sigue un flujo de Integración Continua:

El desarrollo se realiza en ramas de funcionalidad o en la rama deploy.

Se requiere un Pull Request (PR) hacia la rama main para consolidar cambios.

El Merge a main dispara automáticamente el despliegue a la infraestructura de AWS.

Módulo de Logística - Innovatech Chile.


```
