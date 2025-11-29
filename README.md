# VS Code Clean Config Template

Ce dépôt contient un template **propre**, **sécurisé** et **reproductible** de configuration VS Code.  
Aucune donnée sensible, aucun cache, aucune information liée à ta machine.  
Uniquement l’essentiel pour recréer ton environnement VS Code partout.

---

# Contenu du template

Le dossier généré `vscode-clean-config/` contient :

```
vscode-clean-config/
├── User/
│   ├── settings.json
│   ├── keybindings.json
│   └── snippets/
└── extensions.txt
```

✔️ Paramètres  
✔️ Keybindings  
✔️ Snippets  
✔️ Liste d’extensions installées  
❌ Pas de stockage global  
❌ Pas de workspaceStorage  
❌ Pas d'historique  
❌ Pas de données locales sensibles

---

# Script : `vscode-sync.sh`

Le script fournit deux commandes :

- `backup` → export propre de ta configuration VS Code
- `restore` → restauration propre sur une nouvelle machine

---

# Sauvegarder ta configuration (Backup)

```bash
./vscode-sync.sh backup
```

Cela génère un template propre dans :

```
./vscode-clean-config/
```

Parfait pour être versionné dans ton Git.

---

# Restaurer ta configuration (Restore)

```bash
./vscode-sync.sh restore
```

Ce que fait la restauration :

1. Sauvegarde automatique de ton ancienne config dans :
   ```
   ~/vscode-local-backup-YYYYMMDD-HHMMSS/
   ```
2. Écrase ta config locale avec le contenu clean du repo
3. Réinstalle toutes les extensions depuis `extensions.txt`

---

# Réinstaller seulement les extensions (option manuelle)

```bash
cat vscode-clean-config/extensions.txt | xargs -n 1 code --install-extension
```

---

# Emplacements du dossier VS Code User

## macOS

```
~/Library/Application Support/Code/User/
```

## Linux

```
~/.config/Code/User/
```

## Windows (Git Bash / PowerShell)

```
%APPDATA%\Code\User\
```

---

# Notes

- S’assure automatiquement de ne **jamais** sauvegarder les dossiers sensibles (`globalStorage`, `workspaceStorage`, etc.)
- Compatible **macOS**, **Linux**, **Windows (Git Bash)**
- Le script peut être exécuté depuis ton repo Git
- Idéal pour synchroniser ton setup VS Code entre plusieurs machines

---

# Idéal pour

- Recréer VS Code rapidement sur un nouvel ordinateur
- Garder un environnement propre et versionné
- Éviter toute fuite de données sensibles
- Maintenir un template personnel pro / dev setup
