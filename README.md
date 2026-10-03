# fastapi-pricing-service
Un microservice backend asynchrone et léger développé avec Python et FastAPI pour récupérer, calculer et exposer des indicateurs de prix de marché en temps réel. L'application interroge des sources de cotations financières externes à l'aide d'un client HTTP non bloquant, valide rigoureusement chaque transaction avec Pydantic et optimise le temps de réponse grâce à un cache mémoire intégré avec expiration temporelle (TTL).

## Fonctionnalités
- Récupération asynchrone des cours de marché via des requêtes HTTP non bloquantes (`httpx`).
- Validation stricte des données d'entrée et de sortie grâce aux schémas Pydantic.
- Système de cache en mémoire avec TTL pour limiter la latence réseau et les appels redondants vers les API externes.
- Calcul de métriques financières simples (rendement, variations relatives, valeur pondérée).
- Documentation interactive OpenAPI générée automatiquement et accessible via Swagger UI.

## Technologies utilisées
- **Python 3.11+**
- **FastAPI** (cadre applicatif asynchrone)
- **Uvicorn** (serveur ASGI)
- **HTTPX** (client HTTP asynchrone)
- **Pydantic** (typage et validation des modèles de données)

## Démarrage rapide

### Prérequis
- Python 3.11 ou une version plus récente installé sur votre machine.

### Installation et exécution
1. Cloner le dépôt :
   git clone https://github.com/votre-nom-utilisateur/market-metrics-microservice.git
   cd market-metrics-microservice

2. Créer et activer un environnement virtuel :
   python -m venv venv
   source venv/bin/activate  # Sous Windows : venv\Scripts\activate

3. Installer les dépendances :
   pip install -r requirements.txt

4. Lancer le microservice :
   uvicorn main:app --reload

5. Accéder à la documentation interactive :
   Ouvrez votre navigateur à l'adresse `http://127.0.0.1:8000/docs`.

## Endpoints principaux
- `GET /health` : Vérifie l'état de fonctionnement du microservice.
- `GET /api/metrics/{ticker}` : Retourne la dernière cotation et les métriques calculées pour le symbole demandé.
- `POST /api/metrics/calculate` : Calcule le rendement d'une position à partir d'un prix d'achat, d'une quantité et d'un symbole fournis en JSON.
- `DELETE /api/cache` : Purge manuellement le cache en mémoire des cotations.
