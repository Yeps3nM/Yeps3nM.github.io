## Existencia de Urgencias 

En la contabilización global sin separación por ninguna división geográfica, la mayoría de centros médicos (todos sin separación por tipo) no tienen servicio de urgencias, predominando el valor False con 3784 entradas. Por lo tanto, solo 741 si cuentan con urgencias de cualquier tipo.  
Luego en la búsqueda específica por región se tiene que no hay ninguna región que no tenga al menos un servicio de médico sin urgencias (de cualquier tipo).
1. Analizando los valores de todas las regiones en conjunto, la que tiene más servicios con urgencias es la Metropolitana con 177. Que a fecha de 2017 es también la con más población, 7.122.808.
1. La que tiene menos servicios de urgencia analizando todos los valores regionales en conjunto es la de Arica y Parinacota con 5. Su población a 2017 era de 226.068
1. En el porcentaje que equivale al total de centros con urgencia sobre el total de centros por cada región individual, la región con el más alto sobre las otras regiones fue Valparaíso con un 21,09%. Que tiene a 2017 una población de 1.815.902.
1. En el cálculo de porcentajes anteriores, en la región Metropolitana los centros con urgencia médica sobre su total de centros, equivale a 18,15%
1. La región con número más bajo de centros con urgencia sobre el total de centros de la región sola, comparado con las otras regiones es la región de Arica y Parinacota con 6,9%. Por lo que, al ser menos de la mitad respecto al porcentaje mayor debería analizarse una mayor implementación de servicios con urgencias.

Por provincia (dividida internamente por comuna) se observó según los gráficos que las comunas sin servicio de urgencia son : 
   1. Las Torres del Paine, en la provincia de Última Esperanza (22.686 habitantes)
   2. Timaukel y Primavera, en la provincia de Tierra del Fuego (8364 habitantes)
   3. San Gregorio, Río Verde y Laguna Blanca , en la provincia de Magallanes (133.282 habitantes)
   4. Río Ibañez, provincia de General Carrera (7531 habitantes)
   5. O´higgins y Tortel, en la provincia de Capitán Prat (4638 habitantes)
   6. Lago Verde, en la provincia de Coyhaique (58.670 habitantes)
   7. Lumaco, Ercilla, Los Sauces y Renaico, en la provincia de Malleco (205.124 habitantes)
   8. Palmilla y Pumanque, en la provincia de Colchagua (22.556 habitantes)
   9. Quinta de Tilcoco, provincia de Cachapoal (646.133 habitantes)
   10. Panquehue, provincia de San Felipe de Aconcagua (154.718 habitantes)
   11. La Cruz, provincia de Quillota (203.277 habitantes)
   12. San Esteban y Rinconada , provincia de Los Andes (110.602 habitantes)
   13. Ollague , provincia de El Loa (177.048 habitantes)
   14. General lagos, provincia de Parinacota (3449 habitantes)
   15. Camarones, provincia de Arica (22.619 habitantes)
   16. Guaitecas, provincia de Aysén (32.319 habitantes)

Hay 25 comunas que no tienen centros médicos con servicio de urgencia de cualquier tipo. Considerando que en el dataframe, no se consideraba la comuna de la Antártica, es que se contabiliza y analiza por separado. En esta tampoco habían urgencias por lo que en total son 26. 

Finalmente en la tabla resumen se observa lo siguiente : en la columna de "false" se contabiliza aquellos centros que no tienen ningún tipo de urgencia y la de "true" los que sí. Sin embargo, se filtró para dejar solo los que tenían el valor en la variable true como 0. Para así sumar de forma más fácil.

| Tiene Servicio de Urgencia | Nombre Comuna        | false | true |
|----------------------------|----------------------|-------|------|
| 1                          | CAMARONES            | 1     | 0    |
| 6                          | ERCILLA              | 6     | 0    |
| 1                          | GENERAL LAGOS        | 1     | 0    |
| 1                          | GUAITECAS            | 1     | 0    |
| 1                          | LA CRUZ              | 1     | 0    |
| 3                          | LAGO VERDE           | 3     | 0    |
| 1                          | LAGUNA BLANCA        | 1     | 0    |
| 5                          | LOS SAUCES           | 5     | 0    |
| 7                          | LUMACO               | 7     | 0    |
| 1                          | O’HIGGINS            | 1     | 0    |
| 1                          | OLLAGÜE              | 1     | 0    |
| 4                          | PALMILLA             | 4     | 0    |
| 1                          | PANQUEHUE            | 1     | 0    |
| 1                          | PRIMAVERA            | 1     | 0    |
| 3                          | PUMANQUE             | 3     | 0    |
| 2                          | QUINTA DE TILCOCO    | 2     | 0    |
| 2                          | RENAICO              | 2     | 0    |
| 1                          | RINCONADA            | 1     | 0    |
| 5                          | RÍO IBÁÑEZ           | 5     | 0    |
| 1                          | RÍO VERDE            | 1     | 0    |
| 5                          | SAN ESTEBAN          | 5     | 0    |
| 1                          | SAN GREGORIO         | 1     | 0    |
| 1                          | TIMAUKEL             | 1     | 0    |
| 1                          | TORRES DEL PAINE      | 1     | 0    |
| 1                          | TORTEL               | 1     | 0    |

