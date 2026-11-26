# Contribuer à OpenTask

Merci de votre intérêt ! Voici comment le projet est organisé.

## Branches

- `main` : version stable, chaque release y est taguée.
- `feature/<nom>` : nouvelle fonctionnalité (ex. `feature/authentication`).
- `fix/<nom>` : correction de bug.
- `chore/<nom>` : outillage, configuration, documentation.

Chaque branche part de `main` et y revient par une pull request.

## Commits

Le projet suit [Conventional Commits](https://www.conventionalcommits.org/fr/) :

```
feat(backend): ajout de la connexion par JWT
fix(frontend): le tableau ne se rafraîchit plus après suppression
docs: ADR sur le choix de Redis
```

## Pull requests

1. Liez l'issue concernée (`Closes #12`).
2. Ajoutez ou mettez à jour les tests.
3. Vérifiez que `pnpm lint` et `pnpm test` passent.
4. Remplissez le modèle de pull request.

## Décisions techniques

Toute décision d'architecture importante fait l'objet d'un ADR dans `docs/decisions/`, en partant de [0000-modele.md](docs/decisions/0000-modele.md).
