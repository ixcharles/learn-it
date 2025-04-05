
# Fonctionnalités Avancées de GitHub

Ce cours couvre les fonctionnalités avancées de GitHub qui améliorent la gestion de projet, l'automatisation, la sécurité et les intégrations, permettant aux développeurs de tirer pleinement parti de l'écosystème de GitHub.

## Table des Matières

1. [GitHub Pages et Hébergement de Projets](#github-pages-and-hosting-projects)
2. [GitHub Actions pour les Pipelines CI/CD](#github-actions-for-cicd-pipelines)
3. [API GitHub et Intégrations](#github-api-and-integrations)
4. [Gestion des Flux de Travail GitHub avec Actions](#managing-github-workflows-with-actions)
5. [Sécurisation des Dépôts GitHub (Protection des Branches, 2FA)](#securing-github-repositories-branch-protection-2fa)
6. [GitHub Packages et Gestion des Dépendances](#github-packages-and-dependency-management)

---

## GitHub Pages et Hébergement de Projets

GitHub Pages vous permet d'héberger des sites web statiques directement à partir d'un dépôt GitHub.

- **Création de GitHub Pages** : Créez une branche nommée `gh-pages` ou utilisez la branche `main`, et poussez vos fichiers statiques.
- **Domaine Personnalisé** : Vous pouvez lier un domaine personnalisé en configurant le fichier `CNAME`.

**Example:**
1. Créez un dépôt (par exemple, `nomutilisateur.github.io`).
2. Poussez vos fichiers HTML, CSS et JavaScript.
3. Visitez `https://nomutilisateur.github.io` pour voir votre site en ligne.

---

## GitHub Actions pour les Pipelines CI/CD

GitHub Actions automatise les flux de travail tels que l'intégration continue (CI) et le déploiement continu (CD).

- **Création d'Actions** : Définissez les actions dans le répertoire `.github/workflows` en utilisant la configuration YAML.
- **Exécution des Tests et Déploiement** : Exécutez automatiquement les tests et déployez votre application après chaque commit.

**Example:**
```yaml
name: Pipeline CI

on:
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Configurer Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'
      - run: npm install
      - run: npm test
```

---

## API GitHub et Intégrations

L'API GitHub vous permet d'automatiser les interactions avec les dépôts, les issues, les requêtes de tirage et plus encore.

- **Création de Jetons d'Accès Personnel** : Utilisez des jetons pour authentifier les requêtes API de manière sécurisée.
- **Intégrations** : Intégrez GitHub avec des services tiers comme Slack, JIRA et Jenkins.

**Example:**
1. Créez un jeton sur [la page des jetons GitHub](https://github.com/settings/tokens).
2. Utilisez l'API pour lister tous les dépôts :
```bash
curl -H "Authorization: token VOTRE_JETON_D_ACCES_PERSONNEL" https://api.github.com/user/repos
```

---

## Gestion des Flux de Travail GitHub avec Actions

Les flux de travail GitHub automatisent les tâches en fonction d'événements tels que les pushs, les requêtes de tirage ou les issues. Ils sont constitués de tâches et d'étapes exécutées séquentiellement.

- **Déclencheurs de Flux de Travail** : Utilisez des déclencheurs comme `push`, `pull_request` et `schedule` pour démarrer les flux de travail.
- **Tâches et Étapes** : Les tâches peuvent s'exécuter dans des environnements spécifiques, et les étapes exécutent des commandes en séquence.

**Example:**
```yaml
name: Déployer l'Application

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Récupérer le code
        uses: actions/checkout@v2
      - name: Déployer sur le serveur
        run: ./deploy.sh
```

---

## Sécurisation des Dépôts GitHub (Protection des Branches, 2FA)

Les fonctionnalités de sécurité garantissent l'intégrité du code et protègent vos dépôts GitHub.

- **Protection des Branches** : Appliquez des règles pour empêcher les pushs directs, exiger des revues ou exiger des vérifications de statut pour certaines branches.
- **Authentification à Deux Facteurs (2FA)** : Ajoutez une couche de sécurité supplémentaire en exigeant la 2FA pour accéder aux dépôts.

**Example:**
1. Activez la 2FA dans les paramètres GitHub sous **Security**.
2. Configurez la protection des branches sous **Settings > Branches** pour exiger des requêtes de tirage avant la fusion.

---

## GitHub Packages et Gestion des Dépendances

GitHub Packages est un registre de paquets qui vous permet de publier, de partager et de gérer les dépendances directement au sein des dépôts GitHub.

- **Publication de Paquets** : Utilisez GitHub Packages pour publier des images Docker, des paquets npm ou d'autres artefacts.
- **Gestion des Dépendances** : Gérez et installez les dépendances à l'aide du registre de paquets de GitHub dans des projets comme Node.js ou Python.

**Example (npm)** :
1. Ajoutez un paquet au registre :
```bash
npm publish --access public
```
2. Installez un paquet :
```bash
npm install @nomutilisateur/nom-du-paquet
```

---

## Conclusion

### Points Clés à Retenir :
1. **GitHub Pages** permet d'héberger des sites web statiques directement à partir des dépôts.
2. **GitHub Actions** rationalise les processus CI/CD en automatisant les constructions, les tests et les déploiements.
3. L'**API GitHub** permet un accès programmatique aux données du dépôt et s'intègre à d'autres outils.
4. La **sécurisation des dépôts** est cruciale pour protéger le code avec la protection des branches et l'application de la 2FA.
5. **GitHub Packages** facilite le partage et la gestion des paquets logiciels et des dépendances.

### Exercice Pratique :
1. Configurez un site GitHub Pages pour un projet personnel.
2. Créez un flux de travail CI simple à l'aide de GitHub Actions pour exécuter des tests chaque fois que du code est poussé.
3. Explorez l'API GitHub en vous authentifiant avec un jeton d'accès personnel et en listant vos dépôts.
4. Activez la protection des branches sur la branche `main` de votre dépôt et exigez des revues de requêtes de tirage avant la fusion.
5. Publiez un paquet sur GitHub Packages et intégrez-le dans un autre projet.
