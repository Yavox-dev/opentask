# OpenTask

Plateforme open source de gestion de projets collaboratifs : projets, tâches, équipes, collaboration en temps réel, automatisations et statistiques de productivité.

Le projet est construit par itérations, chacune apportant de nouvelles fonctionnalités et faisant évoluer l'architecture. Le processus de développement (issues, pull requests, décisions techniques, releases) fait partie du projet.

## Stack

| Couche | Technologie |
| --- | --- |
| Frontend | Next.js + TypeScript |
| Backend | NestJS |
| Base de données | PostgreSQL + Prisma |
| Authentification | JWT + refresh tokens |
| Temps réel | WebSockets |
| Cache et files d'attente | Redis |
| Tests | Jest + Playwright |
| DevOps | Docker + GitHub Actions |
| Documentation API | Swagger |

Les raisons de ces choix sont dans [docs/decisions/0001-choix-de-la-stack.md](docs/decisions/0001-choix-de-la-stack.md).

## Feuille de route

| Itération | Semaines | Objectif | Livrable |
| --- | --- | --- | --- |
| 1 | 1-2 | MVP et fondations | MVP fonctionnel |
| 2 | 3-4 | Gestion collaborative | Application multi-utilisateurs |
| 3 | 5-6 | Collaboration temps réel | Kanban et notifications en direct |
| 4 | 7-8 | Performance et scalabilité | Backend optimisé |
| 5 | 9-10 | Automatisation | Tâches récurrentes, règles, jobs |
| 6 | 11-12 | Analytics et reporting | Tableau de bord analytique |
| 7 | 13-14 | Qualité et architecture | Application robuste |
| 8 | 15-16 | Production et open source | Projet public exploitable |

Chaque itération a sa milestone GitHub et ses issues.

## Structure du dépôt

```
apps/
  frontend/        Next.js
  backend/         API NestJS
  worker/          jobs asynchrones (itération 5)
packages/
  shared/          types partagés
  config/          configurations communes (TS, lint)
infrastructure/
  docker/          Dockerfiles
  monitoring/      supervision (itération 8)
docs/
  architecture/    schémas et vue d'ensemble
  api/             documentation de l'API
  decisions/       ADR (Architecture Decision Records)
```

## Démarrer en local

Prérequis : Node.js 22, pnpm 10, Docker.

```bash
cp .env.example .env
pnpm install
pnpm db:up        # lance PostgreSQL
pnpm dev          # disponible à partir de l'itération 1
```

## Contribuer

Voir [CONTRIBUTING.md](CONTRIBUTING.md).

## Licence

[MIT](LICENSE)
