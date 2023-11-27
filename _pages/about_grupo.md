## Modelo de Machine Learning 2: Clustering 

Para realizar esta parte del estudio se realizó una limpieza focalizada de los datos, para obtener un análisis más claro. 

```python 
df_hospitales_P4 = df_hospitales.dropna(subset=['latitud', 'longitud', 'nivel_de_complejidad'])
#se pasa el dataframe de hospitales a un geodaframe para poder hacer uso de los métodos que se incluyen en geopandas
gdf_hospitales = gpd.GeoDataFrame(
    df_hospitales_P4, geometry=gpd.points_from_xy(df_hospitales_P4.longitud, df_hospitales_P4.latitud), crs="EPSG:5360"
)
#Se renombran algunas columnas para una lectura más simplificada y además se establece que el sistema de coordenadas de los valores en la columna "geometry" será crs 5360
comunas = gpd.read_file('./maps/Comunas.zip') # se lee el archivo
comunas.rename(columns={'codregion': 'código_región', 'Region': 'nombre_región', 'Comuna': 'comuna'}, inplace=True)
comunas['geometry'] = comunas['geometry'].to_crs(5360) #Sistema de representación de coordenas de seleccionado
```
#### Modelo de Clustering : "DBSCAN"

```python
#Se seleccionan : los valores a utilizar (latitud y longitud), el epsilon (representando el grado de distancia ) y la cantidad mínima de clusters que pueden existir.

from sklearn.cluster import DBSCAN

hospitals_data = gdf_hospitales[['latitud', 'longitud']].values

eps = 0.1 #valor del epsilon
min_samples = 3 #valor mínimo de clusters
dbscan = DBSCAN(eps=eps, min_samples=min_samples)
gdf_hospitales['Cluster'] = dbscan.fit_predict(hospitals_data) #Entrenamiento del modelo


# Gráfico del modelo 

for i in range(1, 17): 
    gdf_selected_region = comunas[comunas['código_región'] == i] 
    gdf_selected_region_hospitals = gdf_hospitales[gdf_hospitales['código_región'] == i]
    
    overlay = gdf_selected_region.overlay(gdf_selected_region_hospitals, how="union", keep_geom_type=False)

    overlay['Cluster'] = overlay['Cluster'].fillna(-2)

    fig, ax = plt.subplots(figsize=[20, 20])

    # Establecer el color de fondo del eje
    ax.set_facecolor("white")

    ax.set_title(gdf_selected_region["nombre_región"].unique()[0])

    # Establecer el color de fondo de la superposición
    overlay.plot(column="Cluster", ax=ax, edgecolor="black", linewidth=0.55, facecolor="none", legend=False)

    plt.show()
```

Para obtener un resumen de cómo estaban estructurados los clusters respecto a los centros de distintas complejidaddes que contenían se utilizó este código, cambiando el número de cuántos establecimientos tenía y luego con un len para el total. 

```python
clusters_sin_dos = set()
for i in gdf_hospitales['Cluster'].unique():
    cluster = gdf_hospitales[gdf_hospitales['Cluster'] == i]#Recorre cada cluster e imprime la información de cada uno 
    print(f"El cluster {i} tiene centros de salud de complejidades {cluster['nivel_de_complejidad'].unique()}")
    print()
    if len(cluster['nivel_de_complejidad'].unique()) < 2:#Si tiene solo un nivel de complejida lo agrega al set que contiene este tipo de clusters
        clusters_sin_dos.add(i)
```
- Existen 105 clusters que no tienen todos los niveles de complejidad
- Hay 84 clusters que tienen establecimientos con un solo nivel de complejidad, siendo todos estos de baja complejidad. 

#### Justificación del modelo 

- Se escoge el modelo de DBSCAN, o llamado agrupación/clustering por densidad, el cuál es un algoritmo de aprendizaje no supervisado de Machine Learning. Pues se necesita conocer qué centros de salud forman una red por ubicación geográfica. Para saber si es posible el traslado entre centros de salud y ver si todas estas redes contienen los 3 tipos de complejidad. Con el fin de averiguar si las personas podrían tener problemas en buscar atención adecuada.

- Para hacer el modelo se hace uso de las variables de : latitud y longitud del dataframe de los hospitales(gdf_hospitales).Con estas variables se calcula la distancia cartesiana entre centros de salud.
- Se seleciona un ε de 0.1, ya que este radio nos entrega una cobertura óptima de redes que contienen centros de todas las complejidades, mientras que al mismo tiempo separa redes más pequeñas que son las que nos interesa analizar con mayor profundidad.
- Destacar en este caso no se considera como necesario normalizar los datos puesto que son coordenadas y no valores valores numericos que representen una cantidad.
- Al ser un modelo de aprendizaje no supervizado, no hay validaciones a realizar. Debido a que es el modelo el que encuentra la solución y no hay etiquetas para saber si el modelo está correcto.


