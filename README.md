# 🔬 Topic Modeling y Análisis de Redes Bipartitas

Este repositorio contiene un proyecto de ejemplo que combina el **Modelado de Temas (Topic Modeling)** usando LDA (`gensim`) para extraer temas de un corpus de texto, y un **Análisis de Redes Bipartitas** usando `networkx` para ilustrar las conexiones entre usuarios y productos.

1. Data Preparation (20%)Cargar el dataset: Carga el conjunto de datos de reseñas de Amazon (o similar) que contenga identificadores de usuario (User ID), identificadores de producto (Product ID) y la calificación (Rating).Filtrado de Datos: Para centrarse en interacciones fuertes y gestionar el tamaño de la red, se debe:Filtrar por Rating: Conservar solo las reseñas con la calificación más alta (ej. $\text{Rating} = 5.0$).Filtrar por Grado (Opcional): Considerar la eliminación de usuarios y/o productos con un número mínimo de conexiones para reducir el ruido.

<img width="640" height="371" alt="image" src="https://github.com/user-attachments/assets/7a16a5f7-7e4f-4d40-9632-811a80f6be00" />

2. Bipartite Network and Projection (30%)Construcción del Grafo Bipartito ($B$):Crea un grafo bipartito donde un conjunto de nodos representa a los Usuarios ($U$) y el otro a los Productos ($V$).Las aristas conectan a un usuario con un producto si el usuario ha calificado positivamente ese producto.Proyección a Red de Productos ($G$):Realiza una proyección bipartita ponderada en el conjunto de nodos de Productos ($V$).La proyección resulta en un grafo unipartito de productos ($G$) donde las aristas entre productos $v_i$ y $v_j$ tienen un peso igual al número de usuarios en común que calificaron positivamente a ambos productos.$$\text{Weight}(v_i, v_j) = |\{u \in U \mid (u, v_i) \in E \text{ y } (u, v_j) \in E\}|$$La matriz de adyacencia de $G$ es simétrica, lo que refleja una fuerza de recomendación mutua.
   
3. Recommendation System (30%)Una vez construida la red de productos $G$, se implementa el motor de recomendación de vecinos:Selección de Producto: Elige un nodo (producto) de origen, por ejemplo, B00ELRTZ5Y.Identificación de Vecinos: Encuentra sus $n$ vecinos (ej. $n=4$) con los pesos de arista más altos. Estos son los productos más recomendados, ya que tienen la mayor cantidad de usuarios en común con el producto de origen.Resultado: Devolver la lista de productos recomendados (IDs y sus pesos).Visualización de Red Estelar: Generar una visualización de red simplificada donde el producto seleccionado es el nodo central y sus $n$ vecinos son los nodos adyacentes, conectados por aristas (ej. de color rojo).
   
4. Visualization and Analysis (20%)El análisis y la visualización se realizan principalmente a través de un Jupyter Notebook (ej. Topic_Modeling_Notebook.ipynb), utilizando networkx y matplotlib (ipywidgets para interactividad).Gráfico de Red Estelar:
   
1. Genera la visualización de la red estelar del paso
   
3. Elementos Interactivos: Incluye dos drop-downs (desplegables) para la exploración dinámica:
   
- Un desplegable para seleccionar el Producto (nodo central).
  
- Un desplegable para elegir el número de vecinos ($n$) a mostrar/recomendar.
  
3. Análisis Opcional: Recortar el grafo proyectado $G$ (ej. filtrar aristas con pesos entre 20 y 100) para analizar la estructura de los productos con baja o alta co-ocurrencia.

