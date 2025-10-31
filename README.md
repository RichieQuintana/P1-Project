# 🔬 Topic Modeling y Análisis de Redes Bipartitas

Este repositorio contiene un proyecto de ejemplo que combina el **Modelado de Temas (Topic Modeling)** usando LDA (`gensim`) para extraer temas de un corpus de texto, y un **Análisis de Redes Bipartitas** usando `networkx` para ilustrar las conexiones entre usuarios y productos.

## 📁 Estructura del Proyecto

* `requirements.txt`: Lista de dependencias de Python.
* `main.py`: Script principal en Python para ejecutar el modelado de temas.
* `Topic_Modeling_Notebook.ipynb`: Jupyter Notebook para un análisis interactivo y la visualización del análisis de red bipartita.
* `index.html`: Una plantilla HTML simple para mostrar los resultados de un análisis.
* `data/`: Carpeta que contendrá los archivos de datos (ej. `corpus.txt`, `Dataset.csv` - este último solo como ejemplo conceptual).

## 🚀 Uso

### 1. Instalación de Dependencias

Se recomienda usar un entorno virtual.

```bash
pip install -r requirements.txt
2. Ejecutar el Modelado de Temas
El script main.py cargará un archivo de texto, realizará el preprocesamiento, ajustará un modelo LDA y mostrará los temas extraídos.

python main.py
