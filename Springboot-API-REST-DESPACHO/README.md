# /back-Despachos_SpringBoot/README.md

# Backend Despachos - Innovatech Chile

Microservicio especializado en la gestión y seguimiento de despachos. Diseñado para operar de forma independiente en una infraestructura distribuida en la nube.

## 🚀 Tecnologías Utilizadas
- **Lenguaje:** Java 17.
- **Framework:** Spring Boot.
- **Puerto de Servicio:** 8081 (configurado para evitar colisiones en despliegues side-by-side).
- **Persistencia:** Hibernate / MySQL.

## 📦 Componentes Creados (Entregables Técnicos)
1. **Dockerfile de Producción:**
   - Reducción de superficie de ataque mediante imágenes Alpine.
   - Limpieza de capas de construcción para optimizar el almacenamiento en ECR.
2. **Pipeline CI/CD:**
   - Configurado con **GitHub Secrets** para el manejo seguro de llaves de AWS.
   - Despliegue inmutable: cada actualización genera una nueva imagen etiquetada.
3. **Capa de Persistencia:** Configurada para soportar **Named Volumes** de Docker, asegurando que los datos de despacho no sean efímeros.

## 🧪 Endpoints Principales
- `GET /api/despachos`: Listado de servicios.
- `GET /swagger-ui.html`: Documentación interactiva de la API.