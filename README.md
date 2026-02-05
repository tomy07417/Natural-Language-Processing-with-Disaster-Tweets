# Proyecto: Natural Language Processing with Disaster Tweets

Este repositorio reúne el trabajo práctico (TP N.º3) de la materia de Ciencia de Datos / Machine Learning, basado en la competencia de Kaggle "NLP - Getting Started" (https://www.kaggle.com/c/nlp-getting-started).

**Objetivo del proyecto**
- Construir modelos que predigan si un tweet describe un desastre real (`target` = 1) o no (`target` = 0).
- Desarrollar análisis exploratorio, features, modelos baseline y modelos avanzados según la consigna del TP.

Descripción de la competencia
- URL: `https://www.kaggle.com/c/nlp-getting-started`
- Resumen: el dataset contiene aproximadamente 10k tweets etiquetados a mano; el reto es predecir si un tweet habla sobre un desastre real.
- Nota: el dataset puede contener lenguaje profano u ofensivo.

Estructura del repositorio
- `*.ipynb`: notebooks con análisis y modelos. Notebooks principales incluidos:
  - `exploracion_ml.ipynb` : visualizaciones y análisis exploratorio (Parte I).
  - `regresion.ipynb`, `regresion_v2.ipynb` : regresión logística y baseline (Parte II).
  - `red_neuronal_v1.ipynb`, `red_neuronal_v2.ipynb`, `red_neuronal_v3.ipynb` : experimentos con redes neuronales (LSTM/GRU) y embeddings.
  - `random_forest.ipynb`, `xg_boost.ipynb` : modelos de la Parte III (dos modelos distintos además de la regresión logística).
  - `armado_features.ipynb` : notebook con transformaciones y creación de features usadas por los modelos.
  - `words_desastres.txt` : lista de palabras relacionadas con desastres usada como referencia para features.

- `data/` : datos originales y con features.
  - `train.csv`, `test.csv` : archivos originales de la competencia.
  - `train_with_features.csv`, `test_with_features.csv` : versiones con features calculadas.
  - `sample_submission.csv` : formato de ejemplo para submissions.

- `plots/` : gráficos generados durante el análisis.
- `submission/` : CSVs generados para enviar a Kaggle (ej.: `logistic_regression_submission.csv`, `random_forest_submission.csv`, `xgb_sbert_submission.csv`, etc.).

Descripción de los archivos clave
- `train.csv` campos:
  - `id`: identificador del tweet
  - `text`: texto del tweet
  - `location`: (opcional) ubicación
  - `keyword`: (opcional) palabra clave asociada al tweet
  - `target`: etiqueta (1 = desastre real, 0 = no)

Cómo reproducir los notebooks (recomendado)
1. Crear un entorno virtual e instalar dependencias mínimas (ejemplo):

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt  # si existe
# o instalar paquetes comunes
pip install pandas numpy scikit-learn matplotlib seaborn nltk spacy tensorflow torch transformers
```

2. Abrir los notebooks en Jupyter / JupyterLab / Kaggle Notebooks.
3. Ejecutar las celdas en orden. Algunos notebooks esperan que `data/train_with_features.csv` y `data/test_with_features.csv` existan; si no existen, ejecutar `armado_features.ipynb` primero.

Formato de envío (submit)
- El archivo de envío debe tener dos columnas: `id` y `target` (0 o 1). Ejemplo:

```csv
id,target
12345,1
12346,0
```

Métrica de evaluación
- La competencia utiliza F1 (macro o micro según la competencia — revisar la página de Kaggle).
