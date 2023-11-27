## Distribución de Farmacias

En este apartado se hace un rastreo de la existencia de farmacias a lo largo del territorio Chileno en el presente año. Concluyéndose que en el filtrado del dataframe por provincia existen solo 2 que no tienen farmacias : Parinacota y La Antártica. 

|   | código_comuna | cantidad_farmacias_comuna | orden | nombre_región | código_región | nombre_provincia | código_provincia | nombre_comuna | edad | hombres | mujeres | total | cantidad_farmacias_prov | cantidad_farmacias_reg |
|---|---------------|---------------------------|-------|---------------|---------------|------------------|------------------|---------------|------|---------|---------|-------|-------------------------|------------------------|
| 2 | 15201.0       | 0.0                       | 66    | ARICA Y PARINACOTA | 15.0  | PARINACOTA  | 152.0  | PUTRE          | Total Comunal | 2054 | 711     | 2765    | 0.0   | 67                      | 0                      |
| 3 | 15202.0       | 0.0                       | 88    | ARICA Y PARINACOTA | 15.0  | PARINACOTA  | 152.0  | GENERAL LAGOS  | Total Comunal | 412  | 272     | 684     | 0.0   | 67                      | 0                      |
| 339 | 12201.0     | 0.0                       | 7480  | MAGALLANES Y DE LA ANTÁRTICA CHILENA | 12.0 | ANTÁRTICA CHILENA | 122.0 | CABO DE HORNOS  | Total Comunal | 1195 | 868     | 2063    | 0.0   | 41                      | 0                      |
| 340 | 12202.0     | 0.0                       | 7502  | MAGALLANES Y DE LA ANTÁRTICA CHILENA | 12.0 | ANTÁRTICA CHILENA | 122.0 | ANTÁRTICA       | Total Comunal | 126  | 12      | 138     | 0.0   | 41                      | 0                      |

---

Por otro lado, aquellas comunas sin farmacias suman 43. Generando una relación con la categoría de urgencias, hay repetición de algunas de estas, en aquellas que tenían falta de cualquier tipo de urgencia. Siendo las siguientes : 

1. Primavera,
2. Ollague
3. Camarones
4. Gral lagos
5. O´higgins
6. Río Ibañez
7. Tortel
8. Lago verde
9. Palmilla
10. Pumanque
11. Panquehue
12. Torres del paine
13. Laguna blanca
14. San gregorio
15. Río verde. 

Por lo que, existiría una carencía en ambos ámbitos dentro de estas localidades. Debíendo considerarse un plan de implementación de estos servicios según necesidades específicas de la población. El riesgo de la población que no tiene urgencias y farmacias en su alrededor es importante, respecto a las garantías que el Estado tendría que proveer.

#### Correlaciones 
Para conocer la relación entre la variable de cantidad total de personas por comuna y las farmacias por comuna se utiliza la función .corr donde se obtiene numéricamente el valor de correlación entre ambas variables. 

Es un valor bastante alto de 0.849 aproximadamente. Indicando que existe una relación importante entre mayor cantidad de farmacias a mayor cantidad de población en una comuna y lo mismo en caso de un menor valor. Esto en la generalidad de los casos

```python 
df_farmacias_cantidad[["cantidad_farmacias_comuna", "total"]].corr(numeric_only=True)
```

|                        | cantidad_farmacias_comuna | total    |
|------------------------|---------------------------|----------|
| **cantidad_farmacias_comuna** | 1.000000                  | 0.849409 |
| **total**                   | 0.849409                  | 1.000000 |

