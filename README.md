# Yoga App - Documentation d'installation et de test

Ce document explique comment installer, configurer et tester l'application **Yoga App**, qui se compose d'un backend Spring Boot et d'un frontend Angular.

## Table des matières

- [Installation et configuration du backend](#installation-et-configuration-du-backend)
- [Installation et configuration du frontend](#installation-et-configuration-du-frontend)
- [Exécution des tests](#exécution-des-tests)
- [Ressources additionnelles](#ressources-additionnelles)
- [Fonctionnalités principales](#fonctionnalités-principales)

## Installation et configuration du backend

### Prérequis

- Java 11
- Maven
- MySQL (sur le port par défaut 3306)

### Configuration de la base de données

Créez une base de données MySQL pour l'application:

```sql
CREATE DATABASE yoga_app;
```

Configurez un utilisateur avec les droits appropriés:

```sql
CREATE USER 'yoga_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON yoga_app.* TO 'yoga_user'@'localhost';
FLUSH PRIVILEGES;
```

Exécutez le script SQL fourni pour initialiser le schéma:

```sh
mysql -u yoga_user -p yoga_app < ressources/sql/script.sql
```

Modifiez le fichier `application.properties` dans le dossier `src/main/resources`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/yoga_app?serverTimezone=UTC
spring.datasource.username=yoga_user
spring.datasource.password=password
spring.jpa.hibernate.ddl-auto=update
```

### Installation et démarrage

Clonez le dépôt:

```sh
git clone https://github.com/Olelouer/yoga-app
```

Accédez au dossier backend et installez les dépendances avec Maven:

```sh
cd yoga-app/backend
mvn clean install
```

Démarrez l'application backend:

```sh
mvn spring-boot:run
```

Le serveur backend démarre sur [http://localhost:8080](http://localhost:8080).

## Installation et configuration du frontend

### Prérequis

- Node.js (version 14 ou supérieure)
- Angular CLI (version 14)

### Installation et démarrage

Accédez au dossier frontend de l'application:

```sh
cd yoga-app/front
```

Installez les dépendances:

```sh
npm install
```

Démarrez l'application frontend:

```sh
npm run start
```

L'application frontend est accessible à l'adresse [http://localhost:4200](http://localhost:4200).

## Accès à l'application

### Compte administrateur

- **Email:** yoga@studio.com
- **Mot de passe:** test!1234

### Créer un compte utilisateur

1. Cliquez sur "Inscription" dans la barre de navigation.
2. Remplissez le formulaire d'inscription.

## Exécution des tests

### Tests backend

Exécution des tests unitaires et d'intégration:

```sh
cd yoga-app/backend
mvn test
```

Le rapport de couverture **JaCoCo** sera généré dans:

```
target/site/jacoco/index.html
```

### Tests frontend

Exécution des tests unitaires avec Jest:

```sh
cd yoga-app/front
npm run test
```

Exécution des tests avec suivi des modifications:

```sh
npm run test:watch
```

Génération du rapport de couverture:

```sh
npm run test:coverage
```

Le rapport de couverture **Jest** sera disponible dans:

```
coverage/lcov-report/index.html
```

### Tests end-to-end

Pour exécuter les tests end-to-end avec **Cypress**:

```sh
cd yoga-app/front
npm run e2e
```

Pour générer le rapport de couverture E2E:

```sh
npm run e2e:coverage
```

Pour ouvrir le tableau de bord Cypress:

```sh
npm run cypress:open
```

Le rapport de couverture **E2E** sera disponible dans:

```
coverage/lcov-report/index.html
```

## Ressources additionnelles

- Collection **Postman** disponible dans: `ressources/postman/yoga.postman_collection.json`
- Script SQL pour la création du schéma: `ressources/sql/script.sql`

## Fonctionnalités principales

### Administrateur

- Visualiser toutes les sessions de yoga
- Ajouter de nouvelles sessions de yoga
- Modifier ou supprimer des sessions existantes

### Utilisateur standard

- Visualiser toutes les sessions de yoga
- S'inscrire à une session de yoga
- Se désinscrire d'une session
- Visualiser le profil utilisateur
