# LogiAI 🚚🤖 — Prédiction du risque de retard de livraison

**LogiAI** est un service complet de Machine Learning permettant de prédire le risque de retard de livraisons logistiques en fonction de divers facteurs (distance, météo, véhicule, trafic, etc.). Le projet expose un modèle prédictif via une **API REST FastAPI** et propose une interface utilisateur interactive **Streamlit** pour les dispatchers.

---

## 📌 Description du Projet

Dans le secteur du transport, anticiper les retards permet d'optimiser les tournées et de prévenir les clients à temps. Ce projet transforme un modèle Machine Learning en un microservice disponible sur le réseau :
- **Validation stricte** des données d'entrée via des schémas **Pydantic**.
- **API REST** performante développée avec **FastAPI** et exécutée via **Uvicorn**.
- **Interface web Streamlit** permettant d'évaluer une livraison en temps réel et de déclencher une alerte si la probabilité dépasse le seuil défini (0.4).

---

## 📸 Aperçu de l'Application

### 1. Documentation OpenAPI (Swagger UI)
L'API REST est documentée et testable directement à l'adresse `/docs` :

![Documentation Swagger](docs/swagger-docs.png)

### 2. Interface Streamlit — Simulations par type de véhicule
L'interface permet de tester différents scénarios logistiques en temps réel :

| Simulation Moto | Simulation Fourgon | Simulation Camion |
| :---: | :---: | :---: |
| ![Moto](docs/streamlit-moto.png) | ![Fourgon](docs/streamlit-fourgon.png) | ![Camion](docs/streamlit-camion.png) |
| **82.9%** de risque | **90.1%** de risque | **94.3%** de risque |

---

## 🏗️ Architecture du Projet

```text
logiai/
├── logiai/
│   ├── api/
│   │   ├── main.py        # Routes REST (/health, /v1/predict)
│   │   └── schemas.py     # Schémas Pydantic de validation
│   ├── config.py          # Configuration globale (seuils, chemins)
│   ├── dataset.py         # Génération du jeu de données
│   ├── train.py           # Entraînement et sauvegarde du modèle
│   └── predict.py         # Chargement du modèle et prédiction
├── data/                  # Jeu de données CSV
├── models/                # Modèle sauvegardé (.joblib)
├── tests/                 # Tests unitaires Pytest
├── streamlit_app.py       # Application client Streamlit
├── COMPTE_RENDU.md        # Compte-rendu des travaux pratiques
└── requirements.txt       # Dépendances Python