# Informe Técnico: Arquitectura de Red y Despliegue Multicontenedor

## 1. Diseño de Red y Aislamiento
La arquitectura implementa segmentación de red utilizando el driver bridge de Docker:
- frontend_net: Conecta el Proxy Inverso (Nginx) con las aplicaciones (Joomla, Jupyter, Grafana).
- backend_net: Aísla la base de datos PostgreSQL. Solo Joomla y Grafana tienen acceso a esta red.

El puerto 5432 de PostgreSQL no está expuesto al host, garantizando el principio de mínimo privilegio y seguridad perimetral.

## 2. Estrategia Zero-Touch y Resiliencia
- Healthchecks: Se configuró pg_isready para verificar la disponibilidad de PostgreSQL antes de iniciar Joomla.
- Aprovisionamiento Automático: Grafana carga la fuente de datos mediante YAML sin requerir intervención manual.
- Reverse Proxy: Nginx centraliza el tráfico web y soporta conexiones persistentes (WebSockets) para Jupyter.
