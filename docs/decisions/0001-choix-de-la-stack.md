# 0001. Choix de la stack technique

- Statut : accepté
- Date : 2026-11-26

## Contexte

OpenTask doit couvrir, au fil de 8 itérations, une API REST, de la collaboration en temps réel, du cache, des jobs asynchrones et un tableau de bord analytique. Le projet est mené par un développeur seul et sert de portfolio : la stack doit être cohérente de bout en bout et représentative de ce qui se fait en entreprise.

## Décision

- **TypeScript partout** (frontend, backend, worker), dans un monorepo pnpm, pour partager les types via `packages/shared`.
- **Next.js** pour le frontend.
- **NestJS** pour le backend : architecture modulaire, injection de dépendances, support natif des WebSockets, de Swagger et des files d'attente.
- **PostgreSQL + Prisma** : modèle relationnel adapté (utilisateurs, équipes, projets, tâches), migrations versionnées et typage généré.
- **JWT + refresh tokens** pour l'authentification.
- **Redis** (itération 4) pour le cache, le rate limiting et la file d'attente des jobs (BullMQ).
- **Jest + Playwright** pour les tests, **Docker + GitHub Actions** pour l'intégration et le déploiement.

## Alternatives envisagées

- **Python (FastAPI) ou Java (Spring Boot)** pour le backend : solides, mais obligent à dupliquer les types entre frontend et backend.
- **Express seul** : plus léger, mais il faudrait reconstruire la structure que NestJS fournit déjà.
- **Microservices dès le départ** : trop coûteux pour un développeur seul. L'extraction d'un service (notifications) reste une piste après l'itération 8.

## Conséquences

- Un seul langage à maîtriser, des types partagés de bout en bout.
- Les composants (Redis, WebSockets, worker) sont introduits seulement à l'itération qui en a besoin.
- NestJS impose une courbe d'apprentissage (modules, décorateurs) au départ.
