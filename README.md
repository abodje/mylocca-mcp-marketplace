# MyLocca — Marketplace de plugins Claude Code

Ce dossier est une marketplace Claude Code autonome. Il ne fait pas partie de l'application MyLocca elle-même — c'est un petit paquet de fichiers de configuration qui pointe vers le serveur MCP déjà déployé (`https://app.lokapro.tech/mcp`).

## Publier cette marketplace

Ce dossier doit devenir **son propre dépôt Git**, distinct du backend MyLocca (qui est privé et ne doit jamais être ajouté comme source de marketplace).

```bash
cd mcp-marketplace
git init
git add .
git commit -m "Initial marketplace: MyLocca MCP plugin"
git remote add origin git@github.com:<votre-compte>/mylocca-mcp-marketplace.git
git push -u origin main
```

Le dépôt peut être public (pour que d'autres utilisateurs MyLocca l'utilisent) ou privé (accessible seulement à votre équipe, selon les droits GitHub).

## Utiliser la marketplace

Une fois poussée sur GitHub :

```
/plugin marketplace add <votre-compte>/mylocca-mcp-marketplace
/plugin install mylocca-mcp@mylocca-marketplace
```

Chaque utilisateur doit d'abord générer son propre token dans **Paramètres → Assistant IA** de son instance MyLocca et l'exporter en variable d'environnement `MYLOCCA_MCP_TOKEN` (voir `plugins/mylocca-mcp/README.md`).

## Structure

```
mcp-marketplace/
├── .claude-plugin/
│   └── marketplace.json       # manifeste de la marketplace
└── plugins/
    └── mylocca-mcp/
        ├── .claude-plugin/
        │   └── plugin.json     # manifeste du plugin
        ├── .mcp.json            # déclaration du serveur MCP distant
        └── README.md            # instructions pour l'utilisateur final
```

## Mettre à jour l'URL du serveur

Si l'URL de production change, modifiez `plugins/mylocca-mcp/.mcp.json` et incrémentez la version dans les deux `plugin.json` / `marketplace.json`, puis republiez (`git commit` + `git push`).
