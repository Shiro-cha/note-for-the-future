# Cahier des Charges : CLI de Génération de Structure de Dossiers

## 1. Introduction

### 1.1. Contexte
Dans le cadre de l'automatisation et de la standardisation des environnements de développement, ce projet vise à créer un outil en ligne de commande (CLI) permettant de générer une structure de dossiers et de fichiers à partir d'un fichier de configuration au format JSON ou YAML.

### 1.2. Objectifs
- Offrir un outil CLI performant et flexible pour créer des arborescences de fichiers basées sur des modèles JSON/YAML.
- Permettre une personnalisation avancée grâce à des variables et des templates.
- Garantir une intégration fluide avec d'autres outils DevOps.

## 2. Fonctionnalités

### 2.1. Entrées
- Un fichier JSON ou YAML décrivant la structure à générer.
- Optionnel : des variables dynamiques pour personnaliser le template.
- Optionnel : support des fichiers `.env` pour injecter des variables d’environnement.

### 2.2. Sorties
- Création d’une structure de dossiers et fichiers selon la configuration.
- Remplacement dynamique des variables dans les fichiers générés.
- Support de logs détaillés pour le suivi des actions.

### 2.3. Fonctionnalités principales
- Lecture et validation du fichier de configuration.
- Génération récursive des dossiers et fichiers.
- Support des placeholders pour le remplissage dynamique.
- Mode "dry-run" pour prévisualiser la structure sans exécution.
- Compatibilité multi-plateforme (Windows, macOS, Linux).

## 3. Contraintes Techniques

### 3.1. Langage et Framework
- Développement en **TypeScript** avec Node.js.
- Utilisation d’un parser YAML (`js-yaml` ou équivalent).
- Gestion des arguments CLI avec `commander.js` ou `yargs`.

### 3.2. Format de Configuration

#### Exemple JSON
```json
{
  "root": "my_project",
  "structure": {
    "src": {
      "index.ts": "console.log('Hello, world!');",
      "utils": {}
    },
    "config": {
      "config.json": "{\"env\": \"development\"}"
    },
    "README.md": "# My Project"
  }
}
```

#### Exemple YAML
```yaml
root: my_project
structure:
  src:
    index.ts: "console.log('Hello, world!');"
    utils: {}
  config:
    config.json: "{\"env\": \"development\"}"
  README.md: "# My Project"
```

## 4. Interface Utilisateur (CLI)

### 4.1. Commandes Principales
- `generate` : Générer la structure de dossiers/fichiers.
- `validate` : Valider un fichier JSON/YAML sans exécution.
- `dry-run` : Simuler la génération sans création physique.

### 4.2. Options
- `-c, --config <file>` : Spécifier le fichier de configuration.
- `-o, --output <dir>` : Définir le répertoire de sortie.
- `--dry-run` : Exécuter en mode simulation.
- `--verbose` : Afficher des logs détaillés.

## 5. Sécurité et Fiabilité
- Vérification et validation des fichiers d’entrée.
- Gestion des erreurs avec messages explicites.
- Tests unitaires et d’intégration via Jest ou Mocha.

## 6. Évolutivité et Perspectives
- Ajout d’un mode interactif avec prompts.
- Support des templates avancés (Handlebars, EJS).
- Génération de scripts spécifiques (ex: Dockerfile, CI/CD).

## 7. Conclusion
Ce projet vise à fournir un outil robuste et flexible permettant aux développeurs et DevOps d’automatiser la création de structures de projets tout en garantissant un haut niveau de personnalisation et d’intégration.

