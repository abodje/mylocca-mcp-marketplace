# MyLocca MCP (lecture seule)

Donne à Claude un accès en lecture seule à vos données MyLocca : paiements, biens, locataires, documents, indicateurs de performance. Aucune écriture n'est exposée (pas de création de ticket, etc.).

## 1. Générer votre token

1. Connectez-vous à MyLocca en tant qu'administrateur.
2. Allez dans **Paramètres → Assistant IA** (`/admin/parametres/assistant-ia`).
3. Dans la section **Accès MCP**, activez l'accès et cliquez sur **Générer un token**.
4. Copiez le token affiché — il ne sera plus jamais montré en clair.

## 2. Configurer le token localement

Ce plugin lit le token depuis la variable d'environnement `MYLOCCA_MCP_TOKEN`. Ajoutez-la à votre shell :

```bash
export MYLOCCA_MCP_TOKEN="mcp_votre_token_ici"
```

(Ajoutez cette ligne à votre `~/.zshrc` ou `~/.bashrc` pour la conserver entre les sessions.)

## 3. Installer le plugin

```
/plugin marketplace add <owner>/<repo>
/plugin install mylocca-mcp@mylocca-marketplace
```

Redémarrez Claude Code, puis vérifiez que les outils sont disponibles :

```
/mcp
```

## Outils disponibles

- `get_payments_summary` — synthèse des paiements sur une période
- `list_overdue_payments` — liste des loyers impayés en retard
- `search_properties` / `get_property_details` — recherche et fiche d'un bien
- `search_tenants` / `get_tenant_details` — recherche et fiche d'un locataire
- `list_maintenance_requests` — demandes de maintenance
- `list_documents` — baux, quittances, factures
- `analyze_performance` — occupation, recouvrement, encaissements, échéances

Chaque token est lié à un compte administrateur et scopé à son organisation (isolation multi-tenant respectée).
