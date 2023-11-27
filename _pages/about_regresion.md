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

Código asociado: 

```python 

from sklearn.model_selection import train_test_split
train, test = train_test_split(df_hospitales_poblacion_comuna, test_size=0.25, random_state=2)
y_train = np.array(train['hospitales_x_comuna'])
y_test = np.array(test['hospitales_x_comuna'])

X_train = np.array(train['total'])
X_train = X_train.reshape(X_train.shape[0], 1)

X_test = np.array(test['total'])
X_test = X_test.reshape(X_test.shape[0], 1)

#realizar modelo
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

linreg = LinearRegression()
linreg.fit(X_train, y_train)

y_pred_train = linreg.predict(X_train)
r2_lineal_train = linreg.score(X_train, y_train)
rmse_train = mean_squared_error(y_train, y_pred_train)

#predecir valores de y para el set de prueba

y_pred_test = linreg.predict(X_test)
r2_lineal_test = linreg.score(X_test, y_test)
rmse_test = mean_squared_error(y_test, y_pred_test)

```
#### Densidad como parámetro 
En paralelo al análisis anterior, se utiliza la variable de densidad de hospitales por personas de una comuna, para conocer la distribución que existe comparativamente entre regiones. Sin embargo se reconoce que no es un parámetro representativo para realizar un análisis considerando que se puede observar que hay comunas grandes como en la region de Tarapaca que aunque tengan 1000 habitantes tienen 6 centros de salud. Debido a que estos habitantes estan muy dispersos. 
