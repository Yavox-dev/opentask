# Architecture cible

L'architecture est atteinte progressivement : chaque composant arrive à l'itération qui en a besoin.

```
              FRONTEND (Next.js)
                     |
                     v
              BACKEND API (NestJS)
                     |
       +-------------+-------------+
       |             |             |
       v             v             v
   PostgreSQL      Redis       WebSocket
       ^             |
       |             v
       |         Job queue
       |             |
       |             v
       +------ Background worker
```

| Composant | Itération |
| --- | --- |
| Frontend, backend, PostgreSQL | 1 |
| WebSocket | 3 |
| Redis (cache, rate limiting) | 4 |
| File d'attente et worker | 5 |
