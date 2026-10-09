# Journal de bord des déploiements

Une ligne par déploiement ou par expérience.

| Date et heure | PR | Version | Ce que j'ai changé | Résultat observé |
|---------------|----|---------|--------------------|------------------|
| 09/10 12:09 | — | 1.0.0 | Premier déploiement : `kubectl apply` de `argocd/application.yaml` (commit `71af4ea` poussé avant le ruleset) | Synced + Healthy, 4 pods Running, `uid=10001`, `/version` = 1.0.0 |
| 09/10 12:15 | — | 1.0.0 | Drift : `kubectl -n monapp scale deployment monapp --replicas=1` | OutOfSync en moins d'1 s, selfHeal remet 4 réplicas en 1 s, 4/4 prêts en 12 s |
| 09/10 14:16 | #1 | 1.0.0 | Prune (1/2) : ajout de `configmap-test.yaml` | ConfigMap `test-prune` créé par Argo CD (révision `92a7eb7`) |
| 09/10 14:54 | #2 | 1.0.0 | Prune (2/2) : suppression de `configmap-test.yaml` | ConfigMap `test-prune` supprimé (« pruned »), Deployment et Service inchangés (révision `1d6ae64`) |
