# Ya-Ya

Red social y marketplace de servicios que conecta a microemprendedores de oficio (gásfiteres, electricistas, jardineros, técnicos, tatuadores, entre otros) con clientes en Chile. Proyecto de título de Ingeniería en Informática, Duoc UC, sede San Carlos de Apoquindo.

## Funcionalidades

- Registro con validación de RUT y roles de cliente, emprendedor y administrador.
- Servicios con fotos, precio, comuna y promociones; búsqueda con filtros y ranking por calificación (Meilisearch).
- Chat entre cliente y emprendedor con cotizaciones dentro del hilo.
- Horario semanal, reservas en hora de Chile y calendario.
- Reseñas verificadas: solo tras una reserva completada, una por reserva.
- Feed con publicaciones, fotos, me gusta y comentarios; seguidores y colaboración entre emprendedores.
- Notificaciones y panel de administración con moderación, suspensión de cuentas y métricas.

## Stack

| Capa | Tecnología |
|---|---|
| Frontend | Next.js 14 (App Router), React 18, Tailwind CSS, TypeScript |
| Backend | NestJS 10, TypeORM, Passport JWT, class-validator, sharp |
| Base de datos | PostgreSQL 16 |
| Búsqueda | Meilisearch 1.10 |
| Infraestructura | Docker Compose; Redis 7 provisionado para colas futuras |
| Pruebas | Playwright (413 pruebas de extremo a extremo) |
| CI | GitHub Actions: lint y build en cada Pull Request |

## Requisitos

- Docker y Docker Compose.
- Node.js 20 o superior, solo para las pruebas y los scripts de demo.

## Levantar el entorno de desarrollo

```bash
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
docker compose -p yaya-starter up --build
```

- Web: http://localhost:3000
- API: http://localhost:3001 (salud en /health)
- Meilisearch: http://localhost:7700

Para cargar datos de muestra, define `SEED_DEMO=true` en `backend/.env` y reinicia el backend.

## Entorno de demo

```bash
npm run demo:up        # levanta la demo con datos completos
npm run demo:verificar  # revisa que responda
npm run demo:reset     # la reinicia desde cero
npm run demo:down      # la apaga
```

Web en http://localhost:3200 y API en http://localhost:3201. Cuenta de cliente: `cliente@demo.yaya.test`, contraseña `demo-yaya-2026`.

## Pruebas

```bash
cd e2e
npm install
npx playwright test          # contra el entorno de desarrollo
npm run test:demo            # contra la demo
```

## Estructura

```bash
backend/     API NestJS (módulos en src/)
frontend/    aplicación Next.js (páginas en src/app)
e2e/         pruebas Playwright
scripts/     scripts del entorno de demo
Fase 1/      evidencias de la Fase 1
docker-compose.yml       entorno de desarrollo
docker-compose.demo.yml  entorno de demo
```

## Flujo de trabajo en Git

- `main`: código estable.
- `develop`: rama de integración.
- `feature/<tarea>`: una rama por actividad del cronograma; se integra con Pull Request revisado por otro integrante.

## Documentación

La carpeta de documentos del proyecto contiene el documento de inicio, la metodología, el Product Backlog, el Sprint Backlog, la Definition of Done, las retrospectivas, la arquitectura, el modelo de datos, los casos de uso, la guía de Docker, el plan de pruebas y el manual técnico.

## Equipo

Nicolás Conejera, Matías Medina, Mayron Palavecinos y Daslav Rivera. Profesor guía: Juan Carlos Saba.
