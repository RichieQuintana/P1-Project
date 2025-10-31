# 🛒 Recommender System using Amazon Reviews

Este proyecto implementa un **sistema de recomendación basado en redes bipartitas** utilizando reseñas de productos de Amazon.  
El enfoque combina análisis de grafos y filtrado colaborativo para encontrar relaciones entre productos a partir de usuarios que han calificado los mismos artículos.


## 📋 Objetivo

Construir un sistema capaz de **recomendar productos similares** basándose en la coocurrencia de usuarios que han calificado múltiples artículos.  
El proyecto utiliza un enfoque de **proyección de red bipartita (usuarios-productos)** para generar una red unipartita de productos relacionados.


## ⚙️ Pasos del Proyecto

### 🧹 1. Data Preparation (20%)

- Se carga el dataset desde [Kaggle](https://www.kaggle.com/code/saurav9786/recommender-system-using-amazon-reviews), que contiene:
  - `userId` → Identificador del usuario  
  - `productId` → Identificador del producto  
  - `rating` → Calificación otorgada
- Se filtran los datos para mejorar el rendimiento y concentrarse en recomendaciones fuertes:
  - Mantener solo reseñas de **5 estrellas**, o  
  - Aplicar un **filtro por grado** (mínimo número de conexiones por usuario o producto).
- Este paso reduce el tamaño de la red, haciéndola más manejable para el análisis.

### 🔗 2. Bipartite Network and Projection (30%)

- Se construye una **red bipartita** `G(U, V, E)` donde:
  - `U` = conjunto de usuarios  
  - `V` = conjunto de productos  
  - `E` = relaciones usuario–producto (rating existente)
- Luego, se realiza la **proyección a red unipartita de productos**:
  1. Se obtiene la **matriz biadyacente** `B` (usuarios × productos).  
  2. Se proyecta en una matriz de adyacencia producto-producto:  
     \[
     A = B^T \times B
     \]
     donde el peso \( A_{ij} \) representa la cantidad de usuarios que calificaron ambos productos \( v_i \) y \( v_j \).
  3. La matriz resultante es **simétrica**, reflejando la fuerza mutua de recomendación entre productos.


### 🎯 3. Recommendation System (30%)

- A partir de la red de productos:
  - Se selecciona un producto (por ejemplo: `BOOELRTZ5Y`).
  - Se identifican sus **n vecinos más cercanos** (p. ej., `n=4`) basados en el **peso del enlace** (usuarios en común).
  - Se retorna:
    - IDs de los productos recomendados.
    - Pesos de conexión (grado de similitud).
  - Se visualiza como una **red tipo estrella**, donde el producto central está conectado a sus recomendaciones con **aristas rojas**.


### 📊 4. Visualization and Analysis (20%)

- Se utilizan librerías de Python para graficar y analizar la red:
  - `networkx` → operaciones con grafos  
  - `matplotlib` o `plotly` → visualización
- Visualizaciones implementadas:
  - Red estrella del producto seleccionado y sus vecinos recomendados.
  - Exploración del grafo completo, filtrando aristas por peso (por ejemplo, entre 20 y 100).
- Se incluyen **controles interactivos** (dropdowns) en el notebook:
  - Seleccionar producto.
  - Elegir número de vecinos `n`.


## 🧰 Tecnologías Utilizadas

- **Python 3.10+**
- **Librerías:**
  - `pandas`
  - `numpy`
  - `networkx`
  - `matplotlib`
  - `plotly`
  - `ipywidgets` (para interactividad)

## ▶️ Ejecución

1. Clona o descarga este repositorio:
   git clone https://github.com/tu-usuario/recommender-system-using-amazon-reviews.git
   cd recommender-system-using-amazon-reviews
Instala las dependencias necesarias:


Copy code
pip install -r requirements.txt
Abre el notebook:


jupyter notebook recommender-system-using-amazon-reviews.ipynb
Ejecuta las celdas paso a paso, siguiendo las secciones del README.

📈 Resultados Esperados
Red bipartita simplificada entre usuarios y productos.

Proyección unipartita con pesos que representan similitud entre productos.

Sistema de recomendación visual que muestra los productos más relacionados.

Gráficos interactivos y filtros para explorar la estructura de la red.
