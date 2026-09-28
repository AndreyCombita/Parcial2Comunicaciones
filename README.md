# Parcial Redes y Comunicaciones - Despliegue Zero-Touch

Infraestructura multicontenedor orquestada con Docker Compose.

## Arquitectura
- **Nginx**: Proxy Inverso expuesto en el puerto 80.
- **Joomla**: CMS conectado a PostgreSQL.
- **PostgreSQL**: Base de datos aislada en `backend_net`.
- **Jupyter Lab**: Entorno de analítica (`/jupyter/`).
- **Grafana**: Monitoreo autoconfigurado (`/grafana/`).

## Instrucciones de Despliegue
1. Copiar variables de entorno:
   ```bash
   cp .env.example .env
2. Levantar la infraestructura:
   docker compose up -d

3. Accesos:
   - Joomla: http://localhost/
   - Jupyter: http://localhost/jupyter/
   - Grafana: http://localhost/grafana/ (admin/admin)
