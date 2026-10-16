# VeritAI — Fake News Detection

VeritAI est une application web qui analyse un texte d'actualité et utilise plusieurs modèles de Machine Learning pour estimer s'il ressemble davantage à une information **FAKE** ou **REAL**.

> **Important :** les prédictions sont des estimations automatiques et peuvent être incorrectes. Elles ne remplacent pas la vérification des sources journalistiques.

## Fonctionnalités

- Analyse de texte avec plusieurs modèles de Machine Learning.
- Modèles pris en charge : Naive Bayes, XGBoost, SGDClassifier, Linear SVM, Decision Tree, Random Forest et Logistic Regression.
- Prétraitement du texte et vectorisation TF-IDF.
- Affichage des prédictions, du niveau de confiance estimé et du temps de traitement.
- API Flask pour communiquer avec l'interface web.
- Extraction de texte depuis des fichiers PDF et DOCX lorsque les dépendances correspondantes sont installées.
- Statut des modèles via l'endpoint `/api/status`.

## Technologies

- Python
- Flask et Flask-CORS
- scikit-learn
- XGBoost
- NLTK
- NumPy et Joblib
- HTML, CSS et JavaScript pour l'interface

## Structure du projet

```text
veritai/
├── app.py
├── index.html
├── requirements.txt
├── diagnose.py
├── README.md
└── models/
    ├── naive_bayes.pkl
    ├── xgboost.pkl
    ├── sgd.pkl
    ├── svm_linearsvc.pkl
    ├── decision_tree.pkl
    ├── random_forest.pkl
    ├── logistic_regression.pkl
    ├── tfidf_vectorizer.pkl
    ├── tfidf_vectorizer_xgb.pkl
    └── model_stats.json
```

Les fichiers `.pkl` contiennent les modèles et vectoriseurs entraînés nécessaires à la prédiction. Ils doivent rester dans le dossier `models/`, à côté de `app.py`.

## Installation

Python est nécessaire. Depuis le dossier `veritai/`, crée et active un environnement virtuel.

### Windows

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Si PowerShell bloque l'activation, tu peux utiliser directement :

```powershell
venv\Scripts\python.exe -m pip install -r requirements.txt
```

## Lancer l'application

1. Dans le terminal, depuis le dossier `veritai/`, lance :

   ```bash
   python app.py
   ```

2. Ouvre ensuite `index.html` dans ton navigateur, comme indiqué par l'application. Si l'interface ne se connecte pas à l'API, vérifie que le serveur Flask est lancé et que l'URL de l'API dans `index.html` correspond à `http://localhost:5000`.

3. Pour vérifier que les modèles sont chargés, ouvre :

   `http://localhost:5000/api/status`

   Le champ `ready` doit être `true`. Si ce n'est pas le cas, consulte `load_errors` dans la réponse et vérifie la présence des fichiers requis dans `models/`.

## API

### `GET /api/status`

Renvoie l'état de l'application, les modèles chargés et les fonctionnalités disponibles.

### `POST /api/predict`

Envoie un texte à analyser et, facultativement, la liste des modèles à utiliser.

Exemple de corps JSON :

```json
{
  "text": "Paste a sufficiently long news article here...",
  "models": ["Naive Bayes", "Random Forest"]
}
```

Le texte doit contenir au moins 20 caractères. La réponse contient les prédictions disponibles pour les modèles sélectionnés.

## Vérifier les modèles

Pour lancer le script de diagnostic :

```bash
python diagnose.py
```

Il vérifie le chargement des vectoriseurs et des modèles, puis tente une prédiction de test.

## Limites

- Une classification FAKE/REAL ne prouve pas qu'une information est vraie ou fausse.
- Les résultats dépendent des données d'entraînement, du prétraitement et des modèles sauvegardés.
- Les performances affichées ne sont disponibles que si `models/model_stats.json` contient les statistiques correspondantes.
- Les modèles sauvegardés avec Joblib peuvent nécessiter des versions compatibles de Python, NumPy et scikit-learn. En cas d'erreur de chargement, utilise les versions employées lors de l'entraînement.

## Auteur

Projet académique de détection de fake news avec Machine Learning.

Ajoute ici ton nom, ton établissement, l'année du projet et, si tu le souhaites, une capture d'écran de l'interface.
