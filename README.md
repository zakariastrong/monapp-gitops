# monapp-gitops

Dépôt GitOps de [monapp](https://github.com/zakariastrong/mon-app) : il décrit
**l'état voulu** du cluster. Argo CD lit le dossier `apps/monapp/` de la branche
`main` et aligne le cluster dessus.

| Chemin | Rôle |
|--------|------|
| `argocd/application.yaml` | L'Application Argo CD, appliquée **une seule fois** à la main |
| `apps/monapp/` | Le dossier surveillé par Argo CD (Deployment + Service) |
| `JOURNAL.md` | Une ligne par déploiement |

## Règle d'or

On ne modifie jamais l'application avec `kubectl`. Tout changement passe par une
Pull Request sur ce dépôt. Pour revenir en arrière : bouton **Revert** sur la PR
fusionnée.

## Installation (une seule fois)

```bash
kubectl apply -f argocd/application.yaml
kubectl -n argocd get application monapp
```
