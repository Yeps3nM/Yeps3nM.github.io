## Modelo Machine Learning : Regresión Lineal Simple

Considerando la correlación importante que se mostró en el mapa de calor entre la cantidad total de habitantes y la cantidad de establecimeintos de salud es que se establece un modelamiento con esta relación bivariable.


Las métricas de evaluación del modelo mostraron lo siguiente:

Métricas de Entrenamiento
-  r^2 : 0.639641285766418
-  RMSE 91.7316069668962
-  Coeficientes: (0.0001607904136724008, 4.481244062907976)

Métricas de Prueba
- r^2 : 0.5177551943968883
- RMSE 88.83409328126801

Por lo tanto, en el caso de las métricas en el entrenamiento se puede decir que el r^2 no es el ideal pero no está bajo de 0.5 por lo que no es realmente un mal ajuste. En la métrica de prueba, este valor valor disminuye. Mostrando que la relación lineal entre ambos no está fuerte, pero aún así es significativa y puede ayudar como predicción.