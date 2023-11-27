## Sobre los Servicios Médicos Públicos y Privados

Dentro del estudio de los datos, también se busca conocer como es que funciona la distribución de centros médicos según su clasificación en público o privado.
Para conocer de forma sintética y clara solo la cantidad de servicios públicos y privados por comuna , se realiza una pivot table.

```python
cantidad_publicos_privados_comuna = pd.pivot_table(df_hospitales_1, 
                                 index='código_comuna', 
                                 columns='tipo_de_prestador_sistema_de_salud', 
                                 aggfunc='size', )  #Función size para conocer la cantidad 
#Agrupar cantidad de servicios público/privado en cada comuna
df_hospitales_poblacion_comuna_publico_privado = pd.merge(df_hospitales_poblacion_comuna, cantidad_publicos_privados_comuna, on="código_comuna") 
#Nueva columna para saber la diferencia en cantidad de público y privado 
df_hospitales_poblacion_comuna_publico_privado["diferencia_publico_menos_privado"] = df_hospitales_poblacion_comuna_publico_privado["Público "] - df_hospitales_poblacion_comuna_publico_privado["Privado"]
df_hospitales_poblacion_comuna_publico_privado.sort_values(by="diferencia_publico_menos_privado", ascending=True, inplace=True)
df_hospitales_poblacion_comuna_publico_privado["nombre_comuna"]
```

#### Correlaciones 
Para conocer la relación entre la variable de cantidad total de prestador por comuna y los tipos de prestadores por comuna, es que se utiliza el gráfico de scatterplot. Ello debido a que por medio de la simbolización dividida de datos en puntos y triángulos es que se permite ver si existe alguna correlación a simple vista entre ambas.

Además se utiliza un mapa de calor para la correlación entre 4 variables : la cantidad de hospitales por comuna, clasificación de público, clasificación de privado y el total poblacional.

```python
sns.heatmap(df_hospitales_poblacion_comuna_publico_privado[["hospitales_x_comuna", "Privado","Público ", "total"]].corr(), annot=True) 
```

- En cuanto a la variedad regional existe una mayor variedad de establecimientos de acceso publico que privado exceptuando por la 1era y tercera región; donde la mayor variedad de establecimientos publicos que se encuentre en la region de la Araucanía, mientras que la mayor variedad de establecimientos privados es en la region de Antofagasta.

- En la variedad comunal existe una mayor variedad de establecimientos privados en 26 regiones donde la comuna con mayor variedad es la comuna de Providencia, con mayor variedad de establecimientos privados, mientras que la comuna de Los Ángeles posee la mayor variedad de establecimientos publicos.
