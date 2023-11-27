## Correlación de variables 
Para comprender si existía una relación numérica importante entre la densidad poblacional y la cantidad de establecimientos hospitalarios por comuna es que se realizó un merge de ambos dataframes (Censo2017 + Minsal), para operar sobre este. Para ello, se utilizó un mapa de calor que graficara la correlación. 

Se ve una relacion importante entre estas dos variables puesto que es del 0.78. Esto permite elaborar de forma general que la cantidad de centros tendería a aumentar con el total de habitantes. Por lo que, debería de analizarse la existencia de más centros en pro de cubrir una mayor demanda de salud por parte de más ciudadanos. También podría realizarse un aumento en la capacidad de los establecimientos de las localidades. Es relevante destacar que si bien esta operación permite dar luces de cómo funciona esta relación y cuán alta es , no significa que haya una causalidad necesaria entre ambas.

Código asociado : 
```python
df_hospitales_poblacion_comuna = pd.merge(on="código_comuna", left=df_hospitales_1,  right=df_poblacion_por_comuna[["código_comuna", "total"]], how="right")
conteo = df_hospitales_poblacion_comuna['código_comuna'].value_counts()
df_hospitales_poblacion_comuna['hospitales_x_comuna'] = df_hospitales_poblacion_comuna['código_comuna'].map(conteo)
df_hospitales_poblacion_comuna.drop_duplicates(subset="código_comuna", inplace=True)

correlation_matrix = df_hospitales_poblacion_comuna[["total", "hospitales_x_comuna"]].corr().round(5)
sns.heatmap(correlation_matrix, annot=True,  fmt=".5f", cmap="PuRd")
```