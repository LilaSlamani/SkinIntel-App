# SkinIntel

SkinIntel est une application de démonstration pour analyser les ingrédients des produits cosmétiques en utilisant des données de l'EWG (Environmental Working Group). Le projet comprend un scraper pour extraire et traiter les données EWG, et une webapp pour analyser les routines utilisateurs.

## Architecture

- **Scraper** : Utilise Apache Airflow pour orchestrer l'extraction, transformation et chargement des données EWG dans PostgreSQL.
- **Webapp** : Application Flask avec plugins pour la vérification de conflits, redondances, et suggestions de routines.

## Prérequis

- Docker et Docker Compose
- Git

## Installation et exécution

1. Clonez le dépôt :
   ```
   git clone https://github.com/LilaSlamani/SkinIntel-Demo.git
   cd SkinIntel-Demo
   ```

2. Copiez le fichier d'environnement et configurez-le :
   ```
   cp .env.example .env
   # Éditez .env avec vos clés API et configurations (ex: base de données)
   ```

3. Lancez les services avec Docker Compose :
   ```
   docker-compose up --build
   ```

4. Accédez à la webapp : Ouvrez http://localhost:5000 dans votre navigateur.

## Utilisation

- **Scraper** : Les DAGs Airflow s'exécutent automatiquement pour scraper et traiter les données.
- **Webapp** : Uploadez une photo de vos produits pour analyser les ingrédients et obtenir des suggestions.

## Tests

Exécutez les tests dans le répertoire `webapp` :
```
cd webapp
python -m pytest tests/
```

## Contribution

Ce projet est une démonstration. Pour contribuer, créez une branche et soumettez une PR.